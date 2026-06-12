---
title: "[SOLVED] Can only hibernate two times"
date: 2008-04-19
forum: Hardware &amp; Laptops
---

### Post by earther on 2008-04-19
Problem:

Can hibernate twice but not a third time


System specs:

Antec NSK4480 Black Mid Tower Case (380watt PS)
Gigabyte GA-P35-DS3L Socket 775 Motherboard
Intel® Core™ 2 Duo E6750 - Socket LGA775
EVGA 8400GS Video Card (PCI-Express, 512MB)
KINGSTON DDR2 2GB PC5300 DUAL (667 MHz)
2 - 250GB WD Sata drives (recycled from old box)
Pioneer DVD_RW DVR-112D (recycled from old box)

Brand new box (almost), one week old.  Did not reinstall the OS.  Just used the drive running Gutsy 2.6.22-14-generic from the old box.

Old machine did not have this problem with Asus P4P 800 SE and nVidia GeForce MX4000.


Logs:

dmesg reports these errors coming out of the first hibernation:

> 753 [   45.015490] ata5.00: ACPI cmd ef/03:46:00:00:00:a0 failed (Emask=0x1 Stat=0x51 Err=0x04)
754 [   45.015492] ata5.00: revalidation failed (errno=-5)
755 [   45.015494] ata5: failed to recover some devices,

771 [   50.325414] ata5.00: ACPI cmd ef/03:46:00:00:00:a0 failed (Emask=0x1 Stat=0x51 Err=0x04)
772 [   50.325419] ata5.00: ACPI on devcfg failed the second time, disabling (errno=-5)
773 [   50.325421] ata5.00: revalidation failed (errno=1)
774 [   50.325424] ata5: failed to recover some devices

and these errors going into the third, failed hibernation:

> 994 [  481.568378] ACPI Exception (exoparg2-0442): AE_AML_PACKAGE_LIMIT, Index (000000006) is beyond end of object [20070126]
995 [  481.568384] ACPI Error (psparse-0551): Method parse/execution failed [\_SB_.PCI0.PEX3.JMB0.SDE0._GTM] (Node df831ed0), AE_AML_PACKAGE_LIMIT
996 [  481.568410] ata5: ACPI get timing mode failed (AE 0x300d)
997 [  481.584202] pci_device_suspend(): ata_pci_device_suspend+0x0/0x40 [libata]() returns -22
998 [  481.584227] suspend_device(): pci_device_suspend+0x0/0x60() returns -22
999 [  481.584233] Could not suspend device 0000:03:00.0: error -22

All other lines of the hibernation sequences are identical.


Troubleshooting:

At first I thought it might be Compiz but it does the same thing if Compiz is disabled.

Have tried acpi=off, noapci and apci=force and none of them makes a difference.

Have stopped and restarted gnome-power-manager  and that didn't help either.

Google found two mentions of this 'third attempt to hibernate failure' bug but neither has a solution:

[http://www.linuxquestions.org/questions/linux-newbie-8/hibernate-works-two-times-and-fails-afterwards-611303/](http://www.linuxquestions.org/questions/linux-newbie-8/hibernate-works-two-times-and-fails-afterwards-611303/)
[http://lists.tuxonice.net/lurker/message/20071208.131529.9043ec90.da.html](http://lists.tuxonice.net/lurker/message/20071208.131529.9043ec90.da.html)

Anybody have an idea what's going on?  This is driving me nuts!  PLEASE HELP!!

---

### Post by earther on 2008-04-20
No one has any ideas?

---

### Post by earther on 2008-04-28
OK.  I did a little trouble shooting found a solution.

Today I did a clean install of Gutsy on a spare drive. Tested both before and after updates. Same problem. Couldn't go into hibernation for a third time.

Next, I tried loading a newer kernel from Hardy - 2.6.24-16 - on the Gutsy clean install as per [**this thread**]("http://ubuntuforums.org/showthread.php?t=646755"). Voila!  That allowed me to hibernate correctly.

However, when I replaced my working drive and tried the kernel upgrade. The result was even worse than before. The hard drive turned off but the system wouldn't power down.  I uninstalled the Hardy kernel and took a break.

After food and downtime, I took another shot at installing the Hardy kernel on Gutsy.  THIS TIME IT WORKED (have no idea why it didn't the first time)!  I am now able to hibernate repeatedly.

IT LOOKS LIKE THIS IS A BUG BETWEEN GUTSY AND MY HARDWARE CONFIGURATION!

I am so happy to have found a fix for this.

---

### Post by earther on 2008-04-29
[**Bug report**]("https://bugs.launchpad.net/ubuntu/+bug/224037") has been filed over at Launchpad and assigned to the Ubuntu-kernel-acpi team.

Bug has been confirmed.

---

