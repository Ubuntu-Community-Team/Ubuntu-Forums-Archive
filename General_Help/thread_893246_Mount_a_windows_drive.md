---
title: "Mount a windows drive?"
date: 2008-08-18
forum: General Help
---

### Post by gillilandboy on 2008-08-18
I have 2 hard drives one has Windows Vista and the other one has Ubuntu I am trying to find out how to transfer files from the windows drive to Ubuntu. Any help would be great.

Thanks.

---

### Post by lordrick112 on 2008-08-18
A quick google search came up with this. Hope this helps you out.

[http://www.go2linux.org/accessing-linux-drive-ext-with-vista](http://www.go2linux.org/accessing-linux-drive-ext-with-vista)

---

### Post by mb_webguy on 2008-08-18
Install the ntfs-config package in Ubuntu.  It provides a simple GUI for mounting NTFS drives.

This tool adds an entry for the drive to the /etc/fstab file so that the drive is mounted every time you startup (in addition to mounting the drive immediately after using the tool).  If you don't want the drive to mount at startup (which isn't a good idea, since otherwise you could accidentally hose your Windows installation), type "sudo gedit /etc/fstab" and delete the entry for the NTFS drive (and ONLY that entry!!!).

You *could* temporarily mount the drive by hand in the terminal, but it's a lot easier using the GUI, even if you do have to edit fstab afterward.

---

### Post by Bahb on 2008-08-18
I'm actually having an issue similar to this. I just installed ubuntu for the first time, so im new. i want my ntfs drives to mount on startup, so i followed the instructions from gillilandboy and ran it, w/e except that when i run NTFS Config, the only option it allows me is to Enable Write Support for external device, which i have none of in the first place. nothing about mounting on startup or anything like that.

---

### Post by mb_webguy on 2008-08-19
NTFS Config automatically adds an entry to fstab, so the volume will be mounted at startup.  It's not an option you choose.

---

