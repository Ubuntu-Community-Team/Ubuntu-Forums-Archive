---
title: "Help! fsck failed error..."
date: 2008-07-25
forum: General Help
---

### Post by c_martini on 2008-07-25
My partner rebooted my pc this morning after an unspecified problem (ktorrent hanging i think). I wasn't awake yet so did not see exactly what was happening before the reboot. Anyhow, upon rebooting, it did not make it to x or kdm or the desktop and this is what was on screen when I saw it:

```
* Setting kernel variables... [ok]
* Activating swap [ok]
* Checking root file system...
1232
fsck 1.40.8 (13-Mar-2008)
/dev/sbd2 contains a file system with errors, check forced.
Checking drive /dev/sbd2: 0% (stage 1/5, 2/195)
Checking drive /dev/sbd2: 1% (stage 1/5, 3/195)
Checking drive /dev/sbd2: 1% (stage 1/5, 4/195)
Checking drive /dev/sbd2: 1% (stage 1/5, 5/195)
Checking drive /dev/sbd2: 5% (stage 1/5, 14/195)
Checking drive /dev/sbd2: 8% (stage 1/5, 23/195)
Checking drive /dev/sbd2: 11% (stage 1/5, 32/195)
/dev/sbd2: Inodes that were part of a corrupted orphan linked list found.

/dev/sbd2: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
             (i.e., without -a or -p options)
fsck died with exit status 4
Checking drive /dev/sbd2: 12% (stage 1/5, 35/195)
                                                                                                                 [fail]
* An automatic file system check (fsck) of the root file system failed.
A manual fsck must be performed, then the system restarted.
The fsck should be performed in maintenance mode with the
root file system mounted in read-only mode.
* The root filesystem is currently mounted in read-only mode.
A maintenance shell will now be started.
After performing system maintenance, press CONTROL-D
to terminate the maintenance shell and restart the system.
bash: no job control in this shell
bash: groups: command not found
bash: lesspipe: command not found
bash: command: command not found
bash: The: command not found
bash: dircolors: command not found
bash: Command: command not found
bash: The: command not found
root@POOT~#_
```

The fsck check thing has run before as I have a dual boot (Windows XP/Kubuntu Hardy Heron) system with a shared NTFS drive. Sometimes when XP locks up or needs a hard reset, upon booting Kubuntu, the fsck thing complains and will not mount the drive. That is usually easily fixed by rebooting windows and then rebooting once again into Linux. But this time the reboot was as a result of some problem with a hanging application in Linux itself. My partner is not computer literate and did not realise you can simply kill the app itself rather than restarting the pc.

I am not sure what to do about this error and unable to get into x or the desktop...

Any ideas?

---

### Post by Herman on 2008-07-25
Yes, you probably need to run e2fsck without the -a or -p options, You may need to recover some files from the /lost+found afterwards.
```
sudo e2fsck -y -f -v /dev/sdb2
```You should run that command from a live CD.

---

### Post by forger on 2008-07-25
You will need a live cd for this one :)

Follow this post:
[http://ubuntuforums.org/showthread.php?p=5454162#post5454162](http://ubuntuforums.org/showthread.php?p=5454162#post5454162)

but **don't use -fp** in e2fsck command as the error describes, you will be asked several questions where you will have to respond with simple yes/no (from what I remember)
for example:
```
e2fsck /dev/sbd2
```

---

### Post by c_martini on 2008-07-25
> **Herman said:**
> Yes, you probably need to run e2fsck without the -a or -p options, You may need to recover some files from the /lost+found afterwards.
```
sudo e2fsck -y -f -v /dev/sdb2
```You should run that command from a live CD.

> **forger said:**
> You will need a live cd for this one :)

Follow this post:
[http://ubuntuforums.org/showthread.php?p=5454162#post5454162](http://ubuntuforums.org/showthread.php?p=5454162#post5454162)

but **don't use -fp** in e2fsck command as the error describes, you will be asked several questions where you will have to respond with simple yes/no (from what I remember)
for example:
```
e2fsck /dev/sbd2
```

Thanks for the lightening fast response. whoa! I wasn't expecting anything until at least this afternoon, which is why I posted early while at work.

Thanks to both of you and will burn a fresh live cd and give it a go this evening and let you know how I made out...

:)

---

### Post by Herman on 2008-07-25
The -y option automatically says 'Yes' to any or all questions about whether to unlink certain files to the "Lost+Found" (owned by root), so you won't have to keep typing it yourself manually in case a lot of files need to be moved.

These will be renamed to the inode on which they were found.  

Afterwards you should be able to do "gksudo nautilus", and right-click on the "Lost+Found" folder, and change the file ownership and permissions. 
Then drag & drop the folders and files to another disc or a spare partition and see if you can identify them.
(Thanks to confused 57 for the above info).

If you're lucky they'll only be data files. 
Try to boot Ubuntu and keep your fingers crossed.
If Ubuntu still boots and everything works okay then good.
If Ubuntu doesn't boot or runs with problems, some vital operating system files may have been moved that might not be easy to identify and restore. If that's the case, you'll need to make a backup of all the rest of your files, and re-install Ubuntu maybe.

