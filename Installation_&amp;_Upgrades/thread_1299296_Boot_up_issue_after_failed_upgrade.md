---
title: "Boot up issue after failed upgrade"
date: 2009-10-23
forum: Installation &amp; Upgrades
---

### Post by blittle on 2009-10-23
Hello,

I have a Dell Laptop Inspiron 1501 AMD 64 Athlon X2 system that dual boots Ubuntu 8.04 and Windoze.

Here is what happened:

Decided to upgrade to 8.10, (the plan was to proceed to subsequent upgrades so I can get to Ubuntu 9.10 when released) I stupidly had the laptop running on battery at the time the upgrade was unpackaging and installing then the laptop died. Upon boot up, I get the following after grub:

[ 0.004000] Aperture beyond 4GB. Ignoring.
[ 0.024001] ..MP-BIOS bug: 8254 timer not connected to IO-APIC
[ 0.520167] Kernel panic - not synching: VFS: Unable to mount root fs on unknown-block(0,0)

Any ideas?

---

### Post by aheckler on 2009-10-23
I would just plug it in and do a reinstall of Ubuntu.

---

### Post by blittle on 2009-10-23
Thank you. I was trying to avoid this because I still had some sensitive data that I failed to backup. I've done 5 upgrades in the past and never had this isseu and the first time I decided to not back up, this happpend.

---

### Post by blittle on 2009-10-24
some progress. I went into grub and chose one of the recovery modes and told Ubuntu to fix broken packages and it began to proceed with the broken packages and installation. This seemed to fix the startup issue which I think was just hangin at the error messages I posted earlier. Now I'm able to log in, however the system hangs on a blank desktop and never shows the gui. Just a mouse arrow.

---

### Post by blittle on 2009-10-26
bump

---

### Post by aheckler on 2009-10-26
Try booting into "safe graphics mode" or whatever it's called (maybe "failsafe X" now?)

---

### Post by chipper_farley on 2009-10-26
Another option is to boot from an Ubuntu install CD and mount the filesystem and then do a fsck.  Since the machine died in mid upgrade, you probably have some inconsistencies in your filesystem.  Once that's done, try booting from the hard disk.  I hate to say it but you might have a hard time with this one.  Good luck.

---

### Post by blittle on 2009-10-26
Thanks guys, I'll try the boot cd first. I may just download the 8.10 iso since the one I do have is  goes back to 7.0. Not sure if that makes a difference.

---

### Post by blittle on 2009-10-31
This is what worked for me, but will skip the first attempt of the last step so as not to waste anybodies' time:

First, ran apt-get upgrade as jessiebrownjr suggests.

then the second step:

1. Select recovery mode from the boot menu.
2. Select login as root from the menu in recovery mode.
3. Type this at the prompt

    # sudo apt-get remove xorg-driver-fglrx
    # sudo dpkg-reconfigure -phigh xserver-xorg

4. Exit

    # exit

5. Now select Resume normal boot from the menu.

Method can be found here [http://blog.dipinkrishna.info/2009/06/blank-screen-after-boot-process-in.html](http://blog.dipinkrishna.info/2009/06/blank-screen-after-boot-process-in.html)

Finally it worked!
It seems that I had to run apt-get upgrade due to original issue that I had an interrupted update to begin with or possibly 8.04/9,04 bug with video driver? Either way, I decided to do aclean upgrade to 9.10 since and I am happy so far!

---

