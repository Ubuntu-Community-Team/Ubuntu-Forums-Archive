---
title: "How to install Windows after Ubuntu"
date: 2008-11-26
forum: General Help
---

### Post by Liviu-Theodor on 2008-11-26
Maybe you will have a case where somebody wants to install Windows, but already have Ubuntu (or any other distribution of Linux). Maybe you want to keep also Linux, but do not want to erase it, and reinstall it after Windows.

These are the steps:

1. First, use gPartEd to make room for Windows partitions. You can also format them under Linux. Sometimes it is necessary to move the swap partition. Just be sure to not format the Linux partitions.

2. Probably you will have at least one partition that changed its UUID. To solve this, you must run in a terminal:
```
blkid
sudo cp /etc/fstab /etc/fstab.backup
gksudo gedit /etc/fstab
```
At the last command use the new values found with the first command.

3. Now install normally Windows on the new partition(s), formatted with FAT32 or NTFS. After doing this, GRUB will be erased by the Windows bootloader.

4. Using a Ubuntu live-cd, use the option [FONT="Courier New"]System->Administration->Restore GRUB[/FONT]. After doing this, you will not see Windows at the GRUB bootloader.

5. Now edit the file [FONT="Courier New"]/boot/grub/menu.lst[/FONT] (maybe you need superuser rights to do that). Append the following lines at its end:
```
# This entry added for a non-linux OS on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
chainloader	+1
```
Or change accordingly if you have another version of Windows, and/or another partition configuration.

6. Restart and enjoy either Linux or Windows.

---

### Post by PoopyTheJ on 2008-11-26
Step1 Use Gparted to Resize the partition, do you have a good walkthrough or further info on how to do this? I've used some windows partition tools in the past and resizinig partitions has always been a nightmare for data security. There's been times it's worked fine and many others where the info on the drive was for all intents and purposes hosed. So if you have any good ideas for NOT losing data I'd appreciate it.
Further, Linux can read NTFS but writing can really be a challenge. So aside from FAT32, which is limited to 8GB in size for reliability purposes, what other ways or Filesystems are good for shared drives between Windows and Ubuntu?

---

### Post by bodhi.zazen on 2008-11-26
> **PoopyTheJ said:**
> Step1 Use Gparted to Resize the partition, do you have a good walkthrough or further info on how to do this? 

Gparted is quite easy and quite reliable.