---

### Post by c_martini on 2008-07-25
I think perhaps I wasn't clear previously about this problem and it came to light once I tried your suggestions:

The partition in question is actually from an NTFS formatted drive. The strange thing is, the live cd boots and mounts all the drives with no problem. When I tried the above suggestions from the live cd desktop environment, I get the following errors (screenshot attached):

[IMG]http://chrisjmartini.googlepages.com/fsck_problem1.jpg[/IMG]

I would imagine that is because the drive is NTFS formatted. Actually the device (sdb2) is a 1kb partition which i don't understand as well... So what to do now? When i test the drive in Windows, no errors are reported...

:confused:

---

### Post by Herman on 2008-07-25
:oops: Oh, it has the NTFS file system...

Okay then, maybe you should check your /etc/fstab file first and make sure it's up to date and correct.

The method I use for doing that now is to type 'sudo blkid' into a terminal and copy the output from that, then open my /etc/fstab file and paste the blkid output to the bottom of it and 'hash it out'.

For example I copy this output,
```
herman@blackacer:~$ sudo blkid
/dev/sda1: UUID="2629-16F0" TYPE="vfat" 
/dev/sda2: UUID="78ef4f70-84eb-47bc-bf00-9af5692e3839" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda4: UUID="b1f95da4-09a0-4cd6-b5d0-facd57f0c94e" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="90f74a0c-6580-4f69-99aa-7561febb3fe5" 
/dev/sdb1: UUID="005D0DF776970DD3" TYPE="ntfs" 
/dev/sdb5: UUID="6ae3e4f2-0fb1-42b4-b2fe-3c78a75efa04" TYPE="ext3" 
/dev/sdb6: TYPE="swap" UUID="f992474b-63d4-4c85-adcd-e3155bb3bfac" 

```Then I get my /etc/fstab file open with root priveleges,
```
gksudo gedit /etc/fstab
``````
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb5
UUID=6ae3e4f2-0fb1-42b4-b2fe-3c78a75efa04 /               ext3    relatime,errors=remount-ro 0       1

# /dev/sdb6
UUID=f992474b-63d4-4c85-adcd-e3155bb3bfac none            swap    sw              0       0

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```...and I paste the blkid output to the bottom of my /etc/fstab file and make sure I comment each line out with a '#' (hash mark).```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb5
UUID=6ae3e4f2-0fb1-42b4-b2fe-3c78a75efa04 /               ext3    relatime,errors=remount-ro 0       1

# /dev/sdb6
UUID=f992474b-63d4-4c85-adcd-e3155bb3bfac none            swap    sw              0       0

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

[COLOR=Sienna][B]# /dev/sda1: UUID="2629-16F0" TYPE="vfat" 
# /dev/sda2: UUID="78ef4f70-84eb-47bc-bf00-9af5692e3839" SEC_TYPE="ext2" TYPE="ext3" 
# /dev/sda4: UUID="b1f95da4-09a0-4cd6-b5d0-facd57f0c94e" SEC_TYPE="ext2" TYPE="ext3" 
# /dev/sda5: TYPE="swap" UUID="90f74a0c-6580-4f69-99aa-7561febb3fe5" 
# /dev/sdb1: UUID="005D0DF776970DD3" TYPE="ntfs" 
# /dev/sdb5: UUID="6ae3e4f2-0fb1-42b4-b2fe-3c78a75efa04" TYPE="ext3" 
# /dev/sdb6: TYPE="swap" UUID="f992474b-63d4-4c85-adcd-e3155bb3bfac" [/B][/COLOR]

```Now if a line is incorrect or out of date, I can easily compare the file system types and UUID numbers from the blkid output, which is correct, to the corresponding information in my /etc/fstab file which may be incorrect out of date, and copy/paste the correct information to my /etc/fstab lines.

It may be that you had an ext3 file system there in your /dev/sda2 partition and you have since reformatted it to an NTFS file system and your /etc/fstab file and hence your Ubuntu operating system is still treating it as if it is formatted with ext3.
I'm not sure if that's the case or not, just making a guess.

