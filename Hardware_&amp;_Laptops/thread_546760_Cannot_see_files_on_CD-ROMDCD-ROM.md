---
title: "Cannot see files on CD-ROM/DCD-ROM"
date: 2007-09-09
forum: Hardware &amp; Laptops
---

### Post by rodgerpb on 2007-09-09
Hello..I am sure that this is a bit of newbie problem.

I have a dedicated Ubuntu machine running Feisty (7.04).  It has two optical drives a CD/DVD ROM and a CD-RW burner.

When I put a CD in the ROM drive all I see when I double click the disc icon on the desktop  is "CD/DVD Creator File browser", and no files.  I do see the files when I use the CD-RW.

Looking at another thread, I have tried the following commands in terminal

rodger@aragorn:~$ sudo wodim --devices
Password:
Beginning native device scan. This may take a while if devices are busy...
wodim: Invalid argument. Cannot set SG_SET_TIMEOUT.
rodger@aragorn:~$ wodim --devices
Beginning native device scan. This may take a while if devices are busy...
wodim: Overview of accessible drives (2 found) :
----------------------------------------------------------------------
0    dev='/dev/hdc'   rwrw-- :  'MATSHITA'  'DVD-ROM SR-8585F'
1    dev='/dev/hdd'   rwrw-- :  'MITSUMI'  'CR-4804TE'
----------------------------------------------------------------------
rodger@aragorn:~$ -

I have installed K3B on the machine using Synaptic Package Manager

Thanks, Rodger:confused:

---

### Post by El Rogueo on 2007-09-09
> **rodgerpb said:**
> 
----------------------------------------------------------------------
0    dev='/dev/hdc'   rwrw-- :  'MATSHITA'  'DVD-ROM SR-8585F'
1    dev='/dev/hdd'   rwrw-- :  'MITSUMI'  'CR-4804TE'
----------------------------------------------------------------------


I've got some questions for you, Rodger.

Were the drives both present when you installed ubuntu? Did they require drivers to be installed under Windows?

 In the terminal output you posted, are those the brand names of your optical drives, or some combination of the two? 

Are your drives (assuming they're IDE and not SATA) configured with the proper Master/Slave jumper settings?

 If you're using IDE connections, are the two drives on the same ribbon, or do you use a combination of optical drives and hard drives?

Please provide more information about your system specifications. I'll hunt around and see if I can't find something in the meantime.

---

### Post by rodgerpb on 2007-09-09
Were the drives both present when you installed ubuntu? Did they require drivers to be installed under Windows?  **[COLOR="Red"]This was an ex Windows machine.   Both drives were present when the machine was re-prepped with ubuntu [/COLOR]**

In the terminal output you posted, are those the brand names of your optical drives, or some combination of the two? **[COLOR="Red"]These are two brand names of the two devices which are present[/COLOR]**

Are your drives (assuming they're IDE and not SATA) configured with the proper Master/Slave jumper settings?**[COLOR="Red"]They are IDE drives.  I have not adjusted the settings which did work under Windows[/COLOR]**

If you're using IDE connections, are the two drives on the same ribbon, or do you use a combination of optical drives and hard drives?**[COLOR="Red"]Just check this - the DVD ROM is on the same cable as the IDE hard drive.  The writer is on the other IDE cable.  I think that this is a standard build[/COLOR]**

[B][COLOR="SeaGreen"]Specification:  Its an AMD Athlon processor with an 80GB HDD and 256MB RAM.  Fortissimo3 sound card.  On board graphics.

Any help would be appreciated[/COLOR][/B]

Thanks Rodger:popcorn:

---

### Post by El Rogueo on 2007-09-09
> **rodgerpb said:**
> [COLOR="Red"]They are IDE drives.  I have not adjusted the settings which did work under Windows[/COLOR]

No matter how I look at this, I get the feeling the issue is that Windows was tolerant of something that Ubuntu is less readily willing to compensate for.

To eliminate a variable, please tell me what each drive is listed as, Master, Slave, or Cable Select.

---

### Post by rodgerpb on 2007-09-09
OK...I'll take a look inside.  Assume that it should be set as a slave, rather than a master.  One other thing.  I just had a look in K3b.  It could distinguish between a CD and DVD, but it said both were empty even though one was a commercial DVD and the other just has some jpegs on it

Thanks

Rodger.

---

### Post by rodgerpb on 2007-09-09
SORRY...:( I have made a mistake now I have looked at the cables. The two optical drives are on the same IDE cable.  the one which is not reading (the DVD ROM) is selected as master.  The CD-RW  which is reading the disks is selected as the slave.

Don't know whether this makes it worse or better.  

Any help again will be appreciated

Thanks again

Rodger

---

