---
title: "Windwos Vista Recovery!!Emergency!!!"
date: 2009-01-13
forum: Installation &amp; Upgrades
---

### Post by huruixd on 2009-01-13
Hello everybody,

I installed Ubuntu 8.10 on a Thinkpad T400 where Windows Vista was preinstalled. During the installation, Ubuntu can't recognize the disk space where Vista located, but a whole free space instead. So I allocated 60GB of high address disk (160GB in total) for Ubuntu to protect vista. 

However, once the installation is done, I found out I can no longer login vista anymore. There are opitions in grub only for Ubuntu. Furthermore, the Thinkvantage button doestn't work either. 

My question is:

1. How could I enable the thinkvantage button again to recover Windows vista?

I appreciate any step by step guide or suggestions. Thank you so much.[COLOR="Red"][/COLOR]

---

### Post by sn8ball on 2009-01-13
Hey, yea the same thing happened to me the other day. I put in my recovery disc and used the repair option. Which resets the Master boot record. Try that then you should be able to login to Vista but you might have to reload Ubuntu.

---

### Post by huruixd on 2009-01-14
But what about the Thinkvantage Button? Would it be enabled again if I recovery Windows Vista by using the recovery CD?

Does anybody know a link to download the recovery CD image? Thank you.

---

### Post by Mark Phelps on 2009-01-14
Generally speaking, recovery disks, especially if supplied with the PC or made from the PC, restore the machine to the state it was in when you unpacked it.  The means the entire drive will be wiped and reformatted and all files and accounts removed.  So, before you do that, be sure to back off any files you want to save to an external drive.

---

### Post by caljohnsmith on 2009-01-14
Does your computer actually have two 160 GB drives in a RAID array? If so, that would explain the problem. How about booting your Live CD (the Ubuntu install CD), open a terminal (Applications > Accessories > Terminal) and please post the output of:
```
sudo fdisk -lu
```
And we can work from there if you want.

---

### Post by huruixd on 2009-01-16
Hi, here is the ouput:

======================================================================

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x81bf5e5d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *   273506625   312576704    19535040   83  Linux
/dev/sda2       195382530   273506624    39062047+   5  Extended
/dev/sda5       195398595   203206184     3903795   82  Linux swap / Solaris
/dev/sda6       203206248   273506624    35150188+  83  Linux

Partition table entries are not in disk order

======================================================================


Thank you.

---

### Post by caljohnsmith on 2009-01-16
So are you sure that fdisk didn't show an sdb drive too? I just want to make sure, because that could greatly affect things. But according to the fdisk results, unfortunately your Vista partition no longer exists. But it does look promising, because there is a large ~104 GB chunk of unclaimed disk space at the beginning of your drive, so hopefully that is where Vista is hiding. In order to try and recover your Vista partition, how about first making sure the Ubuntu Universe repository is enabled in System > Admin > Software Sources, and then download and run testdisk with the following commands:
```
sudo apt-get install testdisk
sudo testdisk
```
Check to see which version of testdisk you are using when you start the program, because you will need at least version 6.9 or later; if you have an older version, let me know and I'll give you directions for how to download the latest version.

So after starting testdisk with the above command, choose "No Log", select HDD and "Proceed", "Intel", "Analyze", "Quick search", "Y" to search for Vista partitions, hit enter to continue, and select "Deeper Search" so it does a deeper search, which could take a while. Please post the output of the screen that has the deep search results. Also, use your up/down arrow keys to select each partition listed in the deep search results, and press "p" to get a directory listing; please let me know exactly which partitions give you a directory listing. And lastly, please post the output of:
```
sudo sfdisk -l
```
And we can work from there.

---

### Post by theozzlives on 2009-01-16
> **huruixd said:**
> Hello everybody,

I installed Ubuntu 8.10 on a Thinkpad T400 where Windows Vista was preinstalled. During the installation, Ubuntu can't recognize the disk space where Vista located, but a whole free space instead. So I allocated 60GB of high address disk (160GB in total) for Ubuntu to protect vista. 

However, once the installation is done, I found out I can no longer login vista anymore. There are opitions in grub only for Ubuntu. Furthermore, the Thinkvantage button doestn't work either. 

My question is:

1. How could I enable the thinkvantage button again to recover Windows vista?

I appreciate any step by step guide or suggestions. Thank you so much.[COLOR="Red"][/COLOR]

