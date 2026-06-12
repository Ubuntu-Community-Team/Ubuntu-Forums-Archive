---
title: "CDROM often refuses to eject and work"
date: 2008-09-05
forum: General Help
---

### Post by descentspb on 2008-09-05
I can't figure out what is the reason, but sometimes, my cdrom stops seeing any cd's, i press the eject button and it does not work. Typing "eject" in terminal also does not help. "sudo eject" also.

It continues until the reboot, then it starts working again. How can i check what's wrong with it? Thanks.

System is Hardy x64, fully updated.

---

### Post by bullgr on 2008-09-05
is this happen i a clean system (after booting) or after you use some applications and if so, what applications?

---

### Post by ainsworth on 2008-09-05
I had a similar issue a while ago, this bug might be of interest to you: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/223780](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/223780)
The fact that it only does it intermittently makes me think it could be something else but I think this would still be worth a try.

---

### Post by descentspb on 2008-09-05
Well, I can't really figure out when exactly does it stop working. What I know, is that after a system reboot, it's perfectly ok.

ainsworth: Thanks for the answer, but I believe that the bug is no the same as mine.

---

### Post by bullgr on 2008-09-05
> **descentspb said:**
> Well, I can't really figure out when exactly does it stop working. What I know, is that after a system reboot, it's perfectly ok.

try to find out with what program the problem appears.
For example i get this problem when i use the dvdrom in virtualbox.
when i close virtualbox and i am in ubuntu desktop, the dvdrom drive are not open until i reboot.

you must check in what programs you use usualy after you run them, appears the cdrom drive problem.

---

### Post by descentspb on 2008-09-08
Hey, thanks! That happens exactly after using VirtualBox. It ejects, but does not come back. Though "eject -t" makes it go inside again. So, you are not alone now. What do you think about filling a bugreport?

---

### Post by Mister.Vash on 2008-09-09
see if any programs are still accessing the device.  If it is in use, you can't eject.  Run the following command

lsof /media/cdrom0

replacing /media/cdrom0 with the path of your drive.  The output will list the command, process ID, user, etc of any open files.  You can test it by running a program, playing music etc, so you can see what the output looks like when it is in use

---

