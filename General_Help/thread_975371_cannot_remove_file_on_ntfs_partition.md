---
title: "cannot remove file on ntfs partition"
date: 2008-11-08
forum: General Help
---

### Post by lavinog on 2008-11-08
I made a backup of my brothers ntfs partition a while back. I am removing files that don't need to be backed up, but I cant remove the windows folder because of two subfolders.
```
 sudo rm -r WINDOWS/
rm: cannot remove directory `WINDOWS/assembly/GAC_32/System.EnterpriseServices/2.0.0.0__b03f5f7f11d50a3a': Operation not supported
rm: cannot remove directory `WINDOWS/assembly/GAC_MSIL/IEExecRemote/2.0.0.0__b03f5f7f11d50a3a': Operation not supported

```
The two folders have the same name, and are empty

Is there a problem with the name of the folder?
If so should this be filed as a bug?

---