There might have been a recovery partition (that was couldve been erased during install) that caused your "thinkadvandage button" to work.

---

### Post by huruixd on 2009-01-16
Thanks. But before that, I am not able to access the internet due to disabled wireless. Could you please tell me how to enable the wireless? It doesn't work after the installation.

---

### Post by caljohnsmith on 2009-01-16
> **huruixd said:**
> Thanks. But before that, I am not able to access the internet due to disabled wireless. Could you please tell me how to enable the wireless? It doesn't work after the installation.
Can you access the internet from your Live CD? If so, you can do it from there. If not, I would suggest downloading the [testdisk package]("http://packages.ubuntu.com/intrepid/testdisk") from some other computer, transfer it to your Ubuntu desktop, and then you can do:
```
sudo dpkg -i ~/Desktop/testdisk*.deb
```
And that will install it.

---

### Post by huruixd on 2009-01-16
Hi, one error happened when I tried the code

======================================================

(Reading database ... 100040 files and directories currently installed.)
Preparing to replace testdisk 6.9-1.1 (using .../testdisk_6.9-1.1_i386.deb) ...
Unpacking replacement testdisk ...
dpkg: dependency problems prevent configuration of testdisk:
 testdisk depends on libntfs10 (>= 2.0.0); however:
  Package libntfs10 is not installed.
dpkg: error processing testdisk (--install):
 dependency problems - leaving unconfigured
Processing triggers for man-db ...
Errors were encountered while processing:
 testdisk


======================================================

---

### Post by caljohnsmith on 2009-01-16
OK, it looks like testdisk just needs the libntfs10 package, so how about downloading that from [here]("http://packages.ubuntu.com/intrepid/libntfs10"), transfer it to your Ubuntu desktop, and run the dpkg command on it to install it. After that try installing testdisk again.

---

### Post by huruixd on 2009-01-16
Here is the partitions:

===============================================
TestDisk 6.9, Data Recovery Utility, February 2008
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)

Disk /dev/sda - 160 GB / 149 GiB - CHS 19458 255 63
     Partition               Start        End    Size in sectors
D HPFS - NTFS              0  32 33   191  89 26    3072000 [O_SERVICEV003]
D HPFS - NTFS            191  89 27 12573  12 31  198911984 [LiNG]
D HPFS - NTFS          12573  45 17 15122 208 62   40960000 [Tools]
D HPFS - NTFS          15122 241 32 18182  66 60   49147904 [New Volume]
D HPFS - NTFS          18182  66 61 19457  21 20   20480000 [O_Lenovo]


Structure: Ok.  Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
Keys A: add partition, L: load backup, T: change type, P: list files,
     Enter: to continue
NTFS, 101 GB / 94 GiB
===============================================

My question is:
In which partition should I do the deeper search? The largest one or all of them? Thanks.

---

### Post by caljohnsmith on 2009-01-16
Let me ask again, because this is important: when you did the fdisk command from post #6, did fdisk show a sdb drive at all? Did it say anything about an invalid partition table if sdb was listed? When you ran testdisk, did it only give you the choice of one drive to check, or were there two drives listed? Something isn't quite right, because the testdisk results don't show any of your new linux partitions. Did you follow the directions exactly from post #7 to make sure you did the "Deeper Search"? Because the screen you posted could be the one you get after doing a "Quick Search". It should have taken awhile to do the deep search. Also, please post:
```
sudo sfdisk -l
```

---

### Post by huruixd on 2009-01-16
yes, after #sudo fdisk -lu, All I got is this:

=======================================
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x81bf5e5d

Device Boot Start End Blocks Id System
/dev/sda1 * 273506625 312576704 19535040 83 Linux
/dev/sda2 195382530 273506624 39062047+ 5 Extended
/dev/sda5 195398595 203206184 3903795 82 Linux swap / Solaris
/dev/sda6 203206248 273506624 35150188+ 83 Linux

Partition table entries are not in disk order
=======================================

I haven't finished the deeper search. The one I just posted is the result of quick search. I was just wondering which partition I should select to do the deeper search, because there are 5 options:

