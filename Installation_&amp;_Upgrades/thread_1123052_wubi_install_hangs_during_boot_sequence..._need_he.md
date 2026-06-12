---
title: "wubi install hangs during boot sequence... need help!!"
date: 2009-04-11
forum: Installation &amp; Upgrades
---

### Post by kennethmsmith on 2009-04-11
I am running Windows Vista Home Premium on HP laptop.  I downloaded and installed Wubi installer 8.10.  I used it to download and install ubuntu (looks like it installed 9.04 beta based on the desktop background that showed up during the installation check process).  Everything seemed to go fine up the point where it asked me to reboot.  I did, and I selected Ubuntu from the boot menu.  At the first Ubuntu logo screen the progress bar freezes and the only way to may it progress and move on through the boot up process is to keep tapping the 'enter' key. Each tap makes the progress bar move a little and then it freezes again.. repeat and repeat.. and then I get the following message on a black screen:

"Loading, please wait...

Could not mount the partition /dev/disk/by -uuid/505ACFBB60A0226C.  This could also happen if the file system is not clean because of an operating system crash, or interrupted boot process, an improper shutdown, or unplugging of a removable device without first unmounting or ejecting it.  To fix this, simply reboot into windows, let it fully start, log in, run 'chkdsk /r' then gracefully shutdown and reboot back into windows.  After this you should be able to reboot again and resume this installation.
(filesystem = ntfs, error code = 243)

BusyBox v1.10.2 (ubuntu 1:1.10.2 -1ubuntu6) built-in shell
(ash) Enter 'help' for a list of built in commands.

(initramfs) _"

I ran chkdsk and everything seems fine.  I rebooted a couple of times in windows to make sure I was getting a good boot and restart before trying ubuntu.  Still no luck, I get the same message.

ran dmesg command and the last line of it says:
mount.ntfs[2214]: segfault at 3d9724d8 ip 00007f9f34flcf79 sp 000000003d9724e0 error 6 in libntfs -3g.so.28[7f9f34efc000+29000]

I need help understanding why the partition will not mount, and what I can do to repair this so Ubuntu will load without affecting my windows partition and files.


UPDATE:  WHEN I INSTALLED WHILE PLUGGED IN USING WUBI and AFTER EDITING MY MENU.LST FILE AS DIRECTED IN A DIFFERENT POST>> I AM NOW FIXED. 
Thanks,
Kenneth

---

