---
title: "[SOLVED] Can't delete folder from trash"
date: 2008-07-18
forum: General Help
---

### Post by knudsenjoe on 2008-07-18
I've got a folder in my trash can that won't let me delete it. I can't drag it out of the trash to change permissions, and I can't change permissions within the trash folder. It has an icon on it that is a box with an x, I know that's some kind of a permission, but again, I can't change the permissions.

All I want is to erase this empty folder from the trash can. Any help would be appreciated.

---

### Post by Potatoj316 on 2008-07-18
open a terminal and type "cd .Trash" (no quotes) now you should be in the trash directory, type "ls -a" (again no quotes) this should show you all the files and directories in the trash.  Now, be careful with this command, if used incorrectly it can do MAJOR damage to your system, type "sudo rm -r [directory to delete]" (no quotes and replace brackets with name of directory to delete) It will then ask you for your password, enter it and hit enter.  Your directory (and its contents) should be gone from trash.

I may have the directory of trash wrong.  Im not on my Ubuntu computer now to check.

---

### Post by drs305 on 2008-07-18
> **knudsenjoe said:**
> I've got a folder in my trash can that won't let me delete it. I can't drag it out of the trash to change permissions, and I can't change permissions within the trash folder. It has an icon on it that is a box with an x, I know that's some kind of a permission, but again, I can't change the permissions.

All I want is to erase this empty folder from the trash can. Any help would be appreciated.

In hardy:
```
gksu nautilus ~/.local/share/Trash
```

Delete the Files folder.

---

### Post by knudsenjoe on 2008-07-18
Thanks drs305, that did it

---

### Post by yit on 2008-09-11
Ok, I have a folder that still won't delete.

I right clicked the folder in the trash and went to permissions.  Owner can create and delete files but I selected read-write access and applied everything to enclosed files.  still won't delete.

I tried "sudo rm -rf .local/share/Trash/files/*" but the folder is still there.  

I also tried "gksu nautilus ~/.local/share/Trash" and navigated to the Trash folder located in .local/share, but the folder is not there.  In the sidebar of nautilus, I tried clicking on the trash icon but it tells me "The folder contents could not be displayed."
I went to the info folder in ~/.local/share/Trash but "folder5" is not in there.

I went ahead and did "sudo rm -r ~/.Trash/*" but of course that is not where the trash is in hardy.

I did "chown user.user -R /home/user/.local/share/Trash"

Tried sudo rm -r /home/user/.Trash/"folder5"

Another post suggested to try "sudo find . -name pan-0.132", but I got "Permission Denied"

Still won't go away. Ideas?

---

