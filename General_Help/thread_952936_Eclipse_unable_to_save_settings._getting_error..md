---
title: "Eclipse unable to save settings. getting error."
date: 2008-10-19
forum: General Help
---

### Post by cp3 on 2008-10-19
just installed eclipse with php plugin and im having trouble saving the font settings.  i get this error:

```
A problem was encountered saving the page Appearance.  Exception saving preferences to:/home/user/workspace/.metadata/.plugins/ord.eclipse.core.runtime/.settings/org.eclipse.ui.workbench.prefs.
```

any ideas?  when i cd to that dir its not even created. im wondering if i got my permissions set.  eclipse seems really buggy if not run by root user but its gotta be a problem on my end with permissions and such.

any help would be appreciated.  thanks in advance for response. :)

---

### Post by Sam on 2008-10-19
Try to recreate the workspace.

Close Eclipse.
Backup the old workspace:
```
mv /home/user/workspace /home/user/workspace_old
```
Run Eclipse.
Recreate the workspace.
Then recreate the projects and move the content in workspace_old/* in the new workspace.

---

