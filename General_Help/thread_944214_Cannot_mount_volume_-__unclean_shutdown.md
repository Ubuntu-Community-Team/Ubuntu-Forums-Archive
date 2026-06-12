---
title: "Cannot mount volume -  unclean shutdown"
date: 2008-10-11
forum: General Help
---

### Post by reggaematic on 2008-10-11
My Windows 2000 Professional isn't booting anymore, so I decided to try backup my files using Ubuntu 8.04 LTS Desktop Edition (live cd of course). I can't get to my hard drive(Lokaal station), this is the error message:

Cannot mount volume.
Unable to mount the volume 'Lokaal station'.

Details: 
$LogFile indicates unclean shutdown (0, 0) Failed to mount '/dev/sda1': Operation not supported Mount is denied because NFTS is marked to be in use. Choose one action:
Choice 1: if you have Windows then disconnect the external devices by clicking on the 'Safely Remove Hardware' icon in the Windows taskbar then shutdown Windows cleanly.
Choice 2: if you don't have Windows then you can use the 'force' option for your own responsibility. For example type on the command line: mount -t ntfs -3g / dev/sda1 / media/Lokaal station -o force Or add the option to the relevant row in the /etc/fstab file: /dev/sda1 / media/Lokaal station ntfs-3g force 0 0

Windows isn't running, I heard my hard drive shut down and get started a couple of minutes ago, I don´t have any external devices connected to the pc except for audio/screen and I don´t dare to use option 2 (I guess I risk losing my data?).

How do I solve this (I´m a n00by and I´m very busy studying as well, so I can´t get into compiling or anything like that)? Is there any way I can backup the files on my hard drive without the risk of losing all content?

---

### Post by Kevbert on 2008-10-11
You need to boot your Windows CD and run recovery mode.  From memory I think you need to do a 
```
chkdsk /v
```
on the drive and then reboot into windows and then shut it down.
Hope this helps.

---

### Post by ibuclaw on 2008-10-11
What the error message means is that you didn't shutdown your computer properly last time you used Windows.

The best fix is booting back into windows again, then shutdown cleanly.

If booting into windows is not an option for you then, as the warning message suggests, use the "-f" force option when you mount it.

Though, I would recommending running an fsck on the partition first, to check for any partition errors. Though,that doesn't say that it will find any...
ie:
```
sudo fsck -y /dev/sda1
```

Last option you could try is "ddrescue". But that is only valid if you have a drive with more than the total space of your NTFS partition free.
ie: if it's a 40GB partition, you need more than 40GB of free space.

```
sudo ddrescue /dev/sda1 /mnt/ntfs.img
```
Leave that to go for a while, depending on the size of the partition.
Once it's finished you can mount the disk image as a loopback filesystem.
```

sudo mkdir /mnt/recovered
sudo mount -t ntfs -o force,loop /mnt/ntfs.img /mnt/recovered

```

If the data is there and accessible (not corrupt and can copy from there to your home folder), you can safely reformat the bad ntfs partition and copy over the data from the mounted image file to the new one.

Hope that's given enough food for thought.
If you need any help, just give a buzz and say so.

Regards
Iain

---

### Post by Goagioou on 2008-10-11
thanks a lot , bump up up up!!--------------------------------very good wow power leveling site:**[buy WoW Gold](http://www.gogoer.com),  [World of warcraft Power Leveling](http://www.wow-powerleveling.org/wow+power+leveling.html), [World of warcraft Power Leveling](http://www.powerlevelingweb.com), [wow power leveling](http://www.powerlevelingweb.com), [wow power level](http://www.powerleveling-wow.com/siteMap.asp)**

---

### Post by reggaematic on 2008-10-12
Thanks Kevbert and Tinivole. I tried /chkdsk and it found errors on my HD, so I had them restored but after exiting the MSDOS/Windows repair and restarting nothing had changed.

It still can´t boot Windows and my pc only has a 40GB hard drive which has less than 1GB free space (probably around 400MB because I had been working on a lot of things before my computer problems started - btw that having little space hasn´t been a problem before). I do have an external hard drive but there are files on it, so I don't know whether I could/shouldn't use it.

```
sudo mount -t ntfs -3g / dev/sda1 / media/Lokaal station -o force 
``` gives mount: invalid option -- 3 and a list of mount commands and an explanation what one can do with them.

```
sudo fsck -y /dev/sda1
``` gives fsck 1.40.8 
fsck: fsck.ntfs: not found
fsck: Error 2 while executing fsck.ntfs for /dev/sda1

(I'm a n00by to Linux so I probably wrote bad commands) sudo mount -f Lokaal station or media/Lokaal station gives nothing and sudo mount -f /dev/sda1 or a combination of that gives mount: can't find /dev/sda1 in /etc/fstab or /etc/mtab

Is there any way I could still recover the data on my hard drive? How should I do this? I hope you can help me!

---

### Post by earthpigg on 2008-10-12
> gives mount: invalid option -- 3

i think that is telling you that the -3 in 

> sudo mount -t ntfs _**-3g**_/ dev/sda1 / media/Lokaal station -o force

is bad. im on a windows computer atm, so i cant type 

> man mount

myself and see what the deal is... but you can :)

---

### Post by earthpigg on 2008-10-12
mount -t ntfs /dev/sda1 -o force

??

---

### Post by ajmorris on 2008-10-12
> **reggaematic said:**
> 
```
sudo mount -t ntfs -3g / dev/sda1 / media/Lokaal station -o force 
``` gives mount: invalid option -- 3 and a list of mount commands and an explanation what one can do with them.


hi there,
that error is because of a typo :) it should be:
```
sudo mount -t ntfs-3g /dev/sda1 /media/Lokaal\ station/ -o force
```(notice there is no gap between ntfs and -3g, also, there are no spaces between the '/' and the physical block device, and between the '/' and the mount point, another typo bash would have complained about.)

