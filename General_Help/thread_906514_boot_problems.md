---
title: "boot problems"
date: 2008-08-31
forum: General Help
---

### Post by nbirkett on 2008-08-31
I have an HP AMD duo core computer with two 250GB drives and 1 GB RAM which I have been using as a base to learn about Ubuntu. ihave worked with Solaris for many years and have a good comfort level with basic UNIX admin - I wanted to see if Ubuntu might be useful on my home computer.  Initially, the computer came with XP Media Centre Edition.  I wiped the disc, partitioned it into two 120GB sections and installed Ubuntu on the first partition.  I then installed a clean copy of XP (not MCE) onto the second partition with a dual boot option.  Everything worked fine for a few months.

Today, I decided to remove Ubuntu to give my system XP drive more space.  I used the disc management software in XP to delete the Ubuntu partition.  Things were fine until I tried to re-boot my XP - it will not re-boot.  I have tried repairing from my XP disc, re-installing the MBR, re-installing GRUB and nothing works.  I also ran a whole bunch of partition and repair utilities with no success.  If I boot Knoppix from a CD, the XP partition and files are still there.  However, if I boot from XP installed on the second disc, that OS fails to recognize the other drive.

I know that I messed up :(  Any help in how to recover would be greatly appreciated.

---

### Post by Sycron on 2008-08-31
Try [Super GRUB disk]("http://supergrub.forjamari.linex.org/").
Also you may give a try to XP instalation CD , boot it in Recovery Console and type **fixmbr** and **fixboot**.

---

### Post by nbirkett on 2008-08-31
I tried both of these approaches and they didn't work.

---

### Post by Sycron on 2008-08-31
In my opinion you screwed something, and one of those two methods should just work. DO you have important data on HDD ? You may try a FULL wipe out by reinstalling your windows...

---

### Post by caljohnsmith on 2008-08-31
> **nbirkett said:**
> I have an HP AMD duo core computer with two 250GB drives and 1 GB RAM which I have been using as a base to learn about Ubuntu. ihave worked with Solaris for many years and have a good comfort level with basic UNIX admin - I wanted to see if Ubuntu might be useful on my home computer.  Initially, the computer came with XP Media Centre Edition.  I wiped the disc, partitioned it into two 120GB sections and installed Ubuntu on the first partition.  I then installed a clean copy of XP (not MCE) onto the second partition with a dual boot option.  Everything worked fine for a few months.

Today, I decided to remove Ubuntu to give my system XP drive more space.  I used the disc management software in XP to delete the Ubuntu partition.  Things were fine until I tried to re-boot my XP - it will not re-boot.  I have tried repairing from my XP disc, re-installing the MBR, re-installing GRUB and nothing works.  I also ran a whole bunch of partition and repair utilities with no success.  If I boot Knoppix from a CD, the XP partition and files are still there.  However, if I boot from XP installed on the second disc, that OS fails to recognize the other drive.

I know that I messed up :(  Any help in how to recover would be greatly appreciated.
So you said you reinstalled the MBR, does that mean you ran "fixmbr" from the Windows Install CD? Also, to fix the boot sector of the Windows partition itself, you can use "fixboot". How about booting the Ubuntu Live CD, open a terminal, and post the output of:
```
sudo fdisk -lu
```
Also, if you can give more details about what happens on start up when it doesn't work, that would greatly help.

---

### Post by nbirkett on 2008-08-31
> **caljohnsmith said:**
> So you said you reinstalled the MBR, does that mean you ran "fixmbr" from the Windows Install CD? Also, to fix the boot sector of the Windows partition itself, you can use "fixboot". How about booting the Ubuntu Live CD, open a terminal, and post the output of:
```
sudo fdisk -lu
```
Also, if you can give more details about what happens on start up when it doesn't work, that would greatly help.
1) Yes, I ran 'fixmbr' and 'fixboot'.

2) I tried the code you suggested using Knoppix (hope that is OK) and got a 'can not scan disk' error.  However, the Windows partition is mounted as 'sda2' and all of the files can be accessed.

3) THe system fails before I see any Windows screens.  I immediately get an error screen which complains about a missing or corrupt file:

