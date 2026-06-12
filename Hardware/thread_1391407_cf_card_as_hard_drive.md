---
title: "cf card as hard drive"
date: 2010-01-26
forum: Hardware
---

### Post by newbemac on 2010-01-26
Hi,

I have a tashiba A85-S107 laptop.  The hard drive gave up and now I am trying something new to me.  I prurchased a device that allows me to remove the hard drive, plug in a 44 pin adaptor to the HD slot then an 8 gig CF card to act as a solid state hard drive.  I first formated the cf card as "fat" in  install it.  I then placed the 9.10 dick in the cd drive and booted up.  The machine will run from the disk fine.  I then installed the OS to the cf card. I selected erase and use entire disk option and installed.  Upon competetion I reboot and on the screen appears "NO OPERATING SYSTEM FOUND"   When I remove the cf card and place it in my desk top card reader the os appears.  I then tried placed the card in a reader and plugged it into mt asus EEE maching and booted up from the cf card.  all is well and runs fine.  When I place the CF card back in the toshiba with the 9.10 cd the machine boots from the cd BUT displayes the CF card on the desk top. the bottom line is when I go the bios screen the hard drive shows NONE.  The boot order is CD drive then HD.  Sorry for the long post but I wanted to gointo as much detail as I could.

any Ideas on how to boot from the CF card that is installed as a hard drive.

newbemac

---

### Post by adam814 on 2010-01-26
Your adapter may not support booting from CF.  Also your BIOS may not play nice with the adapter.  If BIOS doesn't see the drive you won't be able to boot from it.

---

### Post by newbemac on 2010-01-26
Is there a way to cause the bios to see the drive?

---

### Post by adam814 on 2010-01-26
Update your BIOS?  Other than that you're probably at the mercy of your equipment manufacturers.

---

### Post by newbemac on 2010-01-26
this looks like a lost cause.. oh well good excuse for a new machine>>>>

thanks

---

### Post by warfacegod on 2010-01-26
> I first formated the cf card as "fat" in install it

I would strongly suggest reformating to an ext filesystem. I've never had any luck with getting Linux to run on FAT32, ext2, 3, or 4 is best. I use ext4.

---

### Post by adam814 on 2010-01-26
It can be done.  At least it can be done with syslinux, but you're right.  Any of the native Linux filesystems would be preferable.

---

### Post by warfacegod on 2010-01-26
I think the Fat format is the issue here. The OP's laptop should have the same BIOS as my Toshiba P25-s607 and the only thing mine won't boot from, so far, is an external disc drive.

---

### Post by newbemac on 2010-01-27
I started tinkering with the bios..I was able to get the machine to boot from the bios selection "FDD"  I placed the cf card in a 24 in 1 card reader and plugged it into a usb port.  I am using it now.. boots slow to be expected,  but works just fine.
thanks for the help.

---

### Post by tgalati4 on 2010-01-27
You might be able to set a custom user BIOS setting for the hard disk.  You need to dicover the Cylinders, Heads, Sectors count for the CF card.  Put those parameters in the bios for the primary disk drive and see if it boots.

CF cards are designed for long, sustained writes--like a digital camera.  Using it for Ubuntu might shorten its life and put your data at risk.  I would just replace the hard drive with a new on.

---

### Post by Megafag on 2010-01-27
> **newbemac said:**
> I started tinkering with the bios..I was able to get the machine to boot from the bios selection "FDD"  I placed the cf card in a 24 in 1 card reader and plugged it into a usb port.  I am using it now.. boots slow to be expected,  but works just fine.
thanks for the help.

I would say the slow boot has something to do with fat32 though :P

i seriously suggest you use ext3/4

---

### Post by sgosnell on 2010-01-27
He said he formatted it to FAT32 to prepare for the install, not that he kept it that way during and after the install.  I think the filesystem format is a red herring.  It's almost certainly a problem with the BIOS in the laptop, since other machines boot easily from the CF, and he now can boot from it on the original machine using a USB card reader.  It's naturally going to boot slower that way.

---

### Post by newbemac on 2010-01-27
I am not storing any data on this machine, it was more of an experiment than anything else.  I use google docs for long term storage for multi machine convienience. The laptop is very old and when this little experiment dies I'll toss the machine or experiment with it in some other way. But In the meantime I can get a little more life out of it.

---

### Post by adam814 on 2010-01-27
You might have more luck booting the machine as an LTSP client.  These can be diskless provided either your BIOS supports network boot or you use a PXE boot CD of some sort.

[https://help.ubuntu.com/community/UbuntuLTSP/LTSPQuickInstall](https://help.ubuntu.com/community/UbuntuLTSP/LTSPQuickInstall)

---

### Post by ceratophyllum on 2010-01-27
I tried this on an old Mac powerbook Lombard and Pismo and the results were bad: for some strange reason, under Debian Linux, the filesystem would always get corrupted after a while and the machine would stop booting. (Ubuntu PPC would not even boot, so I tried Debian. No idea why, it just did not see any hard drive.)

So then I tried putting Panther on the both laptops.  I found it to run painfully slow on both machines.  Replacing the CF card with a 100GB hard disk made both machines work perfectly and much more quickly.  When I was using CF there was no significant improvement in battery life.

---