This is actually all that is required on an unclean windows shutdown, you do not need to use chkdsk or fsck to check for errors, unless the windows partition contains errors, and more than just the dirty flag on the partition that is set from an unclean shutdown. What the above command does, is forces the windows partition to mount (hence the -o force) If the partition does not contain errors, the -o force will force it to bypass the dirty flag that is set on the partition, and once mounted, the dirty flag will be removed :)

AJ

---

### Post by vanadium on 2008-10-12
```
and once mounted, the dirty flag will be removed
```
I am not sure of this. It will mount, but I find it hard to believe that Ubuntu would then remove the dirty flag. Indeed the file system might not have errors despite of the dirty flag, but then, it might anyway. There is no way for you to know unless the volume has been checked.

Anyway, for backup purposes, you will be fine using the force option, but I recommend to access the drive read only. Thus, use "ntfs" rather than "ntfs-3g" in the mount options.

---

### Post by reggaematic on 2008-10-12
None of these or variations on them worked so far. I either get a list of mount usage, nothing happens or it says that that particular station doesn't exist. :(

---

### Post by vanadium on 2008-10-12
I am not surprised. There are spaces in the name of your mount point. Just attempt this

```

sudo mkdir rescue
sudo mount -t ntfs -o force /dev/sda1 rescue

```

You should now be able to access your data read-only under the directory "rescue".

---

### Post by ajmorris on 2008-10-12
> **vanadium said:**
> ```
and once mounted, the dirty flag will be removed
```I am not sure of this. It will mount, but I find it hard to believe that Ubuntu would then remove the dirty flag. Indeed the file system might not have errors despite of the dirty flag, but then, it might anyway. There is no way for you to know unless the volume has been checked.


ubuntu/linux doesnt remove the dirty flag, however, been successfully mounted, unflags a dirty partition (the equivalent of booting windows, then rebooting)

>          I am not surprised. There are spaces in the name of your mount point. Just attempt this

```
   
     sudo mkdir rescue
sudo mount -t ntfs -o force /dev/sda1 rescue 
```You should now be able to access your data read-only under the directory "rescue".     oh sorry, missed the '\' i fixed it in my initial command....

[quote=reggaematic]None of these or variations on them worked so far. I either get a list of mount usage, nothing happens or it says that that particular station doesn't exist[/quote]

sorry, i missed a space in the mount point as stated above... try running:
```

sudo mount -t ntfs-3g /dev/sda1 /media/Lokaal\ station/ -o force 
``` . If this doesnt work, can you please post the output of it, and
can you please post the output of ```
sudo fdisk -l
``` and the output of ```
sudo fsck -y /dev/sda1
```AJ

---

### Post by caljohnsmith on 2008-10-12
If there are no really serious problems with your Windows NTFS partition, and the only issue is an "unclean shutdown", there is a great program in linux called "ntfsfix" that will take care of that:
```
sudo apt-get install ntfsprogs
sudo ntfsfix /dev/sda1
```
If ntfsfix says it was successful, you should be able to mount the volume; but it may be your Windows has more serious problems than ntfsfix can fix. And by the way, you should use the "/r" option with chkdsk if you want to do the most complete scan and fix, because that will handle bad sectors as well as file system problems:
```
chkdsk /r
```

