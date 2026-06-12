---
title: "Suspend; Hibernate; ACPI; Dell Inspiron 8100 laptop"
date: 2006-10-28
forum: Hardware &amp; Laptops
---

### Post by frogotronic on 2006-10-28
Hello,

	I think I've almost solved the suspend-to-RAM (suspend) and suspend-to-disk (hibernate) problems with my laptop.  I'm using a DELL Inspiron 8100 running a PIII Intel Chip.  The video card (this is important) is an nVIDIA Geforce2 Go 16 MB.

	I am using ACPI.  I am not using APM, in fact I have uninstalled it as it has been posted on the web that using both ACPI and APM can cause conflicts and one has to be careful when initiating both at the same time.
```
sudo apt-get uninstall apmd
```.
        I am using 2.6.15-27-386 kernel, 6.0.6.1 (Dapper Drake).  I did however upgrade the HIBERNATE package from the Dapper Drake (1.12) to the Edgy Eft (1.91) version.  Although, this really hasn't done much that wasn't working before in Dapper Drake.

**Here's what works:**

_Suspend-to-RAM_
Complete suspension of machine and then what appears to be a “shutdown” of power, i.e. no power lights at all.  Pressing the the power button allows the machine to come back and to it's state when suspend when initiated.  Wireless, which on my laptop is a PCMCIA wireless Microsoft MN-720 card doesn't work upon revival from the suspend-to-RAM.  To make it work, I have to choose “Disable Networking” using the NetworkMangerApplet on the Panel, and the “Enable Networking” and the wireless comes back.
It may be that when I am choosing suspend-to-RAM I am in fact inadvertently  suspending-to-DISK.  If it sounds like I am, please let me know.

_Suspend-to-DISK_
This is ALMOST working.  The machine looks as though it is going to hibernate and then at the very end, after the screen has blanked (screen powered down), the HDD has stopped working [aside: there isn't isn't heavy/intense HDD activity when suspend-to-RAM (suspend) is chosen, which leads me to believe I am executing separate scripts], the machine gets to what 'feels' like the final step and then hangs.  Rather than the power going off, the power light stays on, but the HDD access light never comes back on.  I know hibernate worked before, because I used to envoke this under WindowsXP (when I was using this O/S - which I have replaced with Ubuntu: i.e. not a dual boot).  Although I suspect WindowsXP was probably using a software driven package a la SoftwareSuspend2.  In any case, the machine is unresponsive, and the only way to bring it back is holding the power button down for about 5 seconds, and then a hard restart.  This restarts the machine and all most stuff is lost.  The desktop appears to behave as though there had been a power failure, in that some of the porogramme that were running when HIBERNATE was initiated are resumed, but some of the data is lost.

I think ACPI is trying to hibernate, but I need to tweak the script to kill the power after the sys-state, and then ensure that the hibernate script can re-find the saved sys-state on the swap.

If anyone has questions to the specific tweaks I've done, I'll be happy to do that.

[B]Any ideas on the Suspend-to-DISK final stage, hanging problem?

I am also unclear on the following:  Given my description of my suspend-to-RAM, am I using any power in this state?[/B]

Thanks
CH

---

### Post by phillywize on 2006-12-30
Well, I have a similar setup (I-8200, nvidia geforce 2) with the nvidia proprietary drivers, and [this worked for me in dapper: https://help.ubuntu.com/community/NvidiaLaptopBinaryDriverSuspend]("https://help.ubuntu.com/community/NvidiaLaptopBinaryDriverSuspend").  In Edgy, not so much.  Back to the drawing board.  But if you're still on dapper, give that link a whirl.

Bob

---

### Post by frogotronic on 2006-12-30
cool...i'll try it

---