D HPFS - NTFS 0 32 33 191 89 26 3072000 [O_SERVICEV003]
D HPFS - NTFS 191 89 27 12573 12 31 198911984 [LiNG]
D HPFS - NTFS 12573 45 17 15122 208 62 40960000 [Tools]
D HPFS - NTFS 15122 241 32 18182 66 60 49147904 [New Volume]
D HPFS - NTFS 18182 66 61 19457 21 20 20480000 [O_Lenovo]

Should I choose the partition which has the highest possibility containing Vista, or I need to choose all of them and show the deeper search result respectively?

Here is the result of #sudo sfdisk -l:
===========================================
Disk /dev/sda: 19457 cylinders, 255 heads, 63 sectors/track
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1   *  17025   19456    2432   19535040   83  Linux
/dev/sda2      12162   17024    4863   39062047+   5  Extended
/dev/sda3          0       -       0          0    0  Empty
/dev/sda4          0       -       0          0    0  Empty
/dev/sda5      12163   12648     486    3903795   82  Linux swap / Solaris
/dev/sda6      12649+  17024    4376-  35150188+  83  Linux
===========================================

Thank you.

---

### Post by caljohnsmith on 2009-01-16
You don't need to select any partitions in the quick search screen, just press enter and on the next screen you can choose "Deeper Search". Once it finishes, be sure to let me know which partitions give a directory listing, because that will help determine which ones are recoverable.

---

### Post by huruixd on 2009-01-16
Here is the result of deeper search:

==============================================
   * HPFS - NTFS              0  32 33   191  89 26    3072000 [O_SERVICEV003]
Use Right arrow to change directory, c to copy, q to quit
Directory /

dr-xr-xr-x     0     0         0  5-Jan-2009 21:49 .
dr-xr-xr-x     0     0         0  5-Jan-2009 21:49 ..
dr-xr-xr-x     0     0         0  5-Jan-2009 21:50 Boot
-r--r--r--     0     0    333203  5-Jan-2009 21:50 bootmgr
-r--r--r--     0     0      8192  5-Jan-2009 21:50 BOOTSECT.BAK
dr-xr-xr-x     0     0         0  5-Jan-2009 22:11 INOV8LOG
-r--r--r--     0     0    180224  5-Jan-2009 22:53 LenovoSDrive.exe
dr-xr-xr-x     0     0         0  5-Jan-2009 22:11 MFGSTAT
dr-xr-xr-x     0     0         0  5-Jan-2009 22:10 preboot
-r--r--r--     0     0   169357742  5-Jan-2009 22:09 recov.wim
dr-xr-xr-x     0     0         0  5-Jan-2009 22:10 recovery
-r--r--r--     0     0     12390  5-Jan-2009 22:53 sdrive.ico
dr-xr-xr-x     0     0         0  5-Jan-2009 22:11 swwork
dr-xr-xr-x     0     0         0  5-Jan-2009 22:36 System Volume Information
dr-xr-xr-x     0     0         0  5-Jan-2009 23:03 tvtos
dr-xr-xr-x     0     0         0  5-Jan-2009 22:11 windows


==============================================

---

### Post by caljohnsmith on 2009-01-16
I think you might be misunderstanding; the "Deeper Search" should return a listing of partitions, not directories. What you show in your post is a directory listing of one of the partitions from the quick search it looks like. If you go back to the "quick search" results screen exactly like you posted in post #13, just press enter, and then in the next screen select "Deeper Search".

---

### Post by huruixd on 2009-01-16
Here is what I did, step by step:

Step 1: Choose Analyze:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=100074&stc=1&d=1232159513[/IMG]

Step 2: Choose Quick Search:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=100075&stc=1&d=1232159513[/IMG]

Step 3: I choose Yes:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=100076&stc=1&d=1232159513[/IMG]

Step 4: I need to choose one of these options to do a deeper search:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=100077&stc=1&d=1232159513[/IMG]

For example, if I choose the first one, I got this:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=100078&stc=1&d=1232160009[/IMG]
Then I can do the deeper search under the first option.

---

### Post by caljohnsmith on 2009-01-16
That's totally OK that it says no partitions selected for recovery, because the whole idea is to get past the quick search results and do the deeper search. It's the deeper search results that are the most accurate and useful, so in that last screen you show where it shows "deeper search", just select it and press enter.

---

### Post by huruixd on 2009-01-16
The first picture shows progress of deeper search:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=100082&stc=1&d=1232162679[/IMG]

Once the deeper search is done, I got this:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=100083&stc=1&d=1232162679[/IMG]

