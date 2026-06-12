---
title: "Internal usb card reader"
date: 2009-01-10
forum: Hardware
---

### Post by Gillingham on 2009-01-10
I am trying to use an internal card reader with my intrepid installation on a desktop, however I can't mount a SD card using it.  

This is a multi card reader including SD and USB, it was manufactured by akasa but uses Realtek hardware (lsusb gives Bus 004 Device 004: ID 0bda:0151 Realtek Semiconductor Corp. Mass Stroage Device).  This is attached to an USB connection on the motherboard.

The drives appear in dmesg as sdc, sdd, sde (SD card), sdf and sdg (USB port).  When I look in /dev/ I see these as sde with no sde0.

However, when I insert a SD card it isn't automatically mounted and I can't mount it myself. The USB port however, does work.

I haven't added any extra kernel modules to deal with the card reader and I can't find any that seem relevant to a realtek device.

Can anyone help?

David

---

### Post by Giggity on 2009-01-31
I'll get on board trying to find help with this. Mine is a Sony MRW620-U1, but the problem is the same.  I have no idea where to even start.  Like the OP, the integrated USB port works on this reader, but everything else doesn't mount.

The strange thing is that I can see the reader in my "Removable Media" menu in GNOME, and dmesg recognizes it:

```
[    9.642020] scsi 4:0:0:0: Direct-Access     Sony     USB   HS-CF Card 3.95 PQ: 0 ANSI: 0
[    9.645720] scsi 4:0:0:1: Direct-Access     Sony     USB   HS-xD/SM   3.95 PQ: 0 ANSI: 0
[    9.649719] scsi 4:0:0:2: Direct-Access     Sony     USB   HS-MS Card 3.95 PQ: 0 ANSI: 0
[    9.652971] scsi 4:0:0:3: Direct-Access     Sony     USB   HS-SD Card 3.95 PQ: 0 ANSI: 0
[    9.657282] sd 4:0:0:0: [sdd] Attached SCSI removable disk
[    9.657394] sd 4:0:0:0: Attached scsi generic sg5 type 0
[    9.662261] sd 4:0:0:1: [sde] Attached SCSI removable disk
[    9.662309] sd 4:0:0:1: Attached scsi generic sg6 type 0
[    9.666762] sd 4:0:0:2: [sdf] Attached SCSI removable disk
[    9.666808] sd 4:0:0:2: Attached scsi generic sg7 type 0
[    9.717761] sd 4:0:0:3: [sdg] Attached SCSI removable disk
[    9.717807] sd 4:0:0:3: Attached scsi generic sg8 type 0

```

---

### Post by ninboy on 2009-04-25
I second that! My card reader is a Realtek one, connect itself to an internal usb. It was automounted in ubuntu 8.10, but now in 9.04 it won't mount...

---

