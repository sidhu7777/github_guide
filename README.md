# GitHub Guide: Basic Commands and Scenarios

## **Basic Git Commands**

1. **Initialize a Git repository**
   ```bash
   git init
   ```
2. **Clone a repository**
   ```bash
   git clone <repository-url>
   ```
3. **Check the status of your repository**
   ```bash
   git status
   ```
4. **Stage files for commit**
   ```bash
   git add <file>
   ```
5. **Commit staged files**
   ```bash
   git commit -m "Commit message"
   ```
6. **Push changes to the remote repository**
   ```bash
   git push origin <branch-name>
   ```
7. **Pull changes from the remote repository**
   ```bash
   git pull
   ```
8. **Create a new branch**
   ```bash
   git branch <branch-name>
   ```
9. **Switch to a branch**
   ```bash
   git checkout <branch-name>
   ```
10. **Merge a branch**
    ```bash
    git merge <branch-name>
    ```
11. **View commit history**
    ```bash
    git log
    ```
12. **Delete a branch**
    ```bash
    git branch -d <branch-name>
    ```

---



### **Basic Operations**

1. **Undo the Last Commit but Keep Changes**
   - Use this command if you mistakenly committed something but want to edit the commit or add more changes.
   ```bash
   git reset --soft HEAD~1
   ```
   - **Explanation:** This resets the last commit while keeping changes staged (soft reset). You can make adjustments and re-commit.

2. **Discard Changes in a File**
   - Useful when you want to revert a file to the last committed version.
   ```bash
   git checkout -- <file>
   ```
   - **Explanation:** This discards local changes in the file and resets it to its last committed state.

3. **Stage All Changes**
   - Quickly stage all modified files in the repository.
   ```bash
   git add .
   ```
   - **Explanation:** Adds all changes (new, modified, and deleted files) to the staging area.

4. **Delete a File and Stage the Deletion**
   - Deletes a file and stages the change in one step.
   ```bash
   git rm <file>
   ```
   - **Explanation:** Ensures Git knows the file was removed and includes it in the next commit.

5. **Check the Current Branch**
   - Shows the branch you’re currently working on.
   ```bash
   git branch
   ```
   - **Explanation:** The current branch will be highlighted with an asterisk (*).

### **Branching**

6. **Rename a Branch**
   - Changes the branch name without affecting history.
   ```bash
   git branch -m <new-branch-name>
   ```
   - **Explanation:** Renames the current branch without creating a new branch.

7. **Delete a Remote Branch**
   - Use this when a branch is no longer needed remotely.
   ```bash
   git push origin --delete <branch-name>
   ```
   - **Explanation:** Removes the branch from the remote repository.

8. **Create and Switch to a New Branch**
   - Create a new branch and start working on it immediately.
   ```bash
   git checkout -b <branch-name>
   ```
   - **Explanation:** Combines branch creation and checkout into one step.

9. **List All Branches (Local and Remote)**
   ```bash
   git branch -a
   ```
   - **Explanation:** Displays all branches, including remote-tracking branches.

10. **Set Up Tracking for a New Remote Branch**
    - Links a local branch to its remote counterpart for easy pushing and pulling.
    ```bash
    git branch --set-upstream-to=origin/<branch-name> <branch-name>
    ```
    - **Explanation:** Enables commands like `git pull` to work without needing explicit arguments.

### **Merging and Rebase**

11. **Resolve Merge Conflicts**
    - After a conflict during a merge:
      ```bash
      git add <file>
      git commit
      ```
    - **Explanation:** Edit the conflicting file(s), stage the resolved changes, and commit them to complete the merge.

12. **Abort a Merge**
    - Cancel an ongoing merge and return to the pre-merge state.
    ```bash
    git merge --abort
    ```
    - **Explanation:** Useful if you want to discard the merge and start over.

13. **Rebase a Branch**
    - Incorporate the latest changes from another branch into your current branch.
    ```bash
    git rebase <branch-name>
    ```
    - **Explanation:** Keeps a clean linear history by replaying your commits on top of the other branch.

14. **Continue a Rebase After Conflict Resolution**
    ```bash
    git rebase --continue
    ```
    - **Explanation:** After resolving conflicts during a rebase, this command resumes the process.

15. **Squash Commits During a Rebase**
    - Combine multiple commits into one.
    ```bash
    git rebase -i HEAD~<number-of-commits>
    ```
    - **Explanation:** Use an interactive rebase to mark commits as "squash."

### **Remote Repositories**

