---
title: "Need to remove ubuntu along with partitions and Grub"
date: 2010-05-15
forum: Hardware
---

### Post by lovejames on 2010-05-15
Hi,
 
I've been a hardcore fan of Ubuntu. I downloaded and installed Netbook remix version of Lucid a couple of days ago. Everything was fine until I had problem in booting up my laptop since yesterday. After the linux kernel is selected during bootup, the system just goes blank. I tried recovery mode as well but for no use. I then reinstalled the lucid lynx. First couple of logins were fine but had the same problem again. So decided to get rid of Ubuntu.
 
I now need help in restoring my Windows XP with original booting options. How do I remove the Grub screen and partitions created by Ubuntu?
 
Any help is greatly appreciated.
 
Thanks,
James.
 
P.S: I use Datamini netbook with 160GB HDD and 1 GB RAM. No CD drive available.

---

### Post by slibuntu on 2010-05-15
You need to delete the Ubuntu partitions with something like GParted. 

This will mess up your boot, so you'll need to fix the MBR so that Windows can boot again. The easist way to do this is using a Windows recovery disk, but you probably can't do that using your netbook. You need to find a utility that'll fix your MBR after you delete the partitions.

---

### Post by lovejames on 2010-05-15
Can u suggest any tools that can help me in this? I've been doing a lot of searching on the internet but of no use. I tried Super Grub Drive, Easeus Partition Manager but of no help.

---

### Post by slibuntu on 2010-05-15
The best thing to do is to create a GParted live USB and boot from that and use it to modify your partitions. Takes a while, but less chance of anything going wrong as you're booting from a live USB

---

### Post by lovejames on 2010-05-16
i tried gparted usb. It deleted the partitions. But iam stuck at grub rescue cmd at bootup. Pl help how to restore windows. Iam not very familiar wid linux commands. My netbook is completely down. Pl help

---

