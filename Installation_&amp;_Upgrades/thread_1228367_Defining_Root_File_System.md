---
title: "Defining Root File System"
date: 2009-07-31
forum: Installation &amp; Upgrades
---

### Post by mt6112a on 2009-07-31
Hello there,
 
So I'm trying to install ubuntu on an old HP computer that my windows just completely crapped out on. i've been running off the live CD but want my CDROM drive back. So i've gone in and tried to install like 50 times, but every tie i get to the 4th screen i get an error message telling me that no root file system is defined, and I need to fix it in the partition menu. I've gone in the partition menu, repartitioned my hard drive, with 110GB put into an ext3 file system. I saved the other 10GB for an ntfs system, in case i want to interface with windows sometime in the future. so i did the repartitioning, checked for errors, labeled the partition, and got it remounted. But it still is not recognized in the 4th stage of the installation process. I have gone through a ton of threads on here already and have not been able to find an answer. Can anyone help?
 
Mike

---

### Post by merlinus on 2009-07-31
Once you have set a size and format (e.g. ext3) for the partition, rightclick on it (or click and select edit).  Then you should get a dropdown menu with mountpoints.  Choose /.

---

### Post by mt6112a on 2009-07-31
I don't have that option, Merlin.  It's already mounted to /media/butt (butt is the label - I know, real mature)
 
If it helps, I saw a thread earlier between Mason Whitaker and taurus, where taurus asked him to run a command "sudo fdisk -l" from the terminal.  I ran it and here's what mine said:
 
**Terminal Command Results:**
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x02cc02cb
 
Device        Boot    Start     End            Blocks           Id      System
/dev/sda2   *         1          13303        106856316     83      Linux
/dev/sda4   *         13304   14593        10361925       7        HPFS/NTFS
 
 
Is that even relevant?

---

### Post by merlinus on 2009-07-31
Run this command as well

```
df -h
```

---

### Post by mt6112a on 2009-08-02
I don't think the spacing will display correctly, but here's what I got:
 
Filesystem        Size     Used      Avail     Use%     Mounted on
tmpfs               220M      20M     218M      1%       /lib/modules/2.6.27-7-generic/volati
le
tmpfs               220M      20M     218M      1%       /lib/modules/2.6.27-7-generic/volati
le
tmpfs               220M       0        220M      0%      /lib/init/rw
varrun             220M       84K    220M      1%      /var/run
varlock            220M       0        220M       0%     /var/lock
udev                220M     2.8M     217M      2%     /dev
tmpfs               220M     220K    200M      1%      /dev/shm
rootfs               220M     19M     201M       9%     /
/dev/scd0         699M     699M    0M         100%   /cdrom
/dev/loop0        676M     676M   0M          100%  /rofs
tmpfs               220M      12K     220M       1%     /tmp
/dev/sda2        101G       188M    96G       1%     /media/butt
 
Let me know if the spacing is too unreadable and i can type it and do a screenshot or something.  Thanks Merlin

---

### Post by merlinus on 2009-08-02
What folders and files are at /media/butt?

It looks like some few / files have been installed, but far less than what is needed, and there is no / partition.

Are you installing from the live cd?  Have you checked the cd for errors at the opening menu?  Did you do a checksum on the .iso?

---

### Post by mt6112a on 2009-08-03
Hey Merlin,
 
Baby steps here, sir. Haha.  I think I'm a little lost.  When i pull up butt in the browser window, all that's in there is a folder titled "Lost & Found." 
 
I am really starting from scratch here with ubuntu, so I don't know what files would need to be installed; I assumed the installer would do that for me.
 
It seemed as though there was a / partition, at least from the output of that last command.  one of the lines was rootfs, and it was mounted to "/".  I think i just need to figure out how to put butt there.
 
Yes, I am installing from the live CD.  I do not know how to check the disc for errors; could you please help point me in the right direction for that?  When i start up, it first brings up a window asking me to select a language. It highlights English by default and starts a countdown.  I hti Enter but nothing happens, so I let the countdown run out and it goes into ubuntu (after taking a bit to load).  I've never seen any other opening menu...
 
And I don't know what a checksum or a .iso is, but if you'd be kind enough to let me know, I can try it out.
 
Thanks again
 
-Mike

---

### Post by merlinus on 2009-08-03
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

If it checks out, burn the .iso at more than 4x to a CD-R disk.  Then boot from it, and when you get to a menu after selecting language, there is an option to check the cd integrity.

---

### Post by mt6112a on 2009-08-03
I still have the .iso file I used on another computer.  I checked it, and the hashes match.  So the file I used to burn that disc is supposedly OK.  But I can try it again.
 
Does it have to be a CD-R or would a CD-RW work too?

---

### Post by mt6112a on 2009-08-03
Oh, one more thing.  I used ImgBurn 2.4.2.0 to burn the CD.  should I try some other software?

---