16. **Add a Remote Repository**
    ```bash
    git remote add origin <repository-url>
    ```
    - **Explanation:** Links your local repository to a remote repository.

17. **View Remote Repositories**
    ```bash
    git remote -v
    ```
    - **Explanation:** Displays the URLs of all remote repositories.

18. **Change the URL of a Remote Repository**
    ```bash
    git remote set-url origin <new-repository-url>
    ```
    - **Explanation:** Updates the remote repository URL without removing it.

19. **Fetch Changes from a Remote Repository**
    ```bash
    git fetch origin
    ```
    - **Explanation:** Downloads changes from the remote repository without integrating them.

20. **Delete a Remote Repository Reference**
    ```bash
    git remote rm origin
    ```
    - **Explanation:** Removes the connection to a remote repository.

### **Stashing**

21. **Stash Changes**
    ```bash
    git stash
    ```
    - **Explanation:** Temporarily saves changes to your working directory without committing them.

22. **List Stashes**
    ```bash
    git stash list
    ```
    - **Explanation:** Shows all stashed changes with IDs.

23. **Apply the Latest Stash**
    ```bash
    git stash apply
    ```
    - **Explanation:** Reapplies the most recent stash without deleting it.

24. **Drop a Stash**
    ```bash
    git stash drop
    ```
    - **Explanation:** Deletes a specific stash from the list.

25. **Apply and Drop a Stash Simultaneously**
    ```bash
    git stash pop
    ```
    - **Explanation:** Reapplies the stash and removes it from the stash list.

### **Logs and Debugging**

26. **View a Specific Commit**
    ```bash
    git show <commit-hash>
    ```
    - **Explanation:** Displays details and changes made in a specific commit.

27. **View Changes Made in the Last Commit**
    ```bash
    git diff HEAD~1 HEAD
    ```
    - **Explanation:** Compares the latest commit with the one before it.

28. **Find Who Changed a Specific Line in a File**
    ```bash
    git blame <file>
    ```
    - **Explanation:** Shows line-by-line authorship.

29. **Search Commit History for a Keyword**
    ```bash
    git log --grep="keyword"
    ```
    - **Explanation:** Filters the log for commits containing the keyword in their message.

30. **Reset a File to a Specific Commit**
    ```bash
    git checkout <commit-hash> -- <file>
    ```
    - **Explanation:** Restores the file to its state at the specified commit.



31. **Cherry-Pick a Commit from Another Branch**
    - **Scenario:** You need to copy a specific commit from one branch to another without merging the entire branch.
    ```bash
    git cherry-pick <commit-hash>
    ```
    - **Explanation:** Applies the changes from the specific commit to your current branch.

32. **Amend the Last Commit**
    - **Scenario:** You forgot to include changes in the last commit or want to edit its message.
    ```bash
    git commit --amend
    ```
    - **Explanation:** Opens an editor to modify the commit message or add staged changes.

33. **Recover a Deleted Branch**
    ```bash
    git reflog
    git checkout -b <branch-name> <commit-hash>
    ```
    - **Explanation:** Restores a branch using its commit history.

34. **Squash All Commits into One**
    ```bash
    git reset --soft <initial-commit-hash>
    git commit -m "New initial commit"
    ```
    - **Explanation:** Combines all changes into a single commit.

35. **Bisect to Find a Bug**
    ```bash
    git bisect start
    git bisect bad
    git bisect good <commit-hash>
    ```
    - **Explanation:** Uses binary search to find the commit introducing a bug.

36. **Create a Patch from a Commit**
    ```bash
    git format-patch -1 <commit-hash>
    ```
    - **Explanation:** Generates a `.patch` file for sharing or applying changes.

37. **Apply a Patch**
    ```bash
    git apply <patch-file>
    ```
    - **Explanation:** Applies a patch file to your working directory.

38. **Revert a Commit**
    ```bash
    git revert <commit-hash>
    ```
    - **Explanation:** Creates a new commit that undoes the changes of the specified commit.

39. **Stage Partial Changes in a File**
    ```bash
    git add -p <file>
    ```
    - **Explanation:** Lets you select specific changes in a file to stage.

40. **Track an Untracked File**
    ```bash
    git add <file>
    ```
    - **Explanation:** Adds an untracked file to the staging area.

41. **Remove Ignored Files**
    ```bash
    git clean -f -X
    ```
    - **Explanation:** Removes files ignored by `.gitignore`.

42. **Rename a Remote**
    ```bash
    git remote rename <old-name> <new-name>
    ```
    - **Explanation:** Updates the name of a remote.

