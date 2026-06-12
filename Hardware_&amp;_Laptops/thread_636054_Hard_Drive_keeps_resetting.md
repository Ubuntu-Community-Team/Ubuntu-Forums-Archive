---
title: "Hard Drive keeps resetting"
date: 2007-12-09
forum: Hardware &amp; Laptops
---

### Post by EnglishJoel on 2007-12-09
I have set up a file server at home with Ubuntu server, but when I am accessing files (photos, videos) I experience pauses. They last about ten seconds, after which time everything resumes. This seems to be due to the hard drive resetting.
Error messages are as follows:
[INDENT]res 40/00:ff:ff:ff:ff/ff:ff:ff:ff:ff/ff Emask 0x4 (timeout)
Dec  8 15:38:03 Jserver kernel: [ 8723.690000] ata3: port is slow to respond, please be patient (Status 0xd8)
Dec  8 15:38:08 Jserver kernel: [ 8728.370000] ata3: device not ready (errno=-16), forcing hardreset
Dec  8 15:38:08 Jserver kernel: [ 8728.370000] ata3: hard resetting port
Dec  8 15:38:09 Jserver kernel: [ 8728.880000] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Dec  8 15:38:09 Jserver kernel: [ 8728.950000] ata3.00: configured for UDMA/33
Dec  8 15:38:09 Jserver kernel: [ 8728.950000] ata3: EH complete[/INDENT]
There seems to be a few variations in the first line such as (HSM Violation) and (device error).
Sometimes the result is a soft reset and sometimes it's a hard reset.
I have found some similar posts in other forums, related to cd drives but my problem persists with a cd in and out of the drive, as well as with the drive disconnected.
I have changed the cable connecting my Sata hard drive to it's PCI card.
I have read about NCQ causing problems, but the value in the queue_depth file is 1, which I understand means NCQ is disabled.

My hard drive is this:
[INDENT]ATA device, with non-removable media
        Model Number:       WDC WD5000AAKS-00YGA0
        Serial Number:      WD-WCAS80965044
        Firmware Revision:  12.01C02
        Transport:          Serial, SATA 1.0a, SATA II Extensions, SATA Rev 2.5
[/INDENT]

My kernel is  2.6.22-14-server.

If any one can steer me to a solution I would be grateful.
Thanks

---

### Post by atlfalcons866 on 2007-12-09
looks like the hard drive is starting to fail. try running a smart test to see the status of the hdd.

---

### Post by EnglishJoel on 2007-12-09
The hard drive is less than two months old, as is the sata PCI card.

SMART overall-health self-assessment test result: PASSED

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%      1156         -
# 2  Short offline       Completed without error       00%      1134         -
# 3  Short offline       Completed without error       00%      1134         -

Thanks for the quick reply.

---

### Post by atlfalcons866 on 2007-12-09
Dec 8 15:38:09 Jserver kernel: [ 8728.880000] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Dec 8 15:38:09 Jserver kernel: [ 8728.950000] ata3.00: configured for UDMA/33

sounds to me its the pci sata card causing the problem. your not getting the full speed of sata. your only get 33MB/s. try using a pata hard disk.

---

### Post by ian dobson on 2007-12-09
Hi,

I was having exactly the same problems with one of my WD5000AAKS (I have 4 in a raid 5 array). I ran a smart test which showed lots of errors. Took the drive back to my supplier and got it replaced without any problems.

Since then I've not had any more prblems.

Regards
Ian Dobson

---

### Post by EnglishJoel on 2007-12-09
Here's an excerpt from cat /var/log/messages | grep UDMA

