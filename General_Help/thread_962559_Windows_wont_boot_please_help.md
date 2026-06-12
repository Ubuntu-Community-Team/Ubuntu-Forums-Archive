---
title: "Windows wont boot please help"
date: 2008-10-29
forum: General Help
---

### Post by thmtrxhsy on 2008-10-29
So, as my first introduction to Ubuntu, I installed it as a dual-boot on my desktop, and installed it on my external 500GB hard drive.

I erased Vista on my laptop, and also put Ubuntu on there.

I never use the Ubuntu partition on my desktop, so yesterday I formatted the external hard drive and put NTFS on there.

Now, when I restart my computer, GRUB attempts to load, but returns error 22 when the external is plugged in, and error 21 when its not plugged in.

How can I remove GRUB so that my computer will boot straight to Windows? :confused:

Accidently clicked Ubuntu_Mobile, sorry. Please let me know if theres a better place for me to post this.

---

### Post by thmtrxhsy on 2008-10-29
So, as my first introduction to Ubuntu, I installed it as a dual-boot on my desktop, and installed it on my external 500GB hard drive.

I erased Vista on my laptop, and also put Ubuntu on there.

I never use the Ubuntu partition on my desktop, so yesterday I formatted the external hard drive and put NTFS on there.

Now, when I restart my computer, GRUB attempts to load, but returns error 22 when the external is plugged in, and error 21 when its not plugged in.

How can I remove GRUB so that my computer will boot straight to Windows?

---

### Post by edvinpul on 2008-10-29
What I understand from your post is that you removed your Linux partition from your hard drive which also has your Windows install? You say both external hard drive and desktop hard drive so I'm not sure of your configuration

From how I understand grub, and this is an over simplification, Grub loads, and looks for a file (/boot/grub/menu.lst) on your linux partition which "points" to you OS's.  If you deleted your linux partition this file is gone. However, if you have your Windows disk, you should be able to run the recovery console and fix it via the command line. This will over-write the MBR on the disk where the windows is installed.

fixboot??
fixmbr??  I thinks these are the commands (these are from memory so they might not be correct)

---

### Post by Titan8990 on 2008-10-29
Insert a Windows disk. At the main menu hit "R" for Recovery Console.

From the Recover Console:


FIXMBR


That should do it.

---

### Post by bodhi.zazen on 2008-10-29
Threads merged. I understand it happens from time to time, but please do not start multiple threads on the same topic, it causes confusion and duplication of effort.

---

### Post by thmtrxhsy on 2008-10-29
Thanks so much for your help, it worked. I was having problems with posting lol, sorry won't happen again.

---

