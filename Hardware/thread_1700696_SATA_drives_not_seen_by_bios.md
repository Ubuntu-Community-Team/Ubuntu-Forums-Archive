---
title: "SATA drives not seen by bios"
date: 2011-03-05
forum: Hardware
---

### Post by TCMGO on 2011-03-05
[FONT=Times New Roman][SIZE=3][FONT=Arial]I am excited about leaving Windows to switch to Linux (Ubuntu), but have hit a frustrating wall right out of the gate. The bios on my Abit NF7-S V2 mobo does not see my 2 SATA drives. It sees IDE drives just fine, but not SATA, though it has onboard SATA plug-ins and controller. When first booting up, the two SATA drives show up in the boot up dialogue for the SATA RIAD controller where it then states: “no valid device.”[/FONT][/SIZE]
 
[SIZE=3][FONT=Arial]But when I go into the bios, they are not there, and when I boot with the windows XP CD (I am doing a dual boot system to make the transition) to install it, it soon hits a screen that says that there are no hard drives, confirming what I see in bios. I have tried a number of suggested bios settings that I have found in googling the problem, but I get the same result. I even installed a PCI serial ATA host card (Silicon Image sil 3114) and plugged them in on it and the same thing happens. I am at wit’s end trying to figure this one out. This computer worked great in the past with SATA drives, which were connected through a Promise raid card. The card died, causing an irreparable “fatal error” in the MBR of the OS drive, so I am starting over with clean drives. Any insights or experience with this mobo? [/FONT][/SIZE][/FONT]

---

### Post by dabl on 2011-03-05
I don't know your Abit mobo, but here are some quick notions of things to try, which you may or may not have already thought of:

- check whether there is a BIOS flash update for the mobo
- disconnect all IDE devices
- double-check (swap out) the SATA cable(s)
- disable/don't use the RAID feature on the mobo
- try the "legacy IDE" or "compatibility" mode for the SATA channel
- if you get them to show up in BIOS, then boot a Parted Magic or GParted or Ubuntu Live CD, and do "Device > New Partition Table", choose "MS-DOS" and then "Apply" to write a new empty partition table.  Then you can make partitions as needed.

If Linux doesn't have a driver for that Silicon Image RAID controller, then you're not going to do a "fake RAID" with it -- you could only do a software "mdraid".

Hope this helps.

---

### Post by TCMGO on 2011-03-05
dabl,  thank you for your reply. 
 
I am looking for the latest BIOS flash update.  I am rather nervous to try this, as I have heard so many "killed the mobo" stories.
 
I tried disconnecting the IDE drive
I swapped out the SATA cables
I disabled and enabled both the serial ATA and RAID features in the BIOS
I haven't tried the "legacy IDE" or "compatibility" mode for the SATA channel.  Not sure what they are and how to do that
 
If I can get them to show up in BIOS I am pretty much there.
 
Since the *on-board* SATA plug-ins and controller are accessed through the onboard pheripheral mode (verses *on chip*), I wonder whether the SATA drives are meant to show up in the bios.  Any thoughts on this?

---

### Post by dabl on 2011-03-05
I've got both Intel and Asus (and Toshiba netbook) BIOSs.  When I go into BIOS, there's usually a menu item for SATA channel "mode", and the choices will be AHCI, and then "Legacy" or "Legacy IDE" or "Compatibility", and then if it has a RAID chip, "RAID".  The best performance for a SATA drive is normally AHCI, but Linux installers don't always see it when set to AHCI, so you can leave it in "IDE" or "Legacy" mode and it usually works for installation, then after Linux is installed you can go back in and change it to AHCI and it should work that way.  You definitely do not want it set to "RAID", unless you're very lucky and find that Ubuntu has a driver for your RAID chip.

---

### Post by TCMGO on 2011-03-05
dabl,
 
I have gone through my BIOS settings thoroughly and I cannt find anything that mentions SATA channel "mode",  "Legacy" or "Legacy IDE" or "Compatibility"
 
I may have found the problem, as it appears that I need to load the SATA drivers during the XP install in order for the SATA drives to be seen.  I need a floppy drive (A) and I am not sure whether the old one I have works or the floppy disk with drivers has gone bad.  I have not needed a floppy drive in many years.  Is there a way to do a work around a floppy drive in installing drivers during the installation?

---

### Post by psusi on 2011-03-05
Windows drivers aren't going to help your bios or Ubuntu.  You need to put the controller into AHCI mode instead of RAID mode.

---

### Post by dabl on 2011-03-06
If I'm reading this correctly, you could have a motherboard and BIOS as old as 2002:

[http://www.abit.com.tw/page/en/motherboard/motherboard_detail.php?pMODEL_NAME=NF7-S&fMTYPE=Socket%20A&pPRODINFO=BIOS](http://www.abit.com.tw/page/en/motherboard/motherboard_detail.php?pMODEL_NAME=NF7-S&fMTYPE=Socket%20A&pPRODINFO=BIOS)

Not to be arrogant, but for SATA drives, you'll do far better with a motherboard from the past 5 years.  :-(

---

### Post by cascade9 on 2011-03-06
I ran a NF7-S 2.0 for years. Lovely board for the times. 

If you dont have dead drives, I'll bet I know what the problem is- you have a SATAII drives. IIRC, the controller on the NF7-S will not work with SATAII drives. You should be able to get them working if you can set a jumper to SATAI (most drives have this option). 

If your BIOS wont see the drives, it wont matter what you do, the drives wont work. 

BTW, there is no 'work around' for the loading the drivers from floppy problem, you have to load the drivers for the controller chip from a floppy during the XP installation process. 

LOL @ giving windows advice here... 

You may need to update the BIOS for the SATA drives to be bootable if you arent using a PS/2 mouse- 

> BIOS ID:23 
Snip! 

5. Fixed an issue where SATA HDD boot up would fail without a PS/2 mouse installed.

[http://www.abit.com.tw/page/en/download/download_bios_detail.php?pFILE_TYPE=Bios&pMAIN_TYPE=Motherboard&pTITLE_ON_SCREEN=NF7-S+V2.0&pSOCKET_TYPE=Socket%20A](http://www.abit.com.tw/page/en/download/download_bios_detail.php?pFILE_TYPE=Bios&pMAIN_TYPE=Motherboard&pTITLE_ON_SCREEN=NF7-S+V2.0&pSOCKET_TYPE=Socket%20A)

> **dabl said:**
> I've got both Intel and Asus (and Toshiba netbook) BIOSs.  When I go into BIOS, there's usually a menu item for SATA channel "mode", and the choices will be AHCI, and then "Legacy" or "Legacy IDE" or "Compatibility", and then if it has a RAID chip, "RAID".  The best performance for a SATA drive is normally AHCI, but Linux installers don't always see it when set to AHCI, so you can leave it in "IDE" or "Legacy" mode and it usually works for installation, then after Linux is installed you can go back in and change it to AHCI and it should work that way.  You definitely do not want it set to "RAID", unless you're very lucky and find that Ubuntu has a driver for your RAID chip.

I think that 'Legacy', 'comptibility' etc mode are newer than the old NF7-S 2.0 controller, it just had 'RAID' and 'AHCI' modes (or was it 'SATA' mode?). Been awhile since I've seen the BIOS though.

---