---

### Post by RobOrr on 2008-10-13
the force command that everyone is showing you works perfectly if the only thing wrong is that windows didn't shutdown cleanly, e.g. you turned off the power, windows is an *** and crashed, etc. I have never had a problem with forcemounting, however doing so when the disk is damaged may cause more problems. If you cannot actually boot into windows normally, then I would imagine your disk is damaged and therefore needs some fixing. the safest method to mount it is always to just get windows running, then shut it down normally, as this releases windows' hold on the device.

---

### Post by reggaematic on 2008-10-14
```
sudo fsck -y /dev/sda1
```
fsck 1.40.9 (13-Mar-2008)
fsck: fsck.ntfs: not found
fsck: Error 2 while executing fsck.ntfs for /dev/sda1

```
sudo fdisk -l
```
Disk /dev/sda: 40.0 GB, 40016019456 bytes 
255 heads, 63 sectors/track, 4865 cylinders 
Units = cylinders of 16065 * 512 = 8225280 bytes 
Disk identifier: 0xbcbfbcbf 
Device Boot   Start End    Blocks Id System 
/dev/sda1 * 1 4865 39077786 7 HPFS/NTFS

```
sudo mount -t ntfs-3g /dev/sda1 /media/Lokaal\ station/ -o force
```
First gives:
$Logfile indicated unclean shutdown (0, 1)
fuse: failed to access mountpoint /media/Lokaal station: No such file or directory
But when I click on "Lokaal station" in Places I can now access my files!! Thank you!
 


```
chkdsk /r
``` found problems and probably fixed them and ```
sudo apt-get install ntfsprogs
sudo ntfsfix /dev/sda1
``` only took a couple of seconds to scan and gave no output other then unpacking ntfsprogs and scanning briefly.

I still can't boot Windows - that is I get a blue screen (page_fault_in_nonpaged_area, STOP: 0x00000050 which can have several causes among others unclean shutdown) before I can log in to Windows whatever way I try to (last known good configuration, safe reboot and so on).



My main problem now is (I managed to backup a lot, I've got about 4.5 GBs of free space which I can maybe increase to around 18GB free space): how can I rescue my Windows install? I installed so many Giveawayoftheday programs and several other study programs that I would have to pay for again if I had to install everything upon scratch. I'd very, very much like to be able to boot Windows again - I hope you can help me with this!

---

### Post by caljohnsmith on 2008-10-14
> **reggaematic said:**
> 
```
chkdsk /r
``` found problems and probably fixed them and ```
sudo apt-get install ntfsprogs
sudo ntfsfix /dev/sda1
``` only took a couple of seconds to scan and gave no output other then unpacking ntfsprogs and scanning briefly.

I should have mentioned that if chkdsk finds any problems and tries to correct them, it is a good idea to run it again until it claims there are no problems since it can take more than one try; so I would run it again if I were you just to make sure. 

Also, the "ntfsfix" shouldn't terminate without any output whether the Windows partition is OK or not. Try doing:
```
sudo umount /dev/sda1
sudo ntfsfix /dev/sda1
```
In other words, make sure your sda1 partition is mounted and then run the ntfsfix command. If sda1 is OK, you should get an output like:
```
Mounting volume... OK
Processing of $MFT and $MFTMirr completed successfully.
NTFS volume version is 3.1.
NTFS partition /dev/sda1 was processed successfully.
```

The next thing I would try is using "testdisk" to make sure your Windows partition boot sector parameters are OK:
```
sudo apt-get install testdisk
sudo testdisk
```
After starting testdisk, choose "no log", choose the correct HDD and "proceed", choose "intel", choose "advanced", select the Windows XP partition, choose "boot", then choose "Rebuild BS"; if testdisk gives you an error about boot sectors not matching, then choose "write". After you are done doing the "rebuild BS" in testdisk, reboot and let me know what happens. :)

---

### Post by reggaematic on 2008-10-15
Yesterday and today I ran chkdsk /r several times again; every time thereafter Windows says the disk seems to be ok, but when I boot again it found errors again one of the times. Ntfsprogs now scanned for a couple of seconds and gave more output, just like you wrote and a little more. It now said NTFS partition /dev/sda1 was processed successfully. Windows still won't boot properly, though.