### Post by merlinus on 2009-08-03
CD-R seems to work best, at no more than 4x speed.  The software does not matter, as long as it is capable of burning a disk image.

---

### Post by mt6112a on 2009-08-04
I'm just curious as to why it has to be at less than 4x speed....  I tried reburning a few times last night but think I ran into trouble with the burning software, which was defaulting to a higher speed for the disk even though i asked the program to write at 2x more than once.  So I'm going to burn from work today but I can't try the disk before tomorrow evening, so I'll let you know then how it works out

---

### Post by mt6112a on 2009-08-04
OK So IMGBurn is a piece of junk that refuses to just burn CDs at 2x.  I have changed the settings multiple times trying to get it to burn at 2x and it for some reason won't stop defaulting to like 40x or higher.  I just don't get it.  So I guess I've got two questions:
 
First, why does it need to be at less than 4x, and since mine wasn't done at 4x, will it not work? (Also, is this maybe why I never saw the menu with the disc check option on the first one I burned?)
 
Second, is there any software you would suggest using that actually responds when a user asks it to do something?
 
Thanks again, Merlin.

---

### Post by merlinus on 2009-08-04
Infrarecorder, a freeware burning program for windows, as always worked perfectly for me.  Fast burns can easily corrupt data.

[URL="http://sourceforge.net/projects/"]http://infrarecorder.org/?page_id=5
[/URL]

---

### Post by mt6112a on 2009-08-05
Hey Merlin,
 
So I burned two CDs with different programs as slow as I could get them to go, with Ubuntu 9.04 (I had been using the 8.10 previously).  I tried booting with each CD and when it went to that language portion, again it wouldn't respond when I hit enter, and it never gave me the option to check the CD.
 
However, I tried the installer again and it's more advanced (as I'm sure you know), and it's now giving me the option of installing ubuntu to my entire hard disk.  I'm not totally against doing this, but only if I will later have the option to change the size of that partition.  I assume I would, but I just wanted to make sure; so if I install to my entire hard disk (assuming it will do so successfully), I'll be able to change the partition size later if I want to, right?
 
Or the other option I've got is to "install side by side and choose at startup," and it seems to be recognizing the two partitions i made ("butt" and "ntfs").  When I click on it, it tells me:
"before you can change partition size any previous changes have to be written to disk.  this operation can not be undone."  What does that mean?  I don't have any pending changes from the partition editor, so is it referring to something else?
 
Sorry for the dumb questions.  I'm still a novice, as you can clearly see

---

### Post by merlinus on 2009-08-06
If you choose use entire disk, then yes, you will be able to shrink that partition using gparted, and create another one in hte freed-up space.

If you have no data to lose, that might be the easiest way to go.

---

### Post by mt6112a on 2009-08-10
Hey Merlin,
 
So I went ahead and tried the installation, and it seemed to work properly.  However, when I went to reboot my computer (after removing the disc at shutdown like it asked), I ran into the same problem I had way before (which is why i tried Ubuntu/Linux in the first place); it asks me to "reboot and select proper device..." Basically, it's asking me to insert the Windows setup CD.  I had this problem a while ago, and since I could never find the original CD for my computer (and since HP coincidentally doesn't make the Windows CD for my computer anymore), I started using Ubuntu and another form of Linux to access my files.  I hoped that by installing ubuntu it would load automatically, i.e. boot right into Ubuntu when the computer started.  Apparently, this wasn't the case.  From my limited knowledge of computers, and a few discussions with various folks, I think this has something to do with the BIOS, but I've got no clue how to change that.  Also, the computer is unresponsive before this message comes up, so I can never access the setup menus or anything; it just goes right to this screen, regardless of how many times I hit F1 or F8 or F10 or F11 or any other key(s).  Do you have any ideas how I can force my computer to boot into the now-installed Ubuntu?

---

### Post by merlinus on 2009-08-10
If you can run from the live cd, open a terminal and post results of

```
sudo fdisk -l
```

My guess is that you did not notice the advanced button at the last install screen, which is not at all obvious, and so grub did not get installed to the mbr of your hdd.

Let's try to fix that.

---

### Post by mt6112a on 2009-08-10
Here's what I get:
 
Disk/dev/sda: 120.0 GB, 12003412776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x02cc02cb
 
Device       Boot      Start      End       Blocks          Id        System
/dev/sda1      *         1         14431    115916976    83       Linux
/dev/sda2                14432   14593    1301265       5         Extended
/dev/sda5                14432   14593    1301233+     82       Linux swap / Solaris

---

### Post by merlinus on 2009-08-11
Try this whilst running from the live cd:

```
sudo grub
root (hd0,0)
setup (hd0)
quit
```

Remove live cd and restart.

---

### Post by mt6112a on 2009-08-12
No luck with that Merlin
 
I still get the error message when I start up.  It says:
 
"Reboot and Select proper Boot device
or Insert Boot Media in selected Boot device and press a key"
 
Any other suggestions?

---

