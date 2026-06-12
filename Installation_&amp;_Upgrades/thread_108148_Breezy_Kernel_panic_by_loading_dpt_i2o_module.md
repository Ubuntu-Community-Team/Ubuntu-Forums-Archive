---
title: "Breezy Kernel panic by loading dpt_i2o module"
date: 2005-12-25
forum: Installation &amp; Upgrades
---

### Post by linuxone on 2005-12-25
Hi,

I'm currently installing my Web server with Ubuntu Server. During booting the Breezy Install CD a kernel panic occurs caused by the dpt_i2o module (needed from an Adaptec 2400A IDE Raid 5 controller).
I tried both CD (Ubuntu 5.10 and Ubuntu server), same crash. Neither specific boot parameters doesn't help.

Using Ubuntu 5.04 install CD runs fine, no crash.

Thomas

---

### Post by linuxone on 2005-12-25
Status:

First I did an Bios update (Asus P4C800-E Deluxe) to the latest available version (24). And tried different settings for the IDE mode (enhanced or compatible), as reported for possible solvings for the "IRQ 18 nobody cared" error message which appears many times during installation of Ubuntu 5.04. Compatible IDE mode really seems to solve this problem, it didn't appear once again since this changing.

But: Rebooting the original install CD and kernel panic occurs again.

FInal results:

Installation of Ubuntu 5.04 (Server mode) could be finished - no problems (see above: IRQ18 ).
Updating to the latest 5.04 kernel (2.6.10-686-smp) and reboot - no problems.
dist-upgrade to Ubuntu breezy and reboot - no problems.
upgrading to latest kernel 2.6.11-686-smp and reboot - no problems.

installation of latest kernel 2.6.12-10-686-smp and reboot - [color=red]**fails**[/color]. (kernel panic while loading dpt_i2o module)

Reboot to 2.6.11 and the system runs correctly again. No error message. I didn't change anything except selecting a different boot image.

Real strange. My own Desktop machine uses the same hardware except the Adaptec Raid controller but with SATA devices. I successfully use kernel 2.6.12-10-686-smp with Bios IDE setting "enhanced" without any problems.

And grub can't boot from the Adaptec raid-5 disk. Still need to explore this issue .... But first I must get all my server apps installed.

Thomas

---

### Post by Z3K3 on 2006-01-04
I had a similar issue with a Adaptec ZCR card.  The issue I found was to due with the new i2o module included in the kernel, it seems to conflict with the dpt_i2o.

The i2o module was completely re-written from scratch to replace dpt_i2o.

I was able to boot my machine on a non 686-smp kernel, and previous to 2.6.11*.  Once installing the 2.6.12, I got the same errors as you.

The fix was this:

[http://www.ubuntuforums.org/showthread.php?t=78627](http://www.ubuntuforums.org/showthread.php?t=78627)

You have to install the new kernel 2.6.12-10-686-smp
rm -rf the i2o module
do a depmod
dpkg-reconfigure the kernel.
it works then.

It will be another few weeks until I get my development server, once that arrives I'm going to keep working on this to see if I can figure out a way to use the new i2o module vs the old dpt_i2o.

For more info google.  and check out:
[http://i2o.shadowconnect.com/](http://i2o.shadowconnect.com/)
[http://www.ubuntuforums.org/showthread.php?t=81534&highlight=dpt_i2o](http://www.ubuntuforums.org/showthread.php?t=81534&highlight=dpt_i2o)  
My Post is #10.
[http://bugzilla.ubuntu.com/show_bug.cgi?id=17897](http://bugzilla.ubuntu.com/show_bug.cgi?id=17897)
[http://bugzilla.ubuntu.com/show_bug.cgi?id=16011](http://bugzilla.ubuntu.com/show_bug.cgi?id=16011)



Z3K3

---

