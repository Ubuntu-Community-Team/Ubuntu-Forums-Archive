---
title: "Ext4 and hard drive failure(s)"
date: 2009-11-25
forum: Hardware
---

### Post by 73ckn797 on 2009-11-25
I am really beginning to think that ext4 is causing hard drives to corrupt. I have had 4 hard drives this year fail due to bad sectors and all of them were during use of ext4. The hard drives were all purchased new in the last 1 1/2 years. 3 drives are 160GiB Western Digital and one Maxtor 160GiB.

When I format the drives using gparted the bad sectors remain. On one drive that reported bad sectors I used the Windows formatting and it fixed the drive. I notice that Windows takes 30 minutes or longer to format a 160GiB drive. Ubuntu/gparted only takes several minutes. Is the gparted formatting really not a thorough format and that is why it is quicker, and hence, really not a complete surface formatting?

OR, am I just encountering a bad run of hard drives? I have 3 250Gib drives that have been running flawlessly for over 3-4 years on other computers. None, however, use ext4. One has ext3 and the others are Windows systems. 

I have an 80Gib, 40Gib, 20Gib, 15Gib, 10Gib, 6.4Gib and a 2.1Gib drive that are from 15 to 8 years old and have never had problems. I currently do not use those but they worked fine upon removal when upgrading to larger drives. Those have never had ext4 installed.

I am about to reboot into the LiveCD and see what the disk utility reports on one 160GiB drive after formatting from Windows.

---

### Post by l0r3zz on 2009-11-25
Well I installed 9.10 on a brand new 320GB drive, has been running fine, then today I just took a massive upgrade which included a kernel upgrade. Everything went fine, I rebooted, and was still using the system.  I went out for a few hours, can back, the screen was blank and didn't wake up which was odd.  I hard rebooted by turning off the power, the system and monitor came back on but the system won't boot.  The interesting thing is that I my /boot partition is esx2 and that is fine, but when I boot into the Live CD, both my / and my /home partitions which are ext4 are hosed, as in unmountable,  interesting.  Anybody know if they are repairable? It's only been a couple of days but there is a subversion repository on there that I'd like to try and save. what is the equivalent of fsck for esx4 ?

---

### Post by davidg25 on 2009-11-25
I've had a little suspicion myself, since I just had one get bombed out during an install test of Ubuntu and Ubuntu Studio.   It was previously NTFS with  XP and has been flawless for 2 years.  After some errant install with MythTV the drive tanked.  
 
My 250gb was stuck with bad sectors and 'shortened' considerably.  I can't find any utility to fix it, either.  I finally replaced it a week ago.
 
Maybe it was the luck of the draw, but I'm still looking it over.  I'm about to run another install and see if the disk looks ok at this point.  Hopefully this time it was just an update that bummed out things .........

---

### Post by 73ckn797 on 2009-11-25
I have been running Ubuntu ext3 on my laptop for a year with no problems at all, currently 9.10 32 bit. The laptop is dual boot with XP. I will probably wipe the Windows drive (sda) on my desktop and install Ubuntu 9.10 64bit with ext3. I still have Windows XP on the laptop for the needs I have for that OS. I really, based upon my experience, as mentioned, cannot trust ext4 any longer. It is getting expensive, $200 in the trash so far.

---

### Post by 73ckn797 on 2009-11-25
Previously, after running "chkdsk" in Windows XP, the drive showed no bad sectors but did when running "disk utility" from the LiveCD.

I just completed running "KillDisk" from the "Ultimate Boot CD" (UBC) and now when booting from the Ubuntu 9.10 64bit LiveCD and running Disk Utility, the drive shows as being completely healthy.

I was reading another post about a possible bug with the Disk Utility. I have not checked Launch Pad for bug reports at this time.

UPDATE: 9.10 ext3 64bit installed just fine. Drive still shows healthy. The other drives never would even mount on BIOS boot and were making noise. This drive had no noise or problem being seen in BIOS.

---

### Post by 73ckn797 on 2009-11-27
WELL, the last of the 4 hard drives has failed completely. It also had been running ext4. In previous post here, it formatted fine in Windows and no longer reported any bad sectors. Today it completely died. I had to boot with Win XP disk to restore the MBR in order to have a working computer. I will buy another hard drive and install Ubuntu 9.10 on it but with ext3.

Is this an issue with using ext4? So far, my experience says it is. I know others on the forums have stated they have had no problems. I wish that were the case with me. Prior to the latest drive failure I was running 9.04 64bit ext3 and then 9.10 64bit ext4. The troubles began with ext4.

Any thoughts?

---

### Post by PRC09 on 2009-11-27
Not sure if this is related to the errors but....

[https://bugs.launchpad.net/ubuntu/+source/libatasmart/+bug/438136](https://bugs.launchpad.net/ubuntu/+source/libatasmart/+bug/438136)

---

### Post by 73ckn797 on 2009-11-27
> **PRC09 said:**
> Not sure if this is related to the errors but....

[https://bugs.launchpad.net/ubuntu/+source/libatasmart/+bug/438136](https://bugs.launchpad.net/ubuntu/+source/libatasmart/+bug/438136)


I believe the problem is with the ext4 format. The drive is completely dead and is not even recognized by the BIOS on boot up.

---

### Post by Blue Beard on 2009-11-29
There was a known data-loss bug found in Ext4 that was fixed in Linux 2.6.32-rc6 (see article at [http://www.phoronix.com/scan.php?page=news_item&px=NzY2OQ](http://www.phoronix.com/scan.php?page=news_item&px=NzY2OQ))

Currently my system disk is unmountable like many have reported.  I was able to copy my user area with 2 errors (16.9GB) mounting the disk on a 9.10 system.

---

### Post by l0r3zz on 2009-11-29
Well, I had an RMA and had packaged the disk all ready to send it back, then I decided to try to format it on a Windows system, so I opened the box, unwrapped the drive, put it in a USB case and connected it to my Laptop, I started up a Windows XP VM under VMware Workstation (running on 9.04) and was able to successfully format it under windows, so that it says that it is now a Healthy NTFS volume, It still doesn't automount under Linux so now I'm running 

[FONT="Courier New"]smartctl -a -t long -d sat /dev/sdc [/FONT]

And we'll see in a couple of hours.

---

### Post by l0r3zz on 2009-11-29
Finished the smartctl test, the drive came up fine.
Now when I run gpartd it formats just fine as an ext4 FS.
Hmmm, something smells fishy with ext4 IMHO.

I guess I'm not going to RMA this drive, but I've got a Hitachi 500GB 7200 RPM en route so I will install 9.10 on that BUT you can bet I will not be partitioning with ext4 :popcorn:

---

### Post by 73ckn797 on 2009-11-29
I took a 250GiB ATA drive from another computer here. It is over 2 years old and was running Windows XP & Vista by my son and he was playing games heavily on it.I installed  Ubuntu 64 bit ext3 and it runs flawless and fast.

I will consider this as solved with the solution being:
_***Replacing the hard drive and not formatting to ext4.***_

---