BTW My HD hasn't been partitioned, I only have one unpartitioned 40GB HD. ```
sudo apt-get install testdisk
sudo testdisk
```gives
Reading package lists... Done
Building dependency tree
Reading status information... Done
E: Couldn't find package testdisk
Testdisk: command not found

---

### Post by caljohnsmith on 2008-10-15
To run testdisk, you'll need an internet connection, and you'll also need to enable all your repositories in System > Prefs > Software Sources. Do you have an internet connection from wherever you are running those commands?

Also, it doesn't sound good that Windows continually finds errors. How old is that HDD? I would recommend running some HDD diagnostic tests on it; if you have a CD that came with the drive, try using that, otherwise you can use the [Ultimate Boot CD]("http://www.ultimatebootcd.com/") as that has lots of HDD tests you can run.

---

### Post by ajmorris on 2008-10-16
> **reggaematic said:**
> 
 
```
sudo mount -t ntfs-3g /dev/sda1 /media/Lokaal\ station/ -o force
```
First gives:
$Logfile indicated unclean shutdown (0, 1)
fuse: failed to access mountpoint /media/Lokaal station: No such file or directory
But when I click on "Lokaal station" in Places I can now access my files!! Thank you!
 
 
I dont know if you're still watching this thread, but sorry, something if forgot to mention just on this. The linux hotpluggin daemon (what auto mounts devices for you) automatically creates a temporary mount point, for which your device is mounted to, according to the label set on the device. The mount point (in your case /media/Lokaal station) needs to be created before trying to mount to it (i.e sudo mkdir /media/Lokaal\ station/) This is for manual mounting, as well as manually defining a mount in /etc/fstab. I'm glad you can access your files now though :)
 
 
AJ

---

### Post by reggaematic on 2008-10-29
Thanks caljohnsmith and ajmorris. I tested my hard drive and I couldn't find any hard drive errors, but I also can't boot Windows any further. So you're saying that it's normal that my hard drive didn't get recognized at first and that this means that it doesn't indicate there's an error or that this is the normal procedure?

---

### Post by caljohnsmith on 2008-10-29
I would highly recommend trying out the testdisk procedure in post #15, because it might be that testdisk will be all it takes to fix the problem. If you don't have an internet connection from your Live CD to download it, then you could download the [SystemRescueCD]("http://www.sysresccd.org/") and use that since testdisk comes with it. Let us know how it goes. :)

---

### Post by reggaematic on 2008-10-29
Thanks, I will! Downloading it right now. I just saw there is no pagefile.sys file on my HD, do you maybe know if there should be one if Windows is not running - or maybe this is one of the problems?

---

### Post by alienprdkt on 2008-10-29
could try force:

in fstab:
/dev/sda? /media/windows ntfs-3g defaults,force 0 0

if does not work could try:

#sudo ntfs-3g /dev/sda? /media/windows -o force

in both cases where "?" is your actual drive you want to mount

---

### Post by alienprdkt on 2008-10-29
Make sure you have it in fstab

---

### Post by reggaematic on 2008-10-30
> **caljohnsmith said:**
> I would highly recommend trying out the testdisk procedure in post #15, because it might be that testdisk will be all it takes to fix the problem. If you don't have an internet connection from your Live CD to download it, then you could download the [SystemRescueCD]("http://www.sysresccd.org/") and use that since testdisk comes with it. Let us know how it goes. :)

OK, I tried testdisk on the System Rescue CD as you wrote in post 15. It looked promising at first:

```
disk /dev/sda - 40 GB / 37 GiB - CHS 4865 255 63
      Partition         Start          End     Size in sectors 
1 * HPFS -NTFS 0 1 1 4864 245 40 78155272

Boot sector
Error: size boot_sector 78155573 > partition 78155572
Status: Bad

Backup boot sector
Status: Bad

Sectors are not identical


A valid NTFS Boot sector must be present in order to access any data; even if the partition is not bootable

filesystem size 78155572 78155573
sectors_per_cluster 8 8 
mft_lcn 4 4
mftmirr_lcn 4884760 4884760
clusters_per_mft_record -10 -10
clusters_per_index_record 1 1
Extrapolated boot sector and current boot sector are different
```

Then after choosing Write:

```
78155572

Boot sector
Status: OK

Backup boot sector
Status: OK

