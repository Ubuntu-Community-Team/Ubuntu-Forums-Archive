---
title: "[SOLVED] Hdd not getting detected in ubuntu"
date: 2008-02-17
forum: Hardware &amp; Laptops
---

### Post by chavanak on 2008-02-17
I have two hp dv6602au bought on the same day!!! I have created identical partitions in both. But in one machine gutsy is not able to detect the hdd!! Am using the alternate cd as i have a Broadcom wireless and gutsy has issues with it. In the system which has gutsy, I came to know that the Hdd in the system is 
WDC WD1600BEVS-60RST0. The reason i created a new thread is because in one system with the same configuration am able to install gutsy but not in the other. Can someone please help me? Is there something wrong am doing.... I have been using ubuntu from nearly 2 years. But i have not suffered anything like this.

---

### Post by chavanak on 2008-02-17
bump

---

### Post by Zeroangel on 2008-02-17
Not sure if you mean visible as a mountable partition on the desktop. 

Or detected as a partition in gedit (and thus visible to the system).

First I would try opening the System -> Administration -> GNOME Partition Editor (gparted), and see if any other drives but your primary are selectable. 

If that doesnt do, then open the command line and type
```
mount | grep "on / "
```
This will display which hard drive you're booting from. Of the things you'll want to note is if it says "hda" or "sda". HD are IDE drives and SD are SATA drives. If your "/" (root) partition is located on hda whatever, then your second hard drive is probably located on hdb. Likewise if your root partition is located on sda something then your second HD is probably located on sdb. 

So open the command line and type
```
ls /dev/hdb*
```or```
ls /dev/sdb*
```
depending on whether your drives are SATA or IDE. If your system can see them, good. If it can't then double-check to make sure that the drives physically are connected properly (loose cables do happen sometimes)

---

### Post by Zeroangel on 2008-02-17
The previous post gave you the means to detect the drives, but if you want the drives to be accessable as folders within ubuntu (aka: mounted) then you'll need to edit your fstab file.

There are lots of tutorials out there to do that.

---

### Post by chavanak on 2008-02-17
Oh am sorry for not being clear!!! My hdd is not detected during install. Ubuntu says it cant find the drivers for my hdd. But in the other system (identical twin). It has no issues. So no question of entering gnome at all or even using the live cd as i have a broadcom wireless.

Now what next????

---

### Post by Zeroangel on 2008-02-17
Wow, thats extremely strange. The places i might look for the answer are the BIOS settings (check to make sure they're OK), the bootsector or MBR (make sure its not corrupt), or otherwise check it with the fully working system to make sure that its OK, using a utility like fdisk .

I can't be more helpful than that.

---

### Post by IcarusR on 2008-02-17
Hi,
 does the bios 'see' the drive ? If not then nothing else will. At boot do you see the drive listed.
If not possibly the cables are not connected to the drive, open the case & check, if they are remove them & refit them, then try again.

Icarus

---

### Post by chavanak on 2008-02-17
You know guys... This is exactly what is making me cry :(  Vista came pre-installed and is working fine!!! Xp is able to detect the hdd. Only Gutsy is a big ache. BIOS is detecting the drive and i don't have much options :( Has anyone got this laptop and could any error in the mbr cause this problem??? If so how to correct it???

---

### Post by Zeroangel on 2008-02-17
If it's a drive utilizing the NTFS filesystem, then gutsy *might* take issues with it because the NTFS driver needs to be installed. Make sure that the packaged named "ntfs-3g" is installed on Ubuntu. This package gives NTFS read/write capability.

If you can at least find out the /dev/whatever file of the drive then you may be able to try mounting it manually. List any errors that come out, because sometimes Ubuntu will not mount NTFS drives properly if the drive is 'flagged' as needing a check. 

Failing that, you should know that Vista rewrites the MBR upon every reboot. This could cause problems on an Ubuntu installation because it might replace GRUB. I suggest you look into this if nothing else works.

In the future, if you need a filesystem which is visible to both Windows and Ubuntu without problems, I suggest you go with Fat32 for any "shared data" partitions (use NTFS for the windows OS partition, and Ext3 for the Linux OS partition), simply because NTFS and Ext3 both have journaling to prevent dataloss and fragmentation whereas Fat32 has great cross-compatability. Sure the Ext3 can be writable from Windows with a special driver (fs-driver.org) and NTFS can be writable to Linux with ntfs-3g -- but these filesystem can cause headaches for other OS since they are designed for their host OS's.

---

### Post by chavanak on 2008-02-17
but what about my other system??? its working fine!!!! If there is a problem withh mbr how to rectify it???

---

### Post by Zeroangel on 2008-02-17
I've given you some clues on where to start to look. I suggest you learn how to master 'search', if you get no further responses.

---

### Post by chavanak on 2008-02-18
Thanks for the reply zeroangel... I guess i will completely format my hdd and try once more....
Btw between the two systems, in which ubuntu is installed and the other with this hdd problem the only difference is that i formatted the drive completelyfor the one which has ubuntu now. So thats the final resort but its very painful job :(

---

### Post by IcarusR on 2008-02-27
Hi

Here is a link to a similar problem on another board...

[http://forum.doityourself.com/showthread.php?t=128821]("http://forum.doityourself.com/showthread.php?t=128821")

I believe that in order to dual boot linux & Windows you have to load grub first, this will give you a boot menu with options of Windows & Ubuntu.
 So the advise given in the link makes sens & is worth a try.

---

### Post by david lean on 2008-02-28
I ran into a similar problem, and a couple of possible solutions.   My problem was with an ancient e-machines desktop that I was trying to outfit with xubuntu - failed to detect disk drives and asked for disk drivers.  Similar thing happened when I tried to install fluxbuntu - both gutsy

As the mobo recognized the IDE drives on boot-up, I was convinced this was an OS issue.  So, my problem-solving hypothesis was that perhaps ubuntu would welcome the HDD if it was formatted as a linux ext2 or ext3 drive.  My goal then was to format the drive using any linux distro that recognized the hard drive.  I achieved success with the Damn Small Linux (DSL) distro.  I think Puppy linux and the G Parted live CD may also work.  I tried the above distros because they are known to work with old hardware.

Once the drive was formatted (after a hard-drive install of DSL) as ext2, I tried a fresh install with fluxbuntu, and this time it worked.  

As i am not very techie - I don't know why this happened.  But hey, it should be worth a shot.  All the best-

---