<windows root>\system32\hal.dll

---

### Post by caljohnsmith on 2008-08-31
> **nbirkett said:**
> 1) Yes, I ran 'fixmbr' and 'fixboot'.

2) I tried the code you suggested using Knoppix (hope that is OK) and got a 'can not scan disk' error.  However, the Windows partition is mounted as 'sda2' and all of the files can be accessed.

3) THe system fails before I see any Windows screens.  I immediately get an error screen which complains about a missing or corrupt file:

<windows root>\system32\hal.dll
Can you log in as root in knoppix using maybe either of the following:
```
su -
sudo -i

```
Once you are root, then do:
```
fdisk -lu
```
Also, run "testdisk" as root, and go through the prompts until it asks you to "analyze" your HDD, and then post the results of that too. And since you can still access windows, first check if you even have a hal.dll file in that folder you gave, and also post the contents of the "boot.ini" file which is in the Windows root directory. 

Lastly, boot your Windows Install CD and run a "chkdsk /r" from the recovery console. That might help a lot at this point, and let me know if it finds any errors.

---

### Post by nbirkett on 2008-08-31
I'll give it a try and report back.  But, when I remove my second drive from the system, the Windows CD boot doesn't seem to find the file system so that suggestion may not work.  I will look for it under Knoppix.  BTW, I'm using that version of Linux because I have the CD image to-hand from another problem I had to fix.  HOpe that doesn't cause problems in an Ubuntu forum :)

---

### Post by nbirkett on 2008-08-31
OK - some progress.  I was able to mount the Windows partition in Linux.  Looking at the file system confirmed that all of the files were present.  Next, I examined 'boot.ini'.  It was referencing partition(1).  I modified this to 'partition(2)'.  Now, when I boot, I get into the full Windows boot sequence - the windows screen appears and the timing bar flashes across the screen.  However, after about 5 seconds, the screen flashes an error message (far to fast for me to read) and the re-boots.  THis continues indefinitely.  If I try a 'safe' boot, I get long list of programmes which are loaded and then it re-boots.

So, looks like I didn't completely mess-up the Windows partition but did cause some damage.  I know this isn't a Linux issue anymore but does the new information suggest any 'next steps' I could take?

Thanks.

---

### Post by caljohnsmith on 2008-08-31
I would definitely run "chkdsk /r" on your windows partition just to make sure there aren't any basic disk/file system problems. If that doesn't help your booting problems, you are probably stuck with doing a "windows repair" from the install CD. 

What is your partition structure? Is Windows really on the second partition?

---