43. **Sync a Fork with Upstream**
    ```bash
    git fetch upstream
    git merge upstream/main
    ```
    - **Explanation:** Updates your fork with the original repository.

44. **Force Push to Overwrite Remote History**
    ```bash
    git push origin <branch-name> --force
    ```
    - **Explanation:** Overwrites the remote branch with local commits.

45. **Create a Lightweight Tag**
    ```bash
    git tag <tag-name>
    ```
    - **Explanation:** Creates a tag without additional metadata.

46. **Create an Annotated Tag**
    ```bash
    git tag -a <tag-name> -m "Tag message"
    ```
    - **Explanation:** Includes metadata with the tag.

47. **Push Tags to Remote**
    ```bash
    git push origin --tags
    ```
    - **Explanation:** Pushes all tags to the remote repository.

48. **List All Tags**
    ```bash
    git tag
    ```
    - **Explanation:** Displays all tags in the repository.

49. **Remove Local Commits from a Branch**
    ```bash
    git reset --hard <commit-hash>
    ```
    - **Explanation:** Resets the branch to a specific commit, discarding changes.

50. **List Files Ignored by Git**
    ```bash
    git status --ignored
    ```
    - **Explanation:** Shows files ignored by `.gitignore`.

51. **Rewriting Commit History for Multiple Commits**
    ```bash
    git rebase -i HEAD~5
    ```
    - **Explanation:** Use interactive rebase to modify commit messages, amend each one, and continue rebase until all commits are updated.

52. **Split a Large Commit into Smaller Commits**
    ```bash
    git reset --soft HEAD~1
    git add <specific-file-or-changes>
    git commit -m "First logical commit"
    git add <other-files-or-changes>
    git commit -m "Second logical commit"
    ```
    - **Explanation:** Soft reset the commit, selectively stage changes, and create multiple smaller commits.

53. **Remove Sensitive Information from a Repository**
    ```bash
    git filter-branch --force --index-filter \
        "git rm --cached --ignore-unmatch <sensitive-file>" \
        --prune-empty --tag-name-filter cat -- --all
    git push origin --force --all
    git push origin --force --tags
    ```
    - **Explanation:** Rewrite history to remove the sensitive file and force-push the updated repository.

54. **Recover a Deleted File from a Specific Commit**
    ```bash
    git log -- <file>
    git checkout <commit-hash> -- <file>
    git add <file>
    git commit -m "Restore <file> from commit <commit-hash>"
    ```
    - **Explanation:** Find the commit where the file existed, restore it using `checkout`, and commit the restored file.

55. **Rewrite the Author of All Commits**
    ```bash
    git filter-branch --env-filter '
        if [ "$GIT_AUTHOR_NAME" = "Old Name" ];
        then
            export GIT_AUTHOR_NAME="New Name"
            export GIT_AUTHOR_EMAIL="new.email@example.com"
            export GIT_COMMITTER_NAME="New Name"
            export GIT_COMMITTER_EMAIL="new.email@example.com"
        fi' -- --all
    git push origin --force --all
    ```
    - **Explanation:** Rewrite history to replace the old author information with the new one.

56. **Resolve Diverged Branches with Rebasing**
    ```bash
    git fetch origin
    git rebase origin/main
    git push origin <branch-name> --force
    ```
    - **Explanation:** Rebase your branch onto the updated `main` branch and force-push to reconcile the divergence.

57. **Create and Apply a Custom Git Alias**
    ```bash
    git config --global alias.lg "log --oneline --graph --decorate --all"
    git lg
    ```
    - **Explanation:** Create an alias for a long command (`git log --oneline --graph --decorate --all`) and use it.

58. **Migrate a Subdirectory to a New Repository**
    ```bash
    git subtree split --prefix=<folder-path> -b <new-branch-name>
    git clone <repository-url> <new-repository>
    cd <new-repository>
    git checkout <new-branch-name>
    git push origin main
    ```
    - **Explanation:** Use `git subtree split` to create a new branch with the folder’s history, clone the repo, and push the branch as a new repository.

59. **Resolve "Detached HEAD" State**
    ```bash
    git checkout <commit-hash>
    git branch <new-branch-name>
    git checkout <new-branch-name>
    ```
    - **Explanation:** Create a branch from the commit and switch to it, returning to a "normal" state.

60. **Revert a Merge Commit**
    ```bash
    git log
    git revert -m 1 <merge-commit-hash>
    ```
    - **Explanation:** Use `-m 1` to specify the parent branch to keep, creating a new commit that undoes the merge.