### Post by noblerabbit on 2009-05-04
hey i got this:
[http://www.akasa.co.uk/akasa_english/spec_page/control_panels/spec_ak_all_01bk.htm](http://www.akasa.co.uk/akasa_english/spec_page/control_panels/spec_ak_all_01bk.htm)

any news on drivers or anything?

---

### Post by cthulhu666 on 2009-05-20
I have a laptop (Asus U6V) with an internal card reader similar to the OP's:

0bda:0158 Realtek Semiconductor Corp. Mass Stroage Device (nice spelling error :D )

I've found out, that it's a:
Realtek RTS5158 	  	Single-LUN Multi-Card 	  	UDMA-CF

And I also have the problem with cards not being detected. I believe this is a kernel/udev regression.

I am however not running Ubuntu, but Gentoo w/ latest GIT kernel (2.6.30_rc6-git3 as I type this).

Does anyone have an updated status on this issue?

Kind regards

Cthulhu

---

### Post by sloppyc on 2009-06-13
I just tried to use my card reader for the first time in 9.04.  I think it's a no-name brand from Newegg (or maybe Rosewill, I forget.  It was cheap).  

USB port works fine (plugged my flash drive in to make a USB startup drive with zero issues).  

"Removable Media" in previous releases detected the reader and even the type of slot for each card type.  Inserting a card would automagically result in its being mounted with a nice icon representing the card type on my desktop.

Nothing now.

No progress on this?

---

### Post by warpasylum on 2009-06-13
Hey guys,
     I've got the exact same issue with an Alcor Mirco Corp. Hi-speed 21-in-1 flash card reader/ writer. bought from tiger direct who said it was a sabrent internal 64-in-1 multi flash media card reader. I'll post back if I figure anything out.

btw, running jaunty on this computer.

---

### Post by kkram13 on 2010-02-23
Me too, with a Sabrent card reader model crw-uinb

It shows up as an 'Alcor Micro Corp.' in lsusb:
```

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 058f:6364 Alcor Micro Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

Putting a card in does nothing, but the USB port on the front does work. Also, both lights are always on, the red 'power' light and the green 'access' light.

The output of dmesg | grep scsi:
```

[    2.173259] scsi6 : SCSI emulation for USB Mass Storage devices
[    7.173249] scsi 6:0:0:0: Direct-Access     Generic- SD/MMC           1.00 PQ: 0 ANSI: 0
[    7.173743] scsi 6:0:0:1: Direct-Access     Generic- Compact Flash    1.01 PQ: 0 ANSI: 0
[    7.174242] scsi 6:0:0:2: Direct-Access     Generic- SM/xD-Picture    1.02 PQ: 0 ANSI: 0
[    7.174867] scsi 6:0:0:3: Direct-Access     Generic- MS/MS-Pro        1.03 PQ: 0 ANSI: 0 CCS
[    7.175100] sd 6:0:0:0: Attached scsi generic sg2 type 0
[    7.175158] sd 6:0:0:1: Attached scsi generic sg3 type 0
[    7.175215] sd 6:0:0:2: Attached scsi generic sg4 type 0
[    7.175275] sd 6:0:0:3: Attached scsi generic sg5 type 0

```

In /dev I can see /sdb, c, d, e, which come to think of it is not enough since there are 7 slots!

Has anybody made any progress on this?

Grrrr...

Mark

---

### Post by warpasylum on 2010-02-23
Hey guys,
     I don't know if this'll help or not, but I have to put the cards into my reader upside down.  Took me 3 days to0 figure that one out.  Reader works fine though with Karmic.  Worked fine with Jaunty too.  Only red light on all the time, green one only lights up if I put a card in.  Hope this helps.

---

### Post by kkram13 on 2010-02-24
The tech support at Sabrent told me to try that, too. But without seriously force, the card won't go in upside-down.

I did notice in my bios there's an option to turn PnP on or off. I wonder if that has something to do with it. Will try that probably tomorrow. Anybody else tried that?

And dare I say it, my machine is a dual-boot and in *that* other operating system *cough* Windows 7 *cough* the reader sometimes shows up, and sometimes doesn't. Putting in a card sometimes makes the drive show up, but then I cannot see the content and 'need to format the card'. Even though the card can be read in another machine. So I may well have a faulty reader. Even tech support suggested I exchange it.

Give it one more go tomorrow, and if that doesn't work... back it goes!

Mark

---

### Post by Merovius on 2010-02-26
Same problem with a new install of Karmic. HP desktop with built in reader. USB ports work fine. See's card reader but never mounts anything.

Card reader in my home built system works fine.

---

### Post by mechanizedmedic on 2010-12-20
i'm having the same issue as the others... reader worked in previous releases but now that i'm on 10.04 just the usb port works... anyone with a solution or even an idea PLEASE HELP.

edit: my reader is an internal 3.5" that plugs into the usb header on the mobo.

---

### Post by favrest on 2011-08-09
Hi,

after having similar problems in not being able to mount any sd card with even all the suggestions in the forums I wanted to share this with you. Last resort of idea was that the factory might have built in the Multi-Card reader the wrong way around compared with what is printed outside of the box!!! And miracle.... all worked perfectly fine. grrrrr  lost days in finding the bug.

Happy try.

Sincerly 
favrest

---

### Post by angus73 on 2011-12-31
Hi there, I have the same problem with a hamlet bay card reader (3.5", connected to the mobo connector).
lsusb says ID 058f:6364 Alcor Micro Corp.
USB plug works fine, but I cannot mount any SD card in the slot.

Does anybody have found out if it's a kernel problem?
Does anybody know if/where a bug about it could be reported?

Thank you!
Andrea

I run Ubuntu 11.10, kernel 3.0.0-14 32bit

---