What should I do next? There are several operation options at the bottom the last picture. Thanks.

---

### Post by caljohnsmith on 2009-01-16
OK, use your up/down arrow keys to select each partition listed in the deep search results, and press "p" to get a directory listing; please let me know exactly which partitions give you a directory listing. Also, I have to go now and won't be around again until tomorrow morning (about ~10 hours from now), so we can pick up then if you are around.

---

### Post by huruixd on 2009-01-16
Hi, There are 21 partitions, Here are the snapshot of directory listing of each partition.

Listing 1:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=100085&stc=1&d=1232164040[/IMG]

Listing 2:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=100086&stc=1&d=1232164040[/IMG]

Listing 3:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=100087&stc=1&d=1232164040[/IMG]

Listing 4:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=100088&stc=1&d=1232164040[/IMG]

Listing 5:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=100089&stc=1&d=1232164040[/IMG]

---

### Post by huruixd on 2009-01-16
Listing 6:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=100090&stc=1&d=1232164289[/IMG]

Listing 7:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=100091&stc=1&d=1232164289[/IMG]

Listing 8:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=100092&stc=1&d=1232164289[/IMG]

Listing 9:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=100093&stc=1&d=1232164289[/IMG]

Listing 10:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=100094&stc=1&d=1232164289[/IMG]

---

### Post by huruixd on 2009-01-16
Listing 11:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=100095&stc=1&d=1232164485[/IMG]

Listing 12:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=100096&stc=1&d=1232164485[/IMG]

Listing 13:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=100097&stc=1&d=1232164485[/IMG]

Listing 14:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=100098&stc=1&d=1232164485[/IMG]

Listing 15:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=100099&stc=1&d=1232164485[/IMG]

---

### Post by huruixd on 2009-01-16
Listing 16:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=100100&stc=1&d=1232164614[/IMG]

Listing 17:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=100101&stc=1&d=1232164614[/IMG]

Listing 18:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=100102&stc=1&d=1232164614[/IMG]

Listing 19:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=100103&stc=1&d=1232164614[/IMG]

Listing 20:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=100104&stc=1&d=1232164614[/IMG]

---

### Post by huruixd on 2009-01-16
Listing 21:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=100105&stc=1&d=1232164744[/IMG]

---

### Post by huruixd on 2009-01-16
I am looking forward to seeing your reply. Thank you so much.

---

### Post by huruixd on 2009-01-17
Are you there, caljohnsmith?

---

### Post by caljohnsmith on 2009-01-17
Unfortunately it doesn't look especially promising; none of the partitions that give a directory listing show your main Vista install it looks like, although the Vista recovery partition seems to be intact. It appears that your main Vista install might be the "LiGN" partition, but that partition is now corrupt and can't be listed. Also, you have a "Happiness" partition that looks like it has your personal files, but the Linux root partition starts at a point inside the Happiness partition, so probably not all the files in the Happiness partition may be recoverable. Did you have important files in your main Vista partition that you want to try and recover? And do you want to recover files from the Happiness partition? We could try to do that, but I don't know how successful we will be (if at all). Let me know what you would like to do.

---

### Post by huruixd on 2009-01-17
I don't have important files on main vista partition. My goal is to:

1: Recover my laptop back to the factory model, which is Vista installed and Thinkvantage works.

2. Recover the files in Happiness paritiion as much as possilbe.

Thank you.

---

### Post by caljohnsmith on 2009-01-17
OK, how about selecting each of the partitions in the deep search results, and using the right/left arrow keys, mark all of them as deleted "D" except the 0_SERVICEV003 and the Happiness partition; mark those two partitions as "P" instead. Press enter to get the next screen, and then write the new partition table to the drive. Next reboot your Live CD, and post the new output of:
```
sudo fdisk -lu
sudo blkid -c /dev/null
```
And we can go from there.

---

### Post by huruixd on 2009-01-17
Execuse me, what does reboot live CD mean? I wrote the new partition table to the drive. But once I restarted, it says:

========================================== 
Loading GRUB, please wait. 
Error 17
==========================================

So I reboot my labtop with my install CD. I choose the first option: Try ubuntu without any change to your system.

Then I enter the code:
===========================
sudo fdisk -lu
sudo blkid -c /dev/null
============================

