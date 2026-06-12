---
title: "SATA + IDE in one machine, but IDE doesn't show up"
date: 2011-11-13
forum: Hardware
---

### Post by Jiawen on 2011-11-13
I tried installing my old IDE in my new system. The new system has a 1 TB SATA drive that was, at first boot, the only HDD on the system. After I installed the IDE, it shows up in the IDE controller screen and it shows up in the boot list (I can choose it as a boot option from the boot priority screen). However, from within Ubuntu, it doesn't show up at all. sudo fdisk -l shows only sda partitions, nothing on sdb or whatever else. 

Do I need to set some jumpers or something? Is something supposed to be declared as primary, secondary, master or slave?

---

### Post by Jiawen on 2011-11-13
Two additional things: 1) I tried switching the IDE drive from the Master IDE slot on the cable to the Slave slot, but that didn't do anything helpful; 2) I tried booting Windows (this machine also has Windows 7 on it) and it successfully showed the Windows partition on that IDE HDD. So apparently, it's Ubuntu that's not detecting the drive correctly. 

Still confused. :-k

---

### Post by Jiawen on 2011-11-14
More information: 3) I've also seen lots of people having [trouble with dmraid]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/459054"), but my system doesn't have dmraid installed. 4) The Windows partition editor detects the IDE drive with no problem. (It doesn't report what file system the partitions on that disk use, but I assume that's because Windows doesn't recognize ext3, etc.)

Help would be much appreciated!

---

### Post by dabl on 2011-11-14
Are you really running Ubuntu 8.04?  If so, the first thing I would do is boot a 11.10 Live CD, and then check the hard drives.

As for the hardware, put the jumper on "CS", and attach the drive to the end connector of the ribbon cable, not the middle connector.

Does the BIOS IDE channel offer multiple modes?  If so, try changing it.

---

### Post by Jiawen on 2011-11-14
No, this is 10.04 on the desktop. (Sorry, hadn't updated my .sig yet.) I'll try the 10.04 live CD.

I've tried both positions on the ribbon, and according to [this Seagate page]("http://seagate.custkb.com/seagate/crm/selfservice/search.jsp?DocId=196299&Hilite="), I think it's been on CS the whole time. I'm not 100% sure about the model number -- I've been trying to avoid opening the case again if possible -- and [this other Seagate page]("http://support.seagate.com/rightnow/flash/jumperguide/Seagate_ATA_Jumper_Guide.html") might conceivably give me a different jumper configuration, but I'm going to try taking the jumper off entirely (which would indicate slave mode, according to that page), and I'll check the model number then. 

The BIOS IDE screen goes by so fast that I've barely been able to read it. I'll see if there are settings I can change on next boot.

---

### Post by Jiawen on 2011-11-14
On a second read, I assume you meant the settings in the BIOS for IDE. I've tried changing them, but the BIOS doesn't seem to offer anything like master or slave settings. It has boot order, but I assume that shouldn't matter to detecting the drive...?

I actually tried a different IDE drive, because I re-thought where my old computer's /home partition was. I have this drive installed now, on the slave position on the cable and (apparently, according to the [manufacturer's website]("http://www.samsung.com/global/business/hdd/support/userguide/support_setting.html")) the jumpers, and it's the same situation: Ubuntu doesn't detect the drive, either through Gparted or through other means, while Windows detects it just fine. 

I tried the Live CD and it was the same situation: the old IDE drive is not detected by Gparted or any other method I could find. 

I'll try switching jumper positions, but if that doesn't work, I'm kind of at a loss here. What's going on?

---

### Post by Jiawen on 2011-11-15
Okay, I've tried switching the drive to the master position and to CS jumper position, but still Ubuntu doesn't detect it. :(

---

### Post by Jiawen on 2011-11-15
More data points: There were no useful changeable settings in BIOS. (ASUS P8P67LE motherboard.) I could change the boot order, but that hardly seems relevant...?

Also, I tried the ASUS disc that came with the mobo and it didn't have anything useful, and I noticed that the IDE disk doesn't appear in the Windows file explorer, though it appears in the Windows partition editor fine. :???:

---

### Post by dabl on 2011-11-15
> **Jiawen said:**
>  I noticed that the IDE disk doesn't appear in the Windows file explorer, though it appears in the Windows partition editor fine. :???: 

I think that is significant.  Usually Linux sees whatever BIOS sees, but I'm suspecting a BIOS bug here.  Is your BIOS updated to the latest version?

The boot sequence is irrelevant.  If you open the case, one experiment I would try is to disconnect the sata drive, then boot the live CD and see if the IDE drive is recognized.

---

### Post by Jiawen on 2011-11-15
> **dabl said:**
> I think that is significant.  Usually Linux sees whatever BIOS sees, but I'm suspecting a BIOS bug here.  Is your BIOS updated to the latest version?Not sure. I saw an interesting [thread]("http://www.tomshardware.com/forum/300210-30-asus-p8p67le-drive-detect-problem") that might be relevant -- it appears that other people might be having the same problem. However, I really don't want to mess around with my motherboard if I can help it.

I just found [this thread]("http://ubuntuforums.org/showthread.php?t=1691874&page=2") and related [bug report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/777325"), which seems very, very relevant (same mobo, nearly the same problems). How do I install [the patch]("http://lkml.org/lkml/2011/6/14/231"), though? I'm running 10.04, with the 2.6.32-35 kernel.
> The boot sequence is irrelevant.  If you open the case, one experiment I would try is to disconnect the sata drive, then boot the live CD and see if the IDE drive is recognized.The MBR is on the SATA drive. Will the computer boot without it?

I have a PCI IDE controller card in my older computer; if I can't get that patch working, I'll try pulling the controller card out of the old computer and using it in the new computer.

---

### Post by Jiawen on 2011-11-15
[That thread]("http://ubuntuforums.org/showthread.php?t=1691874&page=2") was right on; it seems to have been a problem with the  kernel. I followed [these instructions]("https://sites.google.com/site/lightrush/random-1/howtoinstalllinuxkernel2638onubuntu1004lucidfromubuntu1104nattytheeasyway") to upgrade to the 2.6.38 kernel and my IDE drive now seems to be mounting perfectly. 

The kernel update caused other problems (apparently this kernel is a little more finicky with Nvidia drivers than the previous one I was using), but these were again pretty easily [solved]("http://ubuntuforums.org/showthread.php?t=1771806"). 

This makes me very happy! :D Thank you, dabl, for mentioning BIOS; I wouldn't have done a motherboard-specific search without it.

---

### Post by dabl on 2011-11-16
Huh -- I have that Marvell SATA 6 Gb/s controller on my Asus P6X58D-E mobo.  But I have never tried to connect an IDE drive -- I don't think it has an IDE connector.

Glad it's fixed.

---

### Post by BillyBoa on 2011-11-16
A little late but I like to add that when using two HDDs, 

the PC will incorporate both drives by slowing down the pair to the older drives speed.

---

### Post by Jiawen on 2011-11-18
> **dabl said:**
> Huh -- I have that Marvell SATA 6 Gb/s controller on my Asus P6X58D-E mobo.  But I have never tried to connect an IDE drive -- I don't think it has an IDE connector.Something to keep in mind if/when you do! :)
> Glad it's fixed.Me too! :D Thanks again.

---

