---
title: "Trouble installing windows? (hard disk problem)"
date: 2008-08-17
forum: General Help
---

### Post by joeyl615 on 2008-08-17
I recently tried to install windows xp over my linux ubuntu but before the instillation even started it said that the windows xp could not be saved on any of the hard disks on this computer. I'm supposing that the hard disk is formatted for linux how do i change that to xp?

---

### Post by tfosorcim on 2008-08-17
You may need to install drivers for XP to see the drive. I think this was a problem with SATA drives. 

The CD setup should allow you to partition and format the drive

[http://www.microsoft.com/windowsxp/using/setup/winxp/install.mspx](http://www.microsoft.com/windowsxp/using/setup/winxp/install.mspx)

---

### Post by Loaded.len on 2008-08-17
First, I would check your BIOS to see if your HDD is set to AHCI or not.  XP doesn't support AHCI by default and will tell you there are no drives available.

2nd, for what it's worth - you can completely destroy all partitions (Dos or non-dos) by debugging the drive.  This takes about 2 minutes if you have a win98 boot disk laying around.

Boot win98 and (instead of running setup) exit to DOS and type the following: (type what's in **bold**, the rest is feedback from the debug script)

[COLOR="Red"]THIS WILL DESTROY ALL DATA ON THE DEVICE[/COLOR]


**debug**
**-F 200 L1000 0**
**-A CS:100**
xxxx:0100 **MOV AX,301**
xxxx:0103 **MOV BX,200**
xxxx:0106 **MOV CX,1**
xxxx:0109 **MOV DX,80 **

[COLOR="Red"]WARNING: 80 is the address of your primary hard drive - HD 0, type 81 for the secondary hard drive - HD 1.[/COLOR]

xxxx:010C **INT 13**
xxxx:010E **INT 20**
xxxx:0110 Press the **Enter** (leave the line blank)
-G


you're done and you have a HDD that for all intents and purposes is blank, which is what XP prefers.

---

### Post by joeyl615 on 2008-08-17
i tried it and it still doesn't work but i did manage to get the disk a fat32 and not unknown

---

### Post by joeyl615 on 2008-08-17
The exact error message is:

Setup did not find any hard disk drives installed in your computer.

Make sure any hard disk drives are powered on and properly connected to your computer, and that any disk-related hardware configuration is correct. This may involve running a manufacturer-supplied diagnostic or setup program

---

### Post by Loaded.len on 2008-08-17
Sounds like AHCI to me.  Set your Sata operation to RAID or Autodetect or IDE (depends on the BIOS)

Oh, and if this is an Nvidia chipset board, you may need mass storage drivers during setup (F6) 

Is it a Dell XPS600 or something?

---

### Post by joeyl615 on 2008-08-17
its actually a dell inspiron 1525, and how exactly do I do the things above?

---

### Post by Loaded.len on 2008-08-17
you will need to disable AHCI and probably Flash cache (both in BIOS)

When you power on, press F2 to enter setup (I think it's F2 on newer Dells)
go to Sata operation and you should find what you're looking for.

---

### Post by joeyl615 on 2008-08-17
okay so after i do that should i re-run win98?

---

### Post by joeyl615 on 2008-08-17
ah man nevermind its working now thank you so much! THANKs!

---

### Post by Loaded.len on 2008-08-17
For the record, Windows XP WILL function with AHCI, it just doesn't have native support for it. You can't just turn it on after installing windows either, or you'll get a 0x0000007E stop code on a lovely blue screen. Since you have it working now, you have time to research how to slipstream drivers into your XP disc.  There are also ways (complicated as they may be) to enable AHCI after XP is installed, not recommended for anyone without advanced knowledge of Windows Registry. AHCI (Advanced Host Controller Interface) has a couple of advantages over IDE... primarily, it supports Native Command Queuing (also hot swapping, and staggering of disc spin-ups)

---