[INDENT]Dec  8 13:13:54 Jserver kernel: [    9.230000] ata3.00: ATA-8: WDC WD5000AAKS-00YGA0, 12.01C02, max UDMA/133
Dec  8 13:13:54 Jserver kernel: [    9.270000] ata3.00: configured for UDMA/100
Dec  8 13:13:54 Jserver kernel: [   27.800000] ata3.00: configured for UDMA/100
Dec  8 13:13:54 Jserver kernel: [   28.740000] ata3.00: configured for UDMA/100
Dec  8 13:13:54 Jserver kernel: [   59.420000] ata3.00: configured for UDMA/100
Dec  8 13:13:54 Jserver kernel: [   61.430000] ata3.00: configured for UDMA/100
Dec  8 13:13:54 Jserver kernel: [   74.750000] ata3.00: configured for UDMA/100
Dec  8 13:14:05 Jserver kernel: [   85.700000] ata3.00: configured for UDMA/100
Dec  8 13:14:06 Jserver kernel: [   86.790000] ata3.00: configured for UDMA/100
Dec  8 13:34:40 Jserver kernel: [ 1320.450000] ata3.00: configured for UDMA/100
Dec  8 14:20:39 Jserver kernel: [ 4079.390000] ata3.00: configured for UDMA/100
Dec  8 14:23:12 Jserver kernel: [ 4232.380000] ata3.00: configured for UDMA/100
Dec  8 14:24:12 Jserver kernel: [ 4291.800000] ata3.00: configured for UDMA/100
Dec  8 15:08:36 Jserver kernel: [ 6956.480000] ata3.00: configured for UDMA/100
Dec  8 15:08:47 Jserver kernel: [ 6967.470000] ata3.00: configured for UDMA/100
Dec  8 15:09:18 Jserver kernel: [ 6998.070000] ata3.00: configured for UDMA/100
Dec  8 15:09:48 Jserver kernel: [ 7028.070000] ata3.00: limiting speed to UDMA/66:PIO4
Dec  8 15:09:58 Jserver kernel: [ 7038.700000] ata3.00: configured for UDMA/66
Dec  8 15:10:29 Jserver kernel: [ 7069.300000] ata3.00: configured for UDMA/66
Dec  8 15:10:40 Jserver kernel: [ 7079.970000] ata3.00: configured for UDMA/66
Dec  8 15:11:20 Jserver kernel: [ 7120.590000] ata3.00: configured for UDMA/66
Dec  8 15:11:20 Jserver kernel: [ 7120.790000] ata3.00: configured for UDMA/66
Dec  8 15:11:50 Jserver kernel: [ 7150.790000] ata3.00: limiting speed to UDMA/33:PIO4
[/INDENT]

I definately think I have some kind of I/O problem.

---

### Post by ian dobson on 2007-12-10
Hi,

What controller is your PCI SATA controller using?
Are you sure you don't have any interrupt conflicts?
Could you try running a long smart test.
What happens is you boot with the kernel parameter IDE_ALL_GENERIC?

Regards
Ian Dobson

---

### Post by mezhaka on 2007-12-10
> **ian dobson said:**
> Hi,

What controller is your PCI SATA controller using?
Are you sure you don't have any interrupt conflicts?
Could you try running a long smart test.
What happens is you boot with the kernel parameter IDE_ALL_GENERIC?

Regards
Ian Dobson

can you provide some description of how do i do that? shell commands or something like this?

---

### Post by ian dobson on 2007-12-11
Hi,

Text pulled from [http://www.novell.com/documentation/suse91/suselinux-adminguide/html/ch07s04.html](http://www.novell.com/documentation/suse91/suselinux-adminguide/html/ch07s04.html)

7.4.1.4. Editing Menu Entries During the Boot Procedure

From the graphical boot menu of GRUB, use the cursor keys to select the operating system to boot. If you select a Linux system, you can add boot parameters. After pressing Esc and exiting the splash screen, n press E to edit individual menu entries directly. Changes made in this way only apply to the current boot procedure and will not be adopted permanently. 

 Keyboard Layout during the Boot Procedure 
The US keyboard layout is the only one available at boot time. 
 

After enabling the editing mode, use the arrow keys to navigate to the entry to change. To make the selected item editable, press E again. Adjust the entry as desired. Leave the editing mode with Enter and go back to the menu, where the changed entry can be booted by pressing E. In the lower part of the screen, GRUB displays further options. 

Just add all-generic-ide to the kernel parameters then boot up. This change will only be for one boot, when you reboot the options are reset to the defaults defined in you /boot/grub/menu.lst, but it's a good test to see if it's a driver problem.

By the way I'm still waiting for info on what chip your PCI SATA controller is using. you can use the lspci command to list you installed hardware.

Regards
Ian Dobson

---

### Post by mezhaka on 2007-12-13
I solved my problem. see [https://bugs.launchpad.net/linux/+bug/84603]("https://bugs.launchpad.net/linux/+bug/84603")

---

