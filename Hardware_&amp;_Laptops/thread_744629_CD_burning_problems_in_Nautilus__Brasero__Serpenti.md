---
title: "CD burning problems in Nautilus / Brasero / Serpentine (Dell D420 with media slice)"
date: 2008-04-03
forum: Hardware &amp; Laptops
---

### Post by explicitly ambiguous on 2008-04-03
In setting up a friend on ubuntu I am having difficulties with burning CD/DVDs (system specs and details below).  

**[SIZE="2"]The problem:[/SIZE]**  I did a fresh install of Ubuntu Gusty and installed Brasero (less software to learn after the upgrade in a months time ;-) 

In trying to burn an audio CD with **Brasero** the program fails with error message:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=64863&stc=1&d=1207268247[/IMG]

If I try to burn it to an image on the hard disk I also get an error:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=64873&stc=1&d=1207268509[/IMG]

When a blank CD is inserted dmesg reports:

[  115.204000] cdrom: This disc doesn't have any tracks I recognize!


This error message may be related to: 

[https://answers.launchpad.net/ubuntu/+question/11076]("https://answers.launchpad.net/ubuntu/+question/11076")
 
Although in my case, the "create CD" dialog appears the first time after a reboot and then after a few attempts at burning CDs it stops.

Next I tried to burn an audio CD using **Serpentine**.  All seemed to go well until it had almost completed, when it should have told me it had completed the burn it instead told me that "The system is too slow to write the CD at this speed. Try a lower speed." but the CD completed and ejected.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=64871&stc=1&d=1207268247[/IMG]

On re-inserting the CD it can be played OK -- but the track info is completely random?!?  It comes up with tracks that I have never heard of, one is even in Chineese characters??

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=64872&stc=1&d=1207268247[/IMG]

If I try and burn a data CD using drag and drop in **Nautilus** it acts much like Serpentine; that is, it completes fine but exits with the message "The system is too slow to write the CD at this speed. Try a lower speed.". On reloading the CD the files read fine and there is no evidence that it didn't burn as it should have.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=64870&stc=1&d=1207268247[/IMG]


Any ideas / help anyone can give would be much appreciated!   

If any more info would help diagnose then I can provide it...



**[SIZE="2"]Hardware:[/SIZE]**

Dell D420 with the CD/DVD drive on a media slice (docking station)

dmesg repots the drive as:
```

[   26.008000] ACPI: Battery Slot [BAT0] (battery present)
[   26.572000] usb-storage: device scan complete
[   26.576000] scsi 2:0:0:0: CD-ROM            HL-DT-ST DVD+-RW GWA4083N B105 PQ: 0 ANSI: 0
[   26.576000] scsi 2:0:0:0: Attached scsi generic sg1 type 5
[   26.664000] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[   26.664000] Uniform CD-ROM driver Revision: 3.20
[   26.664000] sr 2:0:0:0: Attached scsi CD-ROM sr0
[   26.676000] ACPI: AC Adapter [AC] (off-line)
[   26.804000] ACPI: ACPI Dock Station Driver 
[   26.972000] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)

```

lspci:
```

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
02:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b4)
02:01.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 09)
02:01.2 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 18)
09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5752 Gigabit Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

```

lsusb:
```

Bus 005 Device 004: ID 0b97:7761 O2 Micro, Inc. 
Bus 005 Device 006: ID 413c:9001 Dell Computer Corp. 
Bus 005 Device 003: ID 413c:a005 Dell Computer Corp. 
Bus 005 Device 005: ID 413c:8103 Dell Computer Corp. Wireless 350 Bluetooth
Bus 005 Device 007: ID 0b97:7762 O2 Micro, Inc. Oz776 SmartCard Reader
Bus 005 Device 002: ID 413c:a005 Dell Computer Corp. 
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000 

```

fstab entry:
```

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       

```

---

### Post by explicitly ambiguous on 2008-04-04
bumpity bump...

...any ideas where to start looking for some kind of solution or workaround -- I don't want my friend getting a bad impression of linux! ;-)

---

### Post by explicitly ambiguous on 2008-04-07
I hate replying to my own posts but...

I noticed that on my desktop PC dmesg also spits out 

```
cdrom: This disc doesn't have any tracks I recognize!
```

although I have no other problems burning CD/DVDs.  So I assume that this has nothing to do with the problem and is normal (my Desktop PC is running Ubuntu Hardy).

The CDs showing up with different tracks I can repeat on my Desktop too (is it looking up an online database to give me the weird track info??)

Anyway, the result is that the problem is reduced to:
[LIST]
[*]How do I get the CD/DVD burner to burn without error?

[*]Is it related to the fact that the drive is on a docking station (media slice)?

[*]Where should I start looking for a solution?
[/LIST]

Any help or ideas would be very appeciated!

---

### Post by explicitly ambiguous on 2008-04-09
Perhaps someone knows the answer to this:

Should I file this as a bug?

---

### Post by explicitly ambiguous on 2008-04-15
Please...   ...someone must even have a few thoughts on this?? no?  Just a hint as to somewhere to start looking for a solution...

Anyone???

---