I got this:
===============================================================
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x81bf5e5d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048     3074047     1536000    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2       249661503   312575759    31457128+   7  HPFS/NTFS



ubuntu@ubuntu:~$ sudo blkid -c /dev/null
/dev/sda1: UUID="DCD073AAD0738A12" LABEL="O_SERVICEV003" TYPE="ntfs" 
/dev/sda2: UUID="9BA687EFFB7BA830" LABEL="Happiness" TYPE="ntfs" 
/dev/loop0: TYPE="squashfs" 
 

===============================================================

---

### Post by caljohnsmith on 2009-01-17
The Live CD is just another name for the Ubuntu install CD. How about next trying the following:
```
sudo mkdir /media/sda1 /media/sda2
sudo mount /dev/sda1 /media/sda1 && ls -l /media/sda1
sudo mount /dev/sda2 /media/sda2 && ls -l /media/sda2
nautilus /media &
```
The last command will pull up a file browser where you should be able to access the sda1 and sda2 partitions if none of the commands before return an error. Please post the output of all the commands and we can work from there.

---

### Post by huruixd on 2009-01-17
Yes, there is no error happens.

[COLOR="Red"]sudo mkdir /media/sda1 /media/sda2
sudo mount /dev/sda1 /media/sda1 && ls -l /media/sda1
sudo mount /dev/sda2 /media/sda2 && ls -l /media/sda2[/COLOR]
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=100183&stc=1&d=1232224487[/IMG]

[COLOR="Red"]nautilus /media &[/COLOR]
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=100184&stc=1&d=1232224487[/IMG]

---

### Post by caljohnsmith on 2009-01-17
It looks like you have a small typo with the second mount command you ran, so try doing:
```
sudo umount /media/sda2
sudo mount /dev/[COLOR="Blue"]sda2[/COLOR] /media/sda2 && ls -l /media/sda2
```
Notice it should be "sda2" and not sda1 above.

---

### Post by huruixd on 2009-01-17
Oh, sorry for that.

Here is the change:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=100186&stc=1&d=1232225682[/IMG]

So, am I able to copy my personaly files to an external hard drive or it still needs further process? Thank you.

---

### Post by caljohnsmith on 2009-01-17
Yes, it looks like you should be able to recover at least some of your personal files, and if your lucky, maybe most or all of them. While sda2 is still mounted on /media/sda2, try:
```
nautilus /media/sda2 &
```
And then you can copy/paste your files to another drive. Good luck and let me know how it goes.

---

### Post by huruixd on 2009-01-17
Thank you so much, I have successively copied those files to an external hard drive.

I notice that there is a recovery folder in sda1, I am wondering if I am able to recover my laptop back to factory mode, where vista is installed and thinkvantage button works.

---

### Post by caljohnsmith on 2009-01-17
> **huruixd said:**
> 
I notice that there is a recovery folder in sda1, I am wondering if I am able to recover my laptop back to factory mode, where vista is installed and thinkvantage button works.
Yes, that was the idea of recovering that recovery partition, we can try to boot it to see if it might reinstall Vista for you. Next, how about doing the following:
```
sudo sfdisk -A1 /dev/sda
sudo lilo -M  /dev/sda mbr
```
If the second command returns an error of "command not found", then do:
```
sudo apt-get install lilo
```
And try the second lilo command above again. If both commands complete successfully, reboot your computer and let me know what happens.

---

### Post by huruixd on 2009-01-17
Yes, the first two commands worked successfully.

When I restarted the laptop, there were two booting options showed up. One is for Vista, and anther is for ubuntu. I chose Vista, and it is attempting to repair vista.

I will let you the result.

---

### Post by huruixd on 2009-01-17
"Fan Error" shows up right after I push the power button.Then, it power off. I think it is a hardware problem. So, right now, I can't turn on my computer.

---

### Post by huruixd on 2009-01-17
Vista attempted to repair the system automatically. But something went wrong at this step. I referred to the repair details, it says:

=======================================
Boot configuration is corrupt.

Repair action: Partition table repair
Result: Failed. Error Code=0x490
Time taken = 8611ms
=======================================

Waiting for solution.

---

### Post by caljohnsmith on 2009-01-17
It sounds like you may have some hardware problems, and if booting the recovery partition doesn't work to reinstall Vista, probably your only other choice is to get a Vista Install CD and use that. Good luck and let me know how it goes.

---

