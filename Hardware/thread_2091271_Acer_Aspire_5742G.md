---
title: "Acer Aspire 5742G"
date: 2012-12-04
forum: Hardware
---

### Post by axy_david on 2012-12-04
I have an acer aspire 5742G specs:
Cpu: i5-480M
Gpu: Geforce GT 540M / intel HD
OS: Ubuntu 12.04 /Win 7   both 64 bit
There are a couple of problems that i need help with:

I tried to install a beta version of nvidia driver 310.14. After 2 hours I got it installed but i only get 640x400, I can't make the resolution bigger nor do I know if the Nvidia gpu is actually working.  The nvidia application states that I don't use any drivers for X either.
I need 310.14 or higher since nvidia optimized it for better performance on linux.
Is there any fix for the annoying optimus for ubuntu, or any way to get the Nvidia GPU working? Or should I just forget linux and stick to 7?
And please, no answers like, bumblebee.
I need a tutorial for linux noobs.

---

### Post by axy_david on 2012-12-04
bump

---

### Post by oldfred on 2012-12-05
I have a standard older nVidia 9600gt and just installing the nVidia driver just works.

       nVidia Optimus and Ubuntu explained 
[http://ubuntuforums.org/showthread.php?t=1657660](http://ubuntuforums.org/showthread.php?t=1657660)
Switchable Graphics is killing my Ubuntu Experience - see post #9
[http://ubuntuforums.org/showthread.php?t=1927317](http://ubuntuforums.org/showthread.php?t=1927317)

    
I did have more issues with 12.10 and had to do all this:

       
[http://ubuntuforums.org/showthread.php?t=2081649](http://ubuntuforums.org/showthread.php?t=2081649)
# You may need headers - meta package for current version:
sudo apt-get install linux-headers-generic
# only reason to purge is there are several versions, if you know you have different nVidia use that:
#To see available  versions:
apt-cache search nvidia-sett*
# I used nvidia-current-updates & nvidia-settings-updates, example below is just nvidia-current, use version you prefer
sudo apt-get purge nvidia*
sudo apt-get install nvidia-current
sudo apt-get install nvidia-settings
sudo dpkg-reconfigure nvidia-current
sudo nvidia-xconfig
sudo reboot
May want nvidia-current, nvidia-current-updates or nvidia-current-experimental-XXX for most recent testing version.
apt-cache search nvidia-sett*

---

### Post by axy_david on 2012-12-05
> **oldfred said:**
> I have a standard older nVidia 9600gt and just installing the nVidia driver just works.

       nVidia Optimus and Ubuntu explained 
[http://ubuntuforums.org/showthread.php?t=1657660](http://ubuntuforums.org/showthread.php?t=1657660)
Switchable Graphics is killing my Ubuntu Experience - see post #9
[http://ubuntuforums.org/showthread.php?t=1927317](http://ubuntuforums.org/showthread.php?t=1927317)

    
I did have more issues with 12.10 and had to do all this:

       
[http://ubuntuforums.org/showthread.php?t=2081649](http://ubuntuforums.org/showthread.php?t=2081649)
# You may need headers - meta package for current version:
sudo apt-get install linux-headers-generic
# only reason to purge is there are several versions, if you know you have different nVidia use that:
#To see available  versions:
apt-cache search nvidia-sett*
# I used nvidia-current-updates & nvidia-settings-updates, example below is just nvidia-current, use version you prefer
sudo apt-get purge nvidia*
sudo apt-get install nvidia-current
sudo apt-get install nvidia-settings
sudo dpkg-reconfigure nvidia-current
sudo nvidia-xconfig
sudo reboot
May want nvidia-current, nvidia-current-updates or nvidia-current-experimental-XXX for most recent testing version.
apt-cache search nvidia-sett*
ok....so far i've installed bumblebee and nvidia-current.
However I want the nvidia experimental, is there any extra config i have to do so I can get it to work with bumblebee? I heard that installing the nvidia driver will break bumblebee.
Also, does the Intel Turbo boost works on 12.04? So the CPU can be OC to 2.933 from 2.6 GHz

---

### Post by oldfred on 2012-12-05
Do not know about bumblebee other than many have reported it works.

Also I have never overclocked a system. I want to keep the heat down and OC tends to push the heat levels up. Good cooling then becomes more important and if a laptop you do not have good cooling.

---

### Post by axy_david on 2012-12-06
> **oldfred said:**
> Do not know about bumblebee other than many have reported it works.

Also I have never overclocked a system. I want to keep the heat down and OC tends to push the heat levels up. Good cooling then becomes more important and if a laptop you do not have good cooling.
But the intel boost, OC the processor whenever it was necesarry not always.....
Oh well, found out its hardcoded in Bios so it\s all good.
now I have another problem, i used gparted to shrink a windows partition and I get:
```
**Shrink /dev/sda3 from 430.83 GiB to 334.33 GiB**  00:13:40    ( ERROR )             calibrate /dev/sda3  00:00:00    ( SUCCESS )             [I]path: /dev/sda3
start: 31,664,128
end: 935,188,479
size: 903,524,352 (430.83 GiB)[/I]          check file system on /dev/sda3 for errors and (if possible) fix them  00:00:18    ( SUCCESS )             ***ntfsresize -P -i -f -v /dev/sda3***             [I]ntfsresize v2012.1.15AR.1 (libntfs-3g)
Device name        : /dev/sda3
NTFS volume version: 3.1
Cluster size       : 4096 bytes
Current volume size: 462604460544 bytes (462605 MB)
Current device size: 462604468224 bytes (462605 MB)
Checking for bad sectors ...
Checking filesystem consistency ...
Accounting clusters ...
Space in use       : 356784 MB (77.1%)
Collecting resizing constraints ...
Estimating smallest shrunken size supported ...
File feature         Last used at      By inode
$MFT               :    396992 MB             0
Multi-Record       :    459916 MB        115476
$MFTMirr           :         1 MB             1
Compressed         :    459671 MB        436208
Sparse             :    451806 MB          6250
Ordinary           :    459970 MB        487571
You might resize at 356783788032 bytes or 356784 MB (freeing 105821 MB).
Please make a test run using both the -n and -s options before real resizing!
[/I]             shrink file system  00:13:22    ( ERROR )             run simulation  00:13:22    ( ERROR )             ***ntfsresize -P --force --force /dev/sda3 -s 358982090751 --no-action***             [I]ntfsresize v2012.1.15AR.1 (libntfs-3g)
No free mft record for $MFT: No space left on device
Could not allocate new MFT record: No space left on device
Device name        : /dev/sda3
NTFS volume version: 3.1
Cluster size       : 4096 bytes
Current volume size: 462604460544 bytes (462605 MB)
Current device size: 462604468224 bytes (462605 MB)
New volume size    : 358982083072 bytes (358983 MB)
Checking filesystem consistency ...
Accounting clusters ...
Space in use       : 356784 MB (77.1%)
Collecting resizing constraints ...
Needed relocations : 19385069 (79402 MB)
Schedule chkdsk for NTFS consistency check at Windows boot time ...
Resetting $LogFile ... (this might take a while)
Relocating needed data ...
Updating $BadClust file ...
Updating $Bitmap file ...
ERROR(28): Could not update runlist for attribute 0x80 in inode 0: No space left on device[/I]
```

---

### Post by axy_david on 2012-12-06
bump

---

### Post by oldfred on 2012-12-06
It says you are using 356GB and want to shrink to 334GB. Not possible. I am even surprised that it suggests you could shrink to 334GB. 

NTFS partition really need 30% free to work well and at 10% free you cannot run defrag as there is not space to copy to/from.

---

### Post by axy_david on 2012-12-06
> **oldfred said:**
> It says you are using 356GB and want to shrink to 334GB. Not possible. I am even surprised that it suggests you could shrink to 334GB. 

NTFS partition really need 30% free to work well and at 10% free you cannot run defrag as there is not space to copy to/from.
stupid Gparted, obviouslly the GUI is full of bugs....thanks for the help,
at any rate, it should be posted on a bugtrack or something, the GUI shows wrong values.
Problem solved by shrinking by 30 GB less.
One problem left:
Making bumblebee work with nvidia 310, i think I will start another thread since I don\t see this as a specifical problem to my laptop.
Thanks for the help, I really appreciate it!

---

