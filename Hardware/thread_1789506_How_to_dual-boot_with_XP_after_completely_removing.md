---
title: "How to dual-boot with XP after completely removing XP?"
date: 2011-06-23
forum: Hardware
---

### Post by keelx on 2011-06-23
I am running an hp pavillion dv6000 with ubuntu 11.04 (classic mode(gnome), no effects), and I am wanting to use some programs that just aren't supported in wine. I don't want to get rid of my beloved ubuntu, I want to dual-boot with windows xp. I have the windows xp install cd, but it stops in the middle of installation saying 'Setup could not find any hard disk drives installed on your computer'. When installing ubuntu, I completely erased windows XP, so do I need to mess with my partitions or something? If so, how do I do that? What is the best way for me to acheive what I want? Preferably, in step-by-step instructions.

---

### Post by Ezlivin on 2011-06-23
You might have some problems here as it's normally far easier to  resize xp and then install ubuntu. For the step by step guide you could try [http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm) [ ignore the page 2 backing up grub menu.lst as 11.04 uses a different system ] so the last step (re-installing grub after xp installation) is covered on point #13 here [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

Or you could try backing up your ubuntu installation using something like remastersys [http://maketecheasier.com/backup-ubuntu-with-remastersys/2008/12/22](http://maketecheasier.com/backup-ubuntu-with-remastersys/2008/12/22) to backup ubuntu, format the whole disk and then do xp and the remastersys installation of ubuntu.

---

### Post by oldfred on 2011-06-24
Did you create a primary NTFS partition with the boot flag set?

Windows either needs a blank drive or a primary partition to install into. It only sees primary as bootable and only works with those with the boot flag.

It also installs to blank drives as it then can create its own partition.

---

### Post by keelx on 2011-06-24
> **oldfred said:**
> Did you create a primary NTFS partition with the boot flag set?

Windows either needs a blank drive or a primary partition to install into. It only sees primary as bootable and only works with those with the boot flag.

It also installs to blank drives as it then can create its own partition.
I created a new primary partition in /dev/sda3, ntfs, and set the boot flag on. Windows still doesn't recognize it. Still that same message. Do I need to do anything else?

---

### Post by mastablasta on 2011-06-24
try to create new partition and leave it blank (no file system) then use the fdisk on windows isntall cd to format it to ntfs. or perhaps the option will be offered automaticly.

---

### Post by Zimmer on 2011-06-24
Why not try VM Virtualbox and install your XP in a Virtual Machine?
[http://www.virtualbox.org/](http://www.virtualbox.org/)
I currently do this in order to run Line6 guitar software.

Ensure you go to the site (not the Ubuntu repositories) and use their version which provides support for USB .Oh, and read the instructions well first... :)

---

### Post by keelx on 2011-06-24
> **mastablasta said:**
> try to create new partition and leave it blank (no file system) then use the fdisk on windows isntall cd to format it to ntfs. or perhaps the option will be offered automaticly.
Do you mean unallocated or unformatted space? And do I still need the boot flag on?

Edit: Tried to do it without a file system, still wouldn't recognize it.
Tried nfts, tried fat32, tried unallocated, even tried fat16. None work.
Setup could not find any hard disk drives installed on your computer.
And it won't let me do any fdisk or anything, it loads up all the files, says 'setup is starting windows', then I have a choice of a recovery console or to start windows xp installation, both lead me to the error message stated above.

---

### Post by oldfred on 2011-06-24
Is BIOS still seeing drive when you boot? Or does Ubuntu still boot? 

You are not trying to install to a USB drive are you?

---

### Post by keelx on 2011-06-24
> **Zimmer said:**
> Why not try VM Virtualbox and install your XP in a Virtual Machine?
[http://www.virtualbox.org/](http://www.virtualbox.org/)
I currently do this in order to run Line6 guitar software.

Ensure you go to the site (not the Ubuntu repositories) and use their version which provides support for USB .Oh, and read the instructions well first... :)
Got me further along, but now it says it doesn't recognize the cd I've put in, saying that there is no version of windows installed previously, and to please instert one of the following, with a list of windows xp versions. I thought the cd I was using *was* the correct cd, should I have to change cd's to something different?

---

### Post by oldfred on 2011-06-24
Does it say it is an upgrade version and not a full install? Upgrades cannot be used as a full install and have to have a valid version already installed.

---

### Post by keelx on 2011-06-25
> **oldfred said:**
> Does it say it is an upgrade version and not a full install? Upgrades cannot be used as a full install and have to have a valid version already installed.
Okay that was an upgrade cd. I was mistaken. I got the complete windows xp installer, and it said 'No valid system partitions were found. Setup is unable to continue.' Same problem as before.

---

### Post by oldfred on 2011-06-26
System partition is a primary NTFS partition with the boot flag. Is the NTFS partition primary sda1 thru sda4?

---

### Post by keelx on 2011-06-28
> **oldfred said:**
> System partition is a primary NTFS partition with the boot flag. Is the NTFS partition primary sda1 thru sda4?
Primary nfts partition with boot flag, dev/sda3. Does it need to be mounted or anything?

---

### Post by oldfred on 2011-06-28
I do not see the problem. But I have not installed XP for about 5 years.

Did you change BIOS to SATA and/or AHCI? Drive has to be in IDE mode or you have to add special drivers. When I changed my newer motherboard to AHCI mode my Ubuntu still booted and XP blue screened. It is easier to install the AHCI drivers during install but standard procedure is from a floppy.

---

### Post by keelx on 2011-07-06
> **oldfred said:**
> I do not see the problem. But I have not installed XP for about 5 years.

Did you change BIOS to SATA and/or AHCI? Drive has to be in IDE mode or you have to add special drivers. When I changed my newer motherboard to AHCI mode my Ubuntu still booted and XP blue screened. It is easier to install the AHCI drivers during install but standard procedure is from a floppy.
Sorry, but I honestly have no idea what any of that means. Point is now moot, though, I can't seem to find a full install cd anywhere.

---

### Post by littlejoe5 on 2011-07-28
By now you may have found your answer. I have been using XP inside VirtualBox for a long time.  If you still haven't been able to install it, try looking for a still-packaged XP that you can buy.  They sometimes turn up at swap meets, or sometimes computer shops still have some on the shelves. These have never been used, and are not 'pirated'.  Even if you had your own complete install disk that came with your computer, it probably wouldn't install in VirtualBox, because it is designed to install in the computer that it came with. The Vbox (even though it is installed in your computer) is in fact a different computer, (a "virtual" computer). 

I do not allow my VBox windows installation to access the internet. Don't need to, when Linux is there. And Windows is just not ready for the internet - it is too suceptible to hackers, etc. in my opinion. But I thought I would need it from time to time. 

The truth is I almost never use it. Linux does nearkly everything better anyway.

---

