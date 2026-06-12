---
title: "Trouble with USB drive"
date: 2008-07-04
forum: Hardware
---

### Post by cdkorzen on 2008-07-04
Hello:

I have a USB drive that I'd like automounted at startup, but somehow that doesn't seem to happen.

I have 3 NTFS formatted drives, 2 internal and one external.  When I browse the mount points of the two internal drives, I see the full listing of the disks' contents.  When I go to the external drive's mount point, I see nothing until I enter: "sudo mount <mount point>" at which point, everything works fine.

It used to work automatically (where the external would also be mounted at startup), but I believe it changed when one time the power cord was loose and the drive was not powered on while the system was booting.

I would like to restore the original behavior, where the drive boots mounted and I do not need to run a terminal session each time the system boots up (I can't exactly create a script because  mount needs root permissions to run).

---

### Post by cdkorzen on 2008-07-06
I'm just going to give it a single bump, just to see if anyone can help me.  I'm kind of disappointed, it seems I've made a couple posts and there's been no help, despite Ubuntu's reputation

---

### Post by red_team316 on 2008-07-06
I believe you have to edit /etc/fstab to get it to automount. I've never had much success with this in the past, and there is the possibility of hosing your system if you don't do it right.

Have you contacted ubuntu tech support? Most of the replys on the forums come from users.

---