### Post by slibuntu on 2010-05-16
As I said in a previous post, you now need to fix your MBR. You will need to create a USB drive that contains a recovery tool, something like Hirens Boot CD will do this, it can be found here - [http://www.hiren.info/pages/bootcd](http://www.hiren.info/pages/bootcd)

Do some google searching on how to fix your MBR and you should find some guides. The problem you have now is not a Ubuntu problem, it's a general "fix MBR" problem.

---

### Post by lovejames on 2010-05-21
I have been searching all over for the net for fixmbr. I don't seem to be getting appropriate information on bootable usb for running fixmbr. I dont know what to do now. I still can't use my laptop.:mad:

---

### Post by wilee-nilee on 2010-05-21
You need a CD device and a XP install CD, I can give you this link for a XP ISO, don't install it is a OEM, it is for repair.
[http://www.aspireoneguide.com/xpinstallu3.html](http://www.aspireoneguide.com/xpinstallu3.html)

I have never been able to get a windows disc to install, or be a recovery/repair from a thumb, but thats just me.

If you download the iso burn it to a CD and get a external cd drive your ms bootloader should go back in the master boot record with no problems if the XP install isn't missing any boot.ini files.

Really I think your best just getting the OEM install disc set and reinstalling, it might be that is what you have to do anyway, not knowing what has been done to the XP install. I don't think there are any quick fixes for this, but others may have a better outlook on this.

Here is a link for installing the XP boot loader you can do this with the ISO I have linked, but you just need a cd driver.
[http://www.ehow.com/how_4891476_reinstall-xp-bootloader.html](http://www.ehow.com/how_4891476_reinstall-xp-bootloader.html)

---

### Post by slibuntu on 2010-05-21
This thread has some information that may help. There are 'boot cd's' that you can put onto a USB drive that have MBR tools that will help.

[http://forums.whirlpool.net.au/forum-replies-archive.cfm/1190768.html](http://forums.whirlpool.net.au/forum-replies-archive.cfm/1190768.html)

**DISCLAIMER** - Using some of the tools listed on the page in the link are for advanced users only. They are very powerful and can easily wipe your hard drive if you do not know what you're doing. The safest way to do an MBR fix is the one proposed by wilee-nilee in the previous post. Use at your own risk.

---

### Post by wilee-nilee on 2010-05-21
> **slibuntu said:**
> This thread has some information that may help. There are 'boot cd's' that you can put onto a USB drive that have MBR tools that will help.

[http://forums.whirlpool.net.au/forum-replies-archive.cfm/1190768.html](http://forums.whirlpool.net.au/forum-replies-archive.cfm/1190768.html)

Hirens is a great tool but really for somebody who knows what there doing, being that you can easily trash the hard drive. Learning how to do a basic MBR reload of the XP boot from a XP install disc is a better starting place. We have to be careful to give information that is usable not just links with no instructions. At the least protecting the original install is the 1st step don't you think.

We also don't know if the XP boot.ini is still in XP so a 3rd part MBR loader is not a good idea here, it could easily screw up the situation

---

### Post by slibuntu on 2010-05-21
Most definitely the XP cd solution is better, but the user doesn't have access to a CD drive, so I provided a possible solution. I should have put in a disclaimer of course, but I'd be in favour of listing all possible solutions, instead of making that decision for the user. 

Anyway, disclaimer added to my original post.

---

### Post by wilee-nilee on 2010-05-21
> **slibuntu said:**
> Most definitely the XP cd solution is better, but the user doesn't have access to a CD drive, so I provided a possible solution. I should have put in a disclaimer of course, but I'd be in favour of listing all possible solutions, instead of making that decision for the user. 

Anyway, disclaimer added to my original post.

I have a netbook and picked up a great mini cd/dvd drive that reads and writes all types from amazon for 50$ US. You can also get a cord that will plug into a regular writer then the usb port pretty cheap.

I wish I could figure out how to load the XP ISO onto a thumb, but I have tried many methods and just have never been able to get it to work.

The best thing a person can do is have a cd/dvd device and all the recovery/install disks for any installs including the OEM recovery disc set, if you want to get things done without having problems and getting stuck like this OP is.

---

### Post by lovejames on 2010-05-25
I have tried reinstalling ubuntu back thinking that I would atleast be able to use my netbook. But during installation, when it asked for partition, I chose the option "Install with Windows side by side", it did some auto partitioning or something and after some time, it showed me a message saying it failed. Now, I am not even getting Grub Rescue command at startup. It just boots into Realtek Ethernet and just shows up " OS not found" message. I am not even able to boot through Live USB. It just keeps on scrolling various commands which ends with "ata: EH Complete" or something like that. 

I even tried Gparted Live USB to see if I can completely wipeoff my hard disk and start a fresh installation. But even that doesn't show up my hard disk in the devices. Does it indicate that my whole HDD is screwed up?? :(

I am completely lost. Please help!

---

### Post by slibuntu on 2010-05-25
Are you sure the Live CD won't boot? Whe the BIOS flashes up at the start can you choose to go into a 'boot menu' or setup and make sure that booting is set to USB?

No matter what you've done to the partitions on your hard drive you should be able to boot into the Live USB.

---

### Post by lovejames on 2010-05-25
Yes. At the startup, I usually press F10 to choose the booting options. From there, I select USB. It then loads the menu of ubuntu like "Run Live CD", "Install Ubuntu" etc. After I select Run Ubuntu, it just goes blank followed by some series of commands ending with "ata: EH Complete". It goes on forever.

If I use the same USB on a different machine, Ubuntu loads normally without any problem.

---

### Post by slibuntu on 2010-05-25
I'm a little out of my depth here, but anyway.

Try hitting ESC when you see the live USB starting up (from this thread - [http://ubuntu-ky.ubuntuforums.org/showthread.php?p=9273980](http://ubuntu-ky.ubuntuforums.org/showthread.php?p=9273980) )

If you can get into Ubuntu, try fire up the installer and go into "Manually Partition". The partition table is problably a bomb site. It'll give us a better idea of what to do from here.

EDIT - Came across this thread, but don't really know what to make of it -http://ubuntu-ky.ubuntuforums.org/showthread.php?p=9273980

This one seems to relate to the problem too. It could be a hardware one unfortunately - [http://ubuntuforums.org/showthread.php?t=598837&page=1](http://ubuntuforums.org/showthread.php?t=598837&page=1)

---

### Post by lovejames on 2010-05-25
Looks like too much to work on. I always thought Linux is simpler than Windows. :(
 
Anyways, got my Windows XP restored using an external CD Drive. I can sleep peacefully tonight. :)
 
After restoring XP, I again tried installing Linux Mint through Mint4Win (similar to WUBI). It still hangs up at the same place where it was getting stuck. Even Live USB is still not working. May be I should just settle down with Windows for some time before venturing more into Linux. 
 
Thanks to everyone who helped me in this. I really appreciate your time and patience in guiding me.
 
EDIT: I am getting a new message "Missing MBR-helper" at the time of startup in Linux Mint installed through Mint4Win. I am tired. :)

---