### Post by nbirkett on 2008-08-31
I can't get my disc to be recognized under any Windows OS which means that I can't run 'chkdsk' :(  Even the 'recovery' option after booting from a Windows CD won't find the disc.  But, under Ubuntu, the whole disc is there and usable.

I did download the new Ubuntu disc image (I had been using version 7) and explored things using Live CD.  The 'sfdisk' command finds four partitions on the disc: #1 is my Ubuntu partition which I tired to get rid of; #2 is Windows; #3 is swap and #4 is Windows recovery.  The programme also complains that it tried to seek an invalid location.  When I look at the disc using the graphics Partition manager, it reports that there are no partitions on the disc at all.

I can mount both the 'deleted' Ubuntu partition and the Windows partition and have full access to all of the file in the system.  I ran 'ntfsfix' but that didn't help.  Everytime I boot to Windows, it just does a re-boot without ever bringing up a usable screen (and without displaying the error message for a long enough time that I can read it).

---

### Post by caljohnsmith on 2008-08-31
Sounds like your HDD's partition table could be corrupt at this point. From your Ubuntu Live CD, try:
```
sudo testdisk
```
Go through the prompts until you get to the part where you can choose "analyze", and see what partitions testdisk shows, and especially if it gives any errors at that point. Please post back the results, and if you wouldn't mind, it would be great if you would also post the output of:
```
sudo fdisk -lu
```

---

### Post by nbirkett on 2008-08-31
'fdisk' fails with an error message about being unable to seek on /dev/sda (I have SATA drives which are mounting as 'sda' rather 'hda' for some reason).

'testdisk' wasn't found by Ubuntu when I tried to run it  (command not found) and it didn't show when I ran a 'man' command.  Is there somewhere else I should be looking?

---

### Post by caljohnsmith on 2008-08-31
You'll need to install that testdisk package while you're in the Live CD; I don't know if it is on the Live CD or not, so you may need internet access. Just install it with:
```
sudo apt-get install testdisk
```
If fdisk is giving you that error you mentioned, I think the chances are extremely high at this point you have a corrupt HDD partition table. Testdisk will soon tell you if that is true, and you can use testdisk to correct your partitioning. 

P.S. I didn't mention it before because I figured it kind of "goes without saying", but I hope you have made a backup of everything important in Windows at this point since you can still mount it. :)

---

### Post by nbirkett on 2008-08-31
OK, I got testdisk installed.  Interesting information.  I can't copy it (or type every last thing) but her is the essence:

250GB/232GiB/    CHS: 30401/255/63

1  P  FAT16   > 32M
1  P  FAT16   > 32M
2  *  HFPS - NTFS
3  E  Extended         29699/??/??   30400/??/??
4  P  Linux swap       30050/??/??   30400/??/??
   X  Extended        114637/227/42  291321/217/7

The physical locations for 1 and 2 were OK.  Clearly, there is a problem with partition 3 and 4.  Also, the 'X' partition makes no sense: it is pointed to cylinder locations over 110000 while the disc only goes to 30,401.  PLus, why does partition 1 get listed twice?

I went onto the next screen and the programme gave the following partitions:

*  LINUX        0/1/1   15257/??/??
P  HPFS-NTFS  ??/??/??  ??/??/??
L  Linux Swap
L  Linus swap

I've stopped here.  Am I correct that the next step would be for testdisk to write out a new partition table/label?  If so, should I change the 'P' to '*' for the Windows partition?

I have good back-ups of the key audio/video files from this computer (on an external USB and a second hard drive).  I am taking another one just in case (Ubuntu Live CD is letting me do this).  The main thing I would lose if I re-format the disc is a lot of time installing and setting up programme (something which you can't back-up).

Once my data back-up is done, should I should keep going with testdisk?

---

### Post by nbirkett on 2008-09-01
That fixed it!

When I got up this morning, I decided that I couldn't make things any worse :) so I went ahead and had Testdisk re-label my disc drive (after first changing the primary boot partition to my Windows partition).  I re-booted and Windows immediately went into running 'chkdsk'.  Once that finished (having found no errors), I re-booted again and the computer went directly into my Windows system.  And there were no errors.  To confirm things, I re-booted in Ubuntu and ran 'fdisk -lu'.  This time, it gave me all the partition information, with no error messages.  I even bet that I could re-boot my Ubuntu system, if I could figure how to get my system to boot from the first partition.

Many, many thanks (I'd hit the 'thanks' button a dozen times if the system would let me).  I really appreciate your help and your willingness to 'stick with me' through this.  One lesson learned by me - don't use Windows disk manager to handle disk partitions.

Have a great day.

---

### Post by caljohnsmith on 2008-09-01
> **nbirkett said:**
> That fixed it!

When I got up this morning, I decided that I couldn't make things any worse :) so I went ahead and had Testdisk re-label my disc drive (after first changing the primary boot partition to my Windows partition).  I re-booted and Windows immediately went into running 'chkdsk'.  Once that finished (having found no errors), I re-booted again and the computer went directly into my Windows system.  And there were no errors.  To confirm things, I re-booted in Ubuntu and ran 'fdisk -lu'.  This time, it gave me all the partition information, with no error messages.  I even bet that I could re-boot my Ubuntu system, if I could figure how to get my system to boot from the first partition.

Many, many thanks (I'd hit the 'thanks' button a dozen times if the system would let me).  I really appreciate your help and your willingness to 'stick with me' through this.  One lesson learned by me - don't use Windows disk manager to handle disk partitions.

Have a great day.
I'm so glad testdisk helped you sort out the problem. :) I don't want to believe that Windows disk manager could screw things up that bad, but it some how did in your case. At least everything seems to be OK now.

---