[Gparted Documentation](http://gparted.sourceforge.net/documentation.php)

---

### Post by Liviu-Theodor on 2008-11-27
This was my experience installing Windows after Ubuntu 8.04, at somebody else's computer. I formatted NTFS using gPartEd, and Windows accepted the two partition I have made with no comment whatsoever (of 30 GB and 100 GB). It installed absolutely normal. I never had any issue with Ubuntu writing to NTFS partitions (I have seen Ubuntu starting with 7.04 version).

---

### Post by thestig_992 on 2008-11-27
Careful when installing on seperate HDs though, windows insists on being on hd0. I nearly lost quite a bit of data from this mistake...

---

### Post by bodhi.zazen on 2008-11-27
> **thestig_992 said:**
> Careful when installing on seperate HDs though, windows insists on being on hd0. I nearly lost quite a bit of data from this mistake...

Windows can be installed on a second hard drive without *much* problem. You need to configure grub.

You need to "map" your hard drives.

See :

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

Specifically: 

[http://users.bigpond.net.au/hermanzone/p15.htm#Chainloading_Windows_using_map_commands](http://users.bigpond.net.au/hermanzone/p15.htm#Chainloading_Windows_using_map_commands)

---

### Post by PoopyTheJ on 2008-12-02
SO I've resized and installed windows but I can't find the System-Administration-Restore Grub on the Intrepid 8.10 LiveCD. Anywhere or how else to do this?

---

### Post by oldos2er on 2008-12-02
AFAIK there is no System-Administration-Restore Grub, you have to do it manually. See [http://ubuntuforums.org/showthread.php?t=353775](http://ubuntuforums.org/showthread.php?t=353775)

---

### Post by PoopyTheJ on 2008-12-02
Ok so I thought I followed the steps in this guide however I apparently missed this step
blkid
sudo cp /etc/fstab /etc/fstab.backup
gksudo gedit /etc/fstab

I then reinstalled Grub after installing windows using this
sudo grub
 find /boot/grub/stage1
 root (hd0,x)
 setup (hd0)
 quit

I now show 3 different Ubuntu installations no windows installation in grub and I get an error when I choose my Ubuntu install of 
Error17:Cannot mount selected partition

****, what do I do now, I hate making stupid mistakes...

---

### Post by PoopyTheJ on 2008-12-02
Here's my output of fdisk -lu

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x56975697

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    64276064    32138001    7  HPFS/NTFS
/dev/sda2        64276065   103346144    19535040   83  Linux
/dev/sda3       103346145   484375814   190514835   83  Linux
/dev/sda4       484375815   488392064     2008125   82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa8d4a8d4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   488392064   244196001   83  Linux


Device sdb is a secondary drive for media, sda2 is my linux root partition and sda3 is home, sda1 is my windows install. What can I do to fix grub?

---

### Post by PoopyTheJ on 2008-12-02
Needed to edit grub and set the correct partitions, fixed.

---

### Post by Slim Odds on 2008-12-02
> **Liviu-Theodor said:**
>  
```
# This entry added for a non-linux OS on /dev/sda1
title        Windows Vista/Longhorn (loader)
root        (hd0,0)
[COLOR=Red]savedefault[/COLOR]
chainloader    +1
```

Most people probably don't want the "savedefault"!!!!

---

### Post by PoopyTheJ on 2008-12-03
What's "savedefault" do?

---

### Post by Slim Odds on 2008-12-03
> — Command: **savedefault** num
Save the current menu entry or num if specified as a default entry. Here is an example:       

               default saved
               timeout 10
          
    title GNU/Linux
    root (hd0,0)
    kernel /boot/vmlinuz root=/dev/sda1 vga=ext
    initrd /boot/initrd
    savedefault
          
    title FreeBSD
    root (hd0,a)
    kernel /boot/loader
    savedefault

              With this configuration, GRUB will choose the entry booted previously as the default entry.          
You can specify `fallback' instead of a number. Then, next fallback entry is saved. Next fallback entry is chosen from fallback entries. Normally, this will be the first entry in fallback ones.From the grub manual....

---

### Post by bodhi.zazen on 2008-12-03
> **PoopyTheJ said:**
> What's "savedefault" do?

savedefalut saves that selection you make and makes it the default.

To be honest, the link I gave you earlier is the best source of information on grub and you should take a look at it.

---

### Post by sim-value on 2008-12-10
I made a 30 Gigs partition with FAT32 ... (also tried just having it as empty space)

but during the Windows installation in the part before EULA i always get a Bluescreen .. any ideas ?

Im trying to install XP btw ...

---

### Post by Liviu-Theodor on 2008-12-15
I think you should declare the Windows boot partition as primary. Maybe you have declared it as logical, inside the extended partition?

---

### Post by Jammanuser on 2008-12-31
> **sim-value said:**
> I made a 30 Gigs partition with FAT32 ... (also tried just having it as empty space)

but during the Windows installation in the part before EULA i always get a Bluescreen .. any ideas ?

Im trying to install XP btw ...

If all else fails, use BING! :P See [this thread]("http://ubuntuforums.org/showthread.php?t=1024929"), where I describe how to do just that...as well as other cool stuff! :D

Cheers! :popcorn:

-Jam man

:guitar:

---

### Post by Liviu-Theodor on 2009-01-08
> **PoopyTheJ said:**
> SO I've resized and installed windows but I can't find the System-Administration-Restore Grub on the Intrepid 8.10 LiveCD. Anywhere or how else to do this?

> **oldos2er said:**
> AFAIK there is no System-Administration-Restore Grub, you have to do it manually. See [http://ubuntuforums.org/showthread.php?t=353775](http://ubuntuforums.org/showthread.php?t=353775)

You could also dowload the grub cd from [http://supergrub.forjamari.linex.org/?section=download]("http://supergrub.forjamari.linex.org/?section=download").

---

### Post by Jammanuser on 2009-01-08
> **sim-value said:**
> I made a 30 Gigs partition with FAT32 ... (also tried just having it as empty space)

but during the Windows installation in the part before EULA [COLOR="Red"]i always get a Bluescreen[/COLOR] .. any ideas ?

Im trying to install XP btw ...

Also...what kind of BSOD are you getting? :) Could you describe it please? I recently got a blue screen trying to install XP, and it was because the XP installation didn't have a AHCI driver integrated with it. what i did to install XP, was to change the SATA operating mode from AHCI to ATA in the BIOS, and that allowed me to install XP! :P I then simply downloaded and installed the Intel Matrix Storage Manager for XP, which allowed me to keep always at AHCI mode! 

Cheers.

-Jam man

:guitar:

---

### Post by meindian523 on 2009-01-08
Well,shouldn't this be in Tutorials and Tips?

---

### Post by subzero.amir on 2009-01-08
> **Liviu-Theodor said:**
> Maybe you will have a case where somebody wants to install Windows, but already have Ubuntu (or any other distribution of Linux). Maybe you want to keep also Linux, but do not want to erase it, and reinstall it after Windows.

These are the steps:

1. First, use gPartEd to make room for Windows partitions. You can also format them under Linux. Sometimes it is necessary to move the swap partition. Just be sure to not format the Linux partitions.

2. Probably you will have at least one partition that changed its UUID. To solve this, you must run in a terminal:
```
blkid
sudo cp /etc/fstab /etc/fstab.backup
gksudo gedit /etc/fstab
```
At the last command use the new values found with the first command.

3. Now install normally Windows on the new partition(s), formatted with FAT32 or NTFS. After doing this, GRUB will be erased by the Windows bootloader.

4. Using a Ubuntu live-cd, use the option [FONT="Courier New"]System->Administration->Restore GRUB[/FONT]. After doing this, you will not see Windows at the GRUB bootloader.

5. Now edit the file [FONT="Courier New"]/boot/grub/menu.lst[/FONT] (maybe you need superuser rights to do that). Append the following lines at its end:
```
# This entry added for a non-linux OS on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
chainloader	+1
```
Or change accordingly if you have another version of Windows, and/or another partition configuration.

6. Restart and enjoy either Linux or Windows.
Why install windows? I just switched from windows.

---

### Post by Liviu-Theodor on 2009-01-08
> Maybe you will have a case where somebody wants to install Windows, but already have Ubuntu (or any other distribution of Linux). Maybe you want to keep also Linux, but do not want to erase it, and reinstall it after Windows.
> **subzero.amir said:**
> Why install windows? I just switched from windows.

Maybe you have a friend who buyed a new computer with Ubuntu, but is too accustomized (is this the word?) with Windows, and asks you to install Windows instead, but you install Windows along Ubuntu...

---

### Post by Jammanuser on 2009-01-08
> **meindian523 said:**
> Well,shouldn't this be in Tutorials and Tips?

Yes, it should...as should **mine**! :) I wrote a tutorial on multi-booting as well, and I'm **still** trying to get it posted in the Tutorials and Tips section of the forums, but it appears as if everyone has forgotten...:(

[http://ubuntuforums.org/showthread.php?t=1024929](http://ubuntuforums.org/showthread.php?t=1024929)

-Jam man

:guitar:

---

