---
title: "DVD drive not recognized"
date: 2009-02-28
forum: Hardware
---

### Post by gurkelur on 2009-02-28
Hello,

For some reason, Ubuntu 8.04 can't find my DVD drive. I've installed Medibuntu, and the lib for playing decrypted DVDs. Nothing shows in nautilus when I insert the DVD, and when I try opening the disc with vlc, it tells me "Unable to open 'dvd://'".

I ran "sudo lshw -C disk". This is what comes up:

```
  *-disk                  
       description: ATA Disk
       product: SAMSUNG SP2514N
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: VF10
       serial: S08BJ1HL338129
       size: 232GiB (250GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=ee95ee95
  *-disk
       description: SCSI Disk
       product: 6DLAT80
       vendor: HDT72251
       physical id: 0.0.0
       bus info: scsi@3:0.0.0
       logical name: /dev/sdc
       version: V43O
       size: 153GiB (164GB)
       capabilities: partitioned partitioned:dos
       configuration: signature=bdc48aaa

```

Which is my two hard drives. How can Ubuntu find my optical drive?

---

### Post by gurkelur on 2009-03-03
The DVD-drive is an Optiarc AD-7200S.

[http://www.sonynec-optiarc.com/products/hhid_dvdrw/ad7200.html](http://www.sonynec-optiarc.com/products/hhid_dvdrw/ad7200.html)

I used this drive when I installed Ubuntu. Any suggestions?

---

### Post by gurkelur on 2009-03-05
bump. The drive is connected with SATA. The manufacturer's site holds no info of drivers or nothing. Rebooting into windows is the only way of watching DVDs for me now. 

I'd really appreciate any help (:

---

### Post by gurkelur on 2009-03-07
There's really no experience on this sort of things? There's no hardware management or any control panel for devices? :\

---

### Post by gurkelur on 2009-03-09
Wow, this got solved!

I merely switched the SATA mode for the DVD-drive from IDE to AHCI in the BIOS.

That was it. Thanks to Zpeidar.

:KS

Edit: I got a pm about accessing the BIOS and doing the changes:

[quote=gurkelur][QUOTE=mmoore12]hey man i have the same problem. im new to ubuntu, relatively, and want to know how you accessed your bios and changed the dvd driVe off of IDE to AHCI[/QUOTE]
When you switch on your computer, you'll have the BIOS-screen giving information about the system. You will have to watch it, and it will tell you what key that needs to be pressed to access the BIOS. Usually it's the DEL-key. This screen will be gone quickly, so you may have to restart. Then press the key repeatably untill you enter the BIOS. It's usually blue/gray.

The following is done on a Asus P5Q motherboard. Depending on yours, menus and submenus will vary a bit.

On the main screen, I entered a menu called "Storage Configuration". Under that menu, I changed the "Configure SATA as" from IDE to AHCI. Then pressed F10 and saved and quit.

If you're not finding exactly these, try looking around in menus searching for "configure SATA as" or "emulate SATA as". There will be three options when you press enter on it. IDE, RAID and AHCI. Choose AHCI. If you've messed something up, press ESC and exit the BIOS without saving.

Remember that if you have windows and ubuntu on your system, windows will now stop recognising your DVD-drive. 

If you can't find it out, just post on the thread so others can help you. 

Cheers[/quote]

I'm no expert on this, so feel free to correct me :)

---

