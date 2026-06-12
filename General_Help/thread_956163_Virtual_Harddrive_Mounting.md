---
title: "Virtual Harddrive Mounting"
date: 2008-10-22
forum: General Help
---

### Post by Minguo on 2008-10-22
I was trying to get Qemu working, and as a lark, I downloaded the ReactOS Qemu package and got it running.


So while following the instructions to get it working, I mounted the the virtual hard drive to my /media/ folder using this command.
```

   mount -oloop,offset=32256 -t vfat ReactOS.hd /media

```
  Now there are a bunch of system files in there from ReactOS system that I want to delete, only now Linux has made them all 'read-only' and I cannot change this or delete the files.

Any idea how to get rid of these files?

---

### Post by cariboo on 2008-10-23
Use sudo eg:

```
sudo rm name_of_file
```

You have to do this is a terminal, or you could use gksu in a graphical program. Press Alt-F2 and type:

```
gksu nautilus
```

Enter your password when asked. This will open Nautilus (Places-->Home Folder) as root, you can then delete the files.

Jim

---