If it's already listed as NTFS in your /etc/fstab file, you can tell Ubuntu not to bother running a file system check on it at boot-up by changing the last '1' or '2' in your /etc/ the /etc/fstab line for that file system to a '0', and Ubuntu will skip the file system check at boot-up for that partition.
For example,
```
#/dev/sda2     
   UUID=285F98566380864A   /media/ntfsdata  ntfs ro,umask=0002,nls=utf8      0         [COLOR=Red]**1**[/COLOR]
```[COLOR=#000000][FONT=Bitstream Vera Sans Mono]Change the '1' to a '0', like this,
[/FONT][/COLOR]```
#/dev/sda2     
   UUID=285F98566380864A   /media/ntfsdata  ntfs ro,umask=0002,nls=utf8      0         [COLOR=Sienna]**0**[/COLOR]

```Just make sure you do remember to run a file system check on that file system from Windows now and again, because all file systems do need checking quite frequently.

You can run a file system check in your NTFS partition from Linux these days quite safely if you want to, 
```
sudo apt-get install ntfsprogs
```
```
sudo umount /dev/sda2
```
```
sudo ntfsfix /dev/sda2
```

---

### Post by articpenguin on 2008-07-25
NTFSfix really dosent fix any ntfs errors all it does is reset the logfile and marks the dirty bit for chkdsk to run when windows boots

---

### Post by Herman on 2008-07-25
> NTFSfix really dosent fix any ntfs errors all it does is reset the logfile and marks the dirty bit for chkdsk to run when windows boots
:) Where did you get that information from?

---

### Post by articpenguin on 2008-07-25
It only repairs some  fundamental  NTFS
       inconsistencies,  resets  the  NTFS  journal file and schedules an NTFS
       consistency check for the first boot into Windows.

I think the fundamental ones are like the $bitmap connectivity and all that.

---

### Post by Herman on 2008-07-25
> It only repairs some  fundamental  NTFS
       inconsistencies,  resets  the  NTFS  journal file and schedules an NTFS
       consistency check for the first boot into Windows.

I think the fundamental ones are like the $bitmap connectivity and all that.:) Oh, okay, interesting.
Where are you getting this information from though?

:shock: Oh, okay, I just did some googling to find out more about that and it appears that you are correct, ntfsprogs' own site even admits that, here, [About ntfsfix]("http://www.linux-ntfs.org/doku.php?id=ntfsfix") - [www.linux-ntfs.org]("http://www.linux-ntfs.org").

Thank you for correcting me, I was wrong in my assumptions about ntfsfix, :oops:
Regards, Herman

---

### Post by forger on 2008-07-26
Well um.. maybe the partition editor check feature would help?

in ubuntu live cd head to system > administration > partition editor > on the **top right** corner choose your **hard drive device** > on the main area of the window **select your partition**, then right-click on it and select **Check**.
If check is greyed out, unmount the partition and try again

---

### Post by c_martini on 2008-07-28
Thanks for your suggestions, forger, Herman and articpenguin,

I finally was able to fix the disk by moving all the data to another disk. I then used the gparted live cd to delete the partition (and the 1kb one), and created a new partition, formatting it as ext3. This fixed the problem with Kubuntu not making it through the disk check during boot. Now I have an fstab mess since there are probably some erroneous entries that I need to get rid of in fstab. I have tried removing some of the stuff I am sure is wrong but its all a bit confusing to me.. Is there a way to regenerate a clean fstab?

running sudo fdisk -l gives me the following output:

```
Disk /dev/sda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x807fe5f9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2   *           2        9964    80027797+   5  Extended
/dev/sda5               2        9964    80027766    7  HPFS/NTFS

Disk /dev/sdb: 61.4 GB, 61492838400 bytes
255 heads, 63 sectors/track, 7476 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1ab41ab3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        4169    33487461    7  HPFS/NTFS
/dev/sdb2            4170        7337    25446960   83  Linux
/dev/sdb3            7338        7476     1116517+   5  Extended
/dev/sdb5            7338        7476     1116486   82  Linux swap / Solaris

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa4e736bb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        9729    78148161   83  Linux
```

That last section/drive in the fdisk output is the drive that was re-partitioned and formatted. I use this drive as shared drive between Linux and windows, as well as a smb network share, so it should be mounted as /media/shared. My Windows installation has a driver for ext3 so it does not matter that the drive was reformatted as ext3.

Can I somehow use the above output info to create a new fstab? Is there some tool in Kubuntu that will generate one for me so I don't mistakenly make a syntax or other error when trying to generate one manually?

---

### Post by Herman on 2008-07-28
:) That's a good move, upgrading from NTFS to ext3. Ext3 is a much better file system in my opinion.

As far as I know, there is no tool for refreshing our /etc/fstab files, we need to do that manually.
It would be nice if there was some software invented that could do that, something like out update-grub script, but for /etc/fstab.
I imagine the reason why there isn't one might be for security concerns. The /etc/fstab file is an important system file.

In Ubuntu Hardy Heron, we don't really need to have all our file systems listed in /etc/fstab any more, we can just go into our 'Places' menu and look around and find icons we can click on to mount all our file systems. I'm not sure about Kubuntu, but I imagine there would be something similar in Kubuntu Hardy Heron.

Your 'sudo fdisk -lu' output is useful, and if your can post the output from 'sudo blkid' here as well, plus a copy of your /etc/fstab file, I or someone else here can correct/update it for you if you like. 

Regards, Herman :)

---

### Post by cscat on 2008-09-18
Hi all,
You are GREAT. Just want to post here to thank Herman, forger, articpenguin and all the guys. You gave a new life to my lost Ubuntu. I didn't sleep all the night but after a lot of attempts I got my OS back!!!
Thanks a lot

---

