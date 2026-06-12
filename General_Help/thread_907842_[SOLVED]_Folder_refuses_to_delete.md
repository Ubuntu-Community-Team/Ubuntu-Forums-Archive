---
title: "[SOLVED] Folder refuses to delete"
date: 2008-09-01
forum: General Help
---

### Post by TNAFan on 2008-09-01
I have a folder that doesn't seem to want to empty from the trash.   I select empty trash and it doesn't delete, I right click and select delete from trash and it gives me an error that says folder not empty.  Though, it is empty, it doesn't even have any invisible folders in it.  Moving it into any other folder gives me an error as well. Any ideas on how to get rid of it?

---

### Post by iaculallad on 2008-09-01
> **TNAFan said:**
> I have a folder that doesn't seem to want to empty from the trash.   I select empty trash and it doesn't delete, I right click and select delete from trash and it gives me an error that says folder not empty.  Though, it is empty, it doesn't even have any invisible folders in it.  Moving it into any other folder gives me an error as well. Any ideas on how to get rid of it?

On your terminal:

```
sudo rm -rf ~/.local/share/Trash/files/*
```

Or

```
gksudo nautilus
```

And try to browse your Trash folder and delete the "undeletable" file/folder.

---

### Post by drs305 on 2008-09-01
Open nautilus with administrative powers, navigate to the Trash folder containing the folder in question and SHIFT-delete.

```
gksu nautilus
```
If it is in your normal user Trash bin, this will take you directly to a point where you will see the Trash folder, then delete it:
```
gksu nautilus ~/.local/share
```

For lots more than you'd want to know about Trash, see the link in my signature line...

---

### Post by TNAFan on 2008-09-01
Thank you both for your help!  How often does something like that happen?  How does it happen in the first place?

---

### Post by iaculallad on 2008-09-01
> **TNAFan said:**
> Thank you both for your help!  How often does something like that happen?  How does it happen in the first place?

Errors like that (Of not being able to delete files/folders in Trash folders) happens on all Operating System. Something might be wrong with Nautilus, or your file system as a whole. But most of the time, it's one of of your System of protecting itself and thus it will now allow files to be deleted (mostly on the compilation process of tarball applications).

---