Sectors are identical
```

Windows won't boot any further than before :(

After rebuilding I chose quit, should I have gone for dump or list instead? I tried the Ultimate Boot cd again but it now only gave the prompt Boot: , what should I type to be able to use it? Or should I do something else, how should I proceed to get my W to boot again?

---

### Post by caljohnsmith on 2008-10-30
In order to boot Windows, do you set it first in the BIOS boot order, or are you trying to boot it from Grub? Also, what exactly happens when you boot Windows now and what errors do you get? Lastly, please post:
```
sudo fdisk -lu
```

---

### Post by reggaematic on 2008-10-30
First and only boot option when booting from HD is Windows 2000 Pro (the HD hasn't been partitioned). Windows 2000 boots partly but a blue screen appears before I can log in: the white loading screen (it says "Booting...") loads until about 3/4 (a little less far than in the attachment) until a blue screen appears saying

```
page_fault_in_nonpaged_area
** STOP: 0x00000050 (0xE5E70577,0x00000001,0x8193A213,0x00000002)
```

It is the same way when I boot Windows in Safe Mode or Last Known Good Configuration as it is for booting the normal way.

sudo fdisk -lu gives

```
sudubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 40.0 GB, 40016019456 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78156288 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xbcbfbcbf

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    78155634    39077786    7  HPFS/NTFS
```

---

### Post by caljohnsmith on 2008-10-30
Probably you're going to have to either do a "Windows repair" or a complete reinstall I think. Do you have your original Win 2000 Install CD?

---

### Post by reggaematic on 2008-11-03
Yes, I still have it. I tried Windows repair (normal way and emergency repair) and it didn't get the pc to boot any further. I haven't tried 4 boot floppies yet though. I couldn't partition the HD either using Ubuntu to install Ubuntu or another Windows, it says that the HD can't be unmounted since it's busy. I'm still looking for a way to back-up some data (Powerarchiver passwords for encrypted files and some more and school programs which I would have to pay for if I want to install them on another pc/HD). Thanks for your help!

---

### Post by Brookesy on 2008-11-17
> **vanadium said:**
> I am not surprised. There are spaces in the name of your mount point. Just attempt this

```

sudo mkdir rescue
sudo mount -t ntfs -o force /dev/sda1 rescue

```

You should now be able to access your data read-only under the directory "rescue".

Sorry to resurrect a bit of an old thread, but this worked perfectly for me. I wrote that in and the little baby popped up on my desktop as its original name and everything. Thanks mate.

EDIT: windows still won't recognise it, my IDE drive is my C: and my SATA drive is the one being bad. For some reason in the 'safely remove hardware' thingo, it is reading my removable sata drive as my C:, there fore I can't remove it. I don't understand, but I'll keep working on it, thanks for the help!

---

### Post by TeXtonyx on 2008-11-17
"Yes, I still have it. I tried Windows repair (normal way and 
emergency repair) and it didn't get the pc to boot any further. 
I haven't tried 4 boot floppies yet though."

---------------------------------

[http://www.theeldergeek.com/repairing_windows_xp.htm](http://www.theeldergeek.com/repairing_windows_xp.htm)

Once the inspection is complete, files will start to load from the 
CD to begin the installation. Eventually the screen shown in Figure
02 will be displayed offering three options. This is the point 
where the majority of confusion occurs about repairing a current 
installation. The second option asks if you want to repair an XP 
installation using Recovery Console. In some situations this may be
the desired course of action, but in this case we want to repair 
XP without using Recovery Console. Rather than the second option, 
select the first option to set up Windows by pressing Enter.

--------------------------------------------

The above quote is found close to the bottom of the page.
Some people don't realize that there is a second repair screen
offered as shown in figure 3 on the webpage provided above.

I seen to recall that if you continue with a fresh install of XP
that it recognizes your current Windows installations and offers
to establish a new copy of Windows in C:\Windows.000

This leaves nearly all the data intact except My Documents.
But most programs won't run, you have to reinstall them.
But if you have the installation file/folder on the drive
rather than a cd install, that works out ok.

---

### Post by reggaematic on 2008-12-21
TeXtonyx thnx for your answer. Does this also hold for Windows 2000?

> **TeXtonyx said:**
> [url]Once the inspection is complete, files will start to load from the 
CD to begin the installation. Eventually the screen shown in Figure
02 will be displayed offering three options. This is the point 
where the majority of confusion occurs about repairing a current 
installation. The second option asks if you want to repair an XP 
installation using Recovery Console. In some situations this may be
the desired course of action, but in this case we want to repair 
XP without using Recovery Console. Rather than the second option, 
select the first option to set up Windows by pressing Enter.

--------------------------------------------

The above quote is found close to the bottom of the page.
Some people don't realize that there is a second repair screen
offered as shown in figure 3 on the webpage provided above.

I seen to recall that if you continue with a fresh install of XP
that it recognizes your current Windows installations and offers
to establish a new copy of Windows in C:\Windows.000

This leaves nearly all the data intact except My Documents.
But most programs won't run, you have to reinstall them.
But if you have the installation file/folder on the drive
rather than a cd install, that works out ok.

---

