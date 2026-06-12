---
title: "Vista-Ubuntu Shared Partition w/ Existing Files"
date: 2009-08-16
forum: Installation &amp; Upgrades
---

### Post by cvandor on 2009-08-16
Hi I just installed Ubuntu 9.04 through the boot-from-disk process. to create a dual boot with Vista.  Both are 64 bit.  I want to create a shared partition between both OS for files in NTFS, but i already have some files created in Vista (ie. itunes music, documents, etc.).  Is there a way to partition the drive so that i can keep those files and still create a shared partition?

---

### Post by Yvan300 on 2009-08-16
Use vista's built in partitioner to resize your disk to get enough space and then partition it to fat32 so that ubuntu and windows can write to it.

Simple, good luck :)

---

### Post by cvandor on 2009-08-16
ok, but i would prefer to use the ntfs format to avoid fragmenting.  I read somewhere that the newer Ubuntu versions support this format.

---

### Post by Yvan300 on 2009-08-16
As far as i know, ntfs suffers from fragmentation, i had vista as well once ago and i had to defragment my hard drive which was ntfs. If you want to avoid fragmentation, then you need to use one of the linux file systems, such ext3 or ext4. Note that in order for your vista to read etc from this, you would need to install a driver.

---

### Post by cvandor on 2009-08-16
hmm.  I already have files being accessed for vista. can i switch to ext3, install the driver in vista, while keeping my files?  also, how can i do this using the partition editor during the ubuntu install?

---

### Post by Yvan300 on 2009-08-16
I suggest that you repartition your vista partition using the built in partitioner that is available. You should do this because when you recise vista using ubuntu's partitioner, there is a chance that vista's boot loader may get corrupted.

After you resize it, then you can use ubuntu to format it to ext3, if you need more details, just ask :)

---

### Post by raymondh on 2009-08-16
> **Yvan300 said:**
> Use vista's built in partitioner to resize your disk to get enough space and then partition it to fat32 so that ubuntu and windows can write to it.

Simple, good luck :)

Here are the advantages/disadvantages of either FAT32 or NTFS as a file system.

[http://technet.microsoft.com/en-us/library/cc938932.aspx](http://technet.microsoft.com/en-us/library/cc938932.aspx)
[http://technet.microsoft.com/en-us/library/cc940351.aspx](http://technet.microsoft.com/en-us/library/cc940351.aspx)

Both suffer from fragmentation hence the need for regular maintenance.

I consider NTFS more robust than Fat32.  Ubuntu can read/write into NTFS thru the use of NTFS-3g (applications > add/remove > search for NTFS)

I have not done so but, you can also make mount an ext drive in windows for read/write access.

[http://linuxhelp.blogspot.com/2007/03/mount-ext2-or-ext3-partition-in-windows.html](http://linuxhelp.blogspot.com/2007/03/mount-ext2-or-ext3-partition-in-windows.html)

If your files are NTFS based and you decide to change it to ext, that will require reformatting the particular drive/partition which risks' erasing your files in that drive.  As such, back-up your files someplace else first.

Good luck.

---

### Post by joelgsf on 2009-08-16
I am running Ubuntu 9.04 64-bits dual booting with XP, which was my original system, having all my personal files in a separate logical drive (NTFS partition). I resized all Windows partitions before installing Ubuntu, and now, after installation, I have access to all stuff that is there, on the NTFS partitions, which Ubuntu recognises automatically for me.
I beleive this is te easiest way. For sure NTFS gets fragmented with time, but you can allways boot into Windows and clean things up.

---

### Post by cvandor on 2009-08-17
alright, so i finished the ubuntu install and had a few problems.  it says it only has about 480 Mb of space to use when i try to update. i think it recognizes the rest of the 450 Gb or so, but how do i create more room for the installs and updates.  i guess i dont really understand what exactly im supposed to do with each partition and how many to have

---

### Post by raymondh on 2009-08-17
> **cvandor said:**
> alright, so i finished the ubuntu install and had a few problems.  it says it only has about 480 Mb of space to use when i try to update. i think it recognizes the rest of the 450 Gb or so, but how do i create more room for the installs and updates.  i guess i dont really understand what exactly im supposed to do with each partition and how many to have



If you access a terminal and type (post back as well)

```
df -h
```

We'll get to see allocations/usage.  Also, post back output of

```
sudo fdisk -l
```

(small L not 1 nor I)

Hunch is you have either the '2.5GB install' or you established very minimal size allocations for root (/).  The 2.5GB install happens when we select side-by-side (or guided resize) but forget to use the slider to allocate size preferences for both OS .... that or something happened during the install part that it defaulted back to the 2.5GB sizing.

Depending on the output of both commands, you will have to get space from somewhere and enlarge ubuntu root (/) to occupy that space.  Here's a read through using gparted.

[http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)

---

### Post by cvandor on 2009-08-17
calvin@calvin-laptop:~$ df -h
Filesystem                  Size  Used  Avail  Use%  Mounted on
/dev/sda5                  2.3G  2.3G       0  100%   /
tmpfs                        1.9G       0   1.9G     0%   /lib/init/rw
varrun                       1.9G  108K  1.9G     1%   /var/run
varlock                      1.9G       0  1.9G     0%   /var/lock
udev                         1.9G  176K  1.9G     1%   /dev
tmpfs                        1.9G  372K  1.9G     1%   /dev/shm
lrm                           1.9G  2.7M   1.9G     1%   /lib/modules/2.6.28-11-generic/volatile
overflow                    1.0M   16K 1008K    2%   /tmp
/dev/sdal                  438G   79G  360G   18%   /media/disk

calvin@calvin-laptop:~$ sudo fdisk -l
[sudo] password for calvin

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk Identifier: 0x87b33479

   Device Boot       Start          End          Blocks    Id   System
/dev/sda1   *              1      57086  458543263+    7   HPFS/NTFS
/dev/sda2            59073     60801     13884416      7   HPFS/NTFS
/dev/sda3            58748     59072      2610562+    5    Extended
/dev/sda5            58748     59050      2433816     83   Linux
/dev/sda6            59051     59072        176683+  82    Linux swap / Solaris

Partition table entries are not in disk order


*****

firefox isnt working on ubuntu so im typing everything over on my XP laptop.

---

### Post by raymondh on 2009-08-17
> **cvandor said:**
> calvin@calvin-laptop:~$ df -h
Filesystem                  Size  Used  Avail  Use%  Mounted on
/dev/sda5                  2.3G  2.3G       0  100%   /
tmpfs                        1.9G       0   1.9G     0%   /lib/init/rw
varrun                       1.9G  108K  1.9G     1%   /var/run
varlock                      1.9G       0  1.9G     0%   /var/lock
udev                         1.9G  176K  1.9G     1%   /dev
tmpfs                        1.9G  372K  1.9G     1%   /dev/shm
lrm                           1.9G  2.7M   1.9G     1%   /lib/modules/2.6.28-11-generic/volatile
overflow                    1.0M   16K 1008K    2%   /tmp
/dev/sdal                  438G   79G  360G   18%   /media/disk

calvin@calvin-laptop:~$ sudo fdisk -l
[sudo] password for calvin

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk Identifier: 0x87b33479

   Device Boot       Start          End          Blocks    Id   System
/dev/sda1   *              1      57086  458543263+    7   HPFS/NTFS
/dev/sda2            59073     60801     13884416      7   HPFS/NTFS
/dev/sda3            58748     59072      2610562+    5    Extended
/dev/sda5            58748     59050      2433816     83   Linux
/dev/sda6            59051     59072        176683+  82    Linux swap / Solaris

Partition table entries are not in disk order


*****

firefox isnt working on ubuntu so im typing everything over on my XP laptop.


Mr. Cvandor,

As you can see, you have the 2.3GB install and root (/) is already close-to-full.  We'll need to expand root partition.

Assuming this is not a WUBI-installed ubuntu ....

This sentence may cause you problems later on...
[B][I]
Partition table entries are not in disk order[/I][/B]

What do you prefer to do?

1.  Shrink windows - enlarge extended - enlarge root partition or;
2.  Re-do the installation which will require
a.  Erasing current Ubuntu
b.  Resizing windows to get more unallocated space (about 15-20GB for a nice, breathing Ubuntu root ... but does not include space for your data & media...all depends on your needs)
c.  Installing Ubuntu in the bigger unallocated space.

Somewhere in between (in option 2), we will also defrag windows as much as possible (2x if you have the time).

In the meantime (while you ponder your decision)

1.  Think of how much space you want to give Ubuntu based on how you plan to use the OS.  15GB is good for root alone.
2.  Do you hibernate your computer and, how much RAM do you have as well as how much RAM are you capable of having?
3.  Have you tested the liveCD (in live session) to see if it plays well with your system/hardware (wifi, fn keys, etc, etc)?
4.  Do you wish to have a separate /home partition to store your config files, settings, etc so that (in the future) in case you need to re-install, you can retain the same settings, etc.?

Some reading materials to reference what you are about to do:

[Jaunty release notes]("http://www.ubuntu.com/getubuntu/releasenotes/904")
[http://ubuntuforums.org/showthread.php?t=282018](http://ubuntuforums.org/showthread.php?t=282018)
[http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)
[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)

We'll go from your decision.  In the meantime, back-up your files as there are no guarantees when working with partitions.

---

### Post by Yvan300 on 2009-08-17
Basically your 200gb is not really allocated to ubuntu but really to your data. And you have done is that you allocated to little space to root(/) which is where ubuntu stores itself. So all you have to do is add more space to root and you should be fine :D

---

### Post by cvandor on 2009-08-17
Well, i have a 500GB hard disk so im not worried about space for windows. eventually i would like to switch over to Ubuntu as my main OS, so i think splitting the 500 fairly evenly between would be a good idea.  I do hibernate my computer occasionally and i have 4GB RAM.  I think having a separate /home partition would be a good idea as well.  Also, my computer has some extra features which ive heard can be problematic with linux (ie. webcam, blueray, fingerprint reader).  the webcam and blueray are more important, but ive also heard they can be used with some research and finding theright drivers. so i think you first suggestion, to shrink windows, would be best.

---

### Post by raymondh on 2009-08-17
> **cvandor said:**
>  so i think you first suggestion, to shrink windows, would be best.


Files backed up?  NTFS partitions defragged?  Power cable plugged?  You sure you don't want to pay attention to your current "not in disk order"?

I think you said you were posting from XP. XP cannot shrink so we'll use gparted.  If you have Vista, that is different as I prefer to use Vista to shrink a NTFS/windows partition.  

Leaving sda1 alone (and getting space from sda2) to minimize risks on your windows install ....

1.  Boot into your liveCD and in live session (try ubuntu without...)
2.  Access gparted (system > administration > partition editor
3.  Double check that the partitions are unmounted.  Example, Rt. click on sda2 and if given option to unmount, do so. Same for swap and select swapoff.
4.  Click to Highlight sda2 and resize/shrink appropriately as decided by grabbing the slider and moving such.  As you slide, note below and see how the sizing changes.  No need to be accurate at this point.
5.  Click to Highlight the EXTENDED (sda3) partition and enlarge appropriately by grabbing the slider and sliding towards the border of sda2.
6.  Highlight root partition (sda5) and grab/slide the up to the right-border of the extended (sda3).
7.  Leave swap alone.  For the /home, see below and link to psyhocats' tutorial.

Review and apply.  Quit gparted, the liveCD and reboot.  Access terminal and check with a df-h command.  If satisfied, go ahead with normal updating.

For having a separate /home (since you did not create it during the install), [see here]("http://www.psychocats.net/ubuntu/separatehome").  How much space for /home has to be added to your resizing efforts above.  I understand you have a shared data/media partition.

My suggestion for sizing purposes:

Root (/) 15GB
/home    30GB

Knowing that you only have 2.3GB current .... you need to take about 45GB from sda2 and that'll give you 47GB for Ubuntu.  Let's worry about enlarging swap later.

This will take time.  Hence the suggestion to re-do which might be 'cleaner'.

As for having that 50-50 split, you'll have to take space from sda1 and enlarge sda2.

Again ... see the link in previous post about re-sizing for reference.

Post back if you need clarifications.  If you want, before proceeding, post an screenshot of gparted so the forum has a visual guide of your HD.

Good luck.

---

### Post by cvandor on 2009-08-17
oh sorry. i forgot to add that i would like to address the "not in disk order" msg., but im not sure what to do with that.  the XP im posting from is another, older laptop, so yes, im using vista for the same laptop as ubuntu.  hope that clears some things up.

---

### Post by raymondh on 2009-08-17
> **cvandor said:**
> oh sorry. i forgot to add that i would like to address the "not in disk order" msg., but im not sure what to do with that.  the XP im posting from is another, older laptop, so yes, im using vista for the same laptop as ubuntu.  hope that clears some things up.

Kindly post a screenshot of what gparted outputs.

---

### Post by cvandor on 2009-08-17
im using vista, i should still use gparted?

---

### Post by cvandor on 2009-08-17
if doing a reinstall would be cleaner and faster, then i would like to go with that option.  am i correct in that i will be able take care of these things in the ubuntu re-install.  If so, how would i go about it. im sorry to be changing things, but i would prefer to do things as cleanly as possible

---

### Post by raymondh on 2009-08-17
> **cvandor said:**
> if doing a reinstall would be cleaner and faster, then i would like to go with that option.  am i correct in that i will be able take care of these things in the ubuntu re-install.  If so, how would i go about it. im sorry to be changing things, but i would prefer to do things as cleanly as possible

I know the forum has your fdisk output ... but help us visualize the HD thru a screenshot of gparted.

1.  Boot into the liveCD (if your current Ubuntu is bootable ... then use your current Ubuntu)
2.  Access gparted (system > administration > partition editor
3.  When gparted opens, you can either press "printscreen" (one of the function keys above/on the keyboard) and save the output to your desktop or.... access 'take a screenshot' (applications > accessories), position the open windows that none overlaps the other, select grab the current window, click to highlight the gparted window, take a shot and save to desktop.
4.  When you reply to the thread, click on the ATTACH (beside the smiley icon on top of window).  Another window opens.  Browse to your desktop and open the saved screenshot. Upload.  When done, close the window. Continue with your reply/post if you need to include any other info.  Send.

Thanks.  I want to compare the fisk with the gparted shot. In the meantime, I'll start with a tutorial to re-do.

What's currently in sda2?

---

### Post by raymondh on 2009-08-17
Calvin,

Will be back in about 2 hrs.  Supper time with the kids.  There's another thread going on at absolute beginners forum about resizing/expanding.  Suggest you read thru it even though your goal now is to re-install and create partitions for a /home, etc.

[http://ubuntuforums.org/showthread.php?t=1242940](http://ubuntuforums.org/showthread.php?t=1242940)

Raymond

---

### Post by cvandor on 2009-08-17
ok sda2 is the windows recovery.

heres a copy of fdisk again:
ubuntu@ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
tmpfs                 1.9G  2.7M  1.9G   1% /lib/modules/2.6.28-11-generic/volatile
tmpfs                 1.9G  2.7M  1.9G   1% /lib/modules/2.6.28-11-generic/volatile
tmpfs                 1.9G     0  1.9G   0% /lib/init/rw
varrun                1.9G  104K  1.9G   1% /var/run
varlock               1.9G     0  1.9G   0% /var/lock
udev                  1.9G  176K  1.9G   1% /dev
tmpfs                 1.9G  380K  1.9G   1% /dev/shm
rootfs                1.9G   40M  1.9G   3% /
/dev/sr0              697M  697M     0 100% /cdrom
/dev/loop0            674M  674M     0 100% /rofs
tmpfs                 1.9G   16K  1.9G   1% /tmp
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x87b33479

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       58747   471883935+   7  HPFS/NTFS
/dev/sda2           59073       60801    13884416    7  HPFS/NTFS
/dev/sda3           58748       59072     2610562+   5  Extended
/dev/sda5           58748       59050     2433816   83  Linux
/dev/sda6           59051       59072      176683+  82  Linux swap / Solaris

Partition table entries are not in disk order

some of the numbers may look different, because i had a bunch of unallocated space from a resize of sda1 that i did earlier. i re-extended sda1 in vista earlier so that my hard drive would be back to normal. extension of about 13GB.  other than that i didnt do anything else.

the corresponding GParted image is attached

---

### Post by raymondh on 2009-08-17
Wow ... I, for one, am glad I saw that visual.  I was assuming sda2 was the shared /data partition you were talking about earlier.  Whew!  I see that you don't have the shared data/media partition yet ... am I right?

In this set-up, partition order (or lack of it) is manageable.  Much better than partitions not ending in cylinder bounderies ... which I was thinking :)  

You can elect to resize & move or ....you can re-install whilst establishing your /home.

If you choose to resize (using a 50GB ubuntu install):

1.  Defrag sda1 (Vista).  defrag 2x if you have the time.
2.  Access in Vista the disk management tool and use that to shrink sda1.  Goal is to have a unallocated space of about 47GB.
3.  Quit Vista and Windows and boot into the liveCD and gparted in live session.
4.  2-check that the partitions are indeed unmounted.  Swapoff for swap. You'll know that it's still mounted when you have a greyed-out option to resize.
5.  Click (or highlight) sda3 > grab the left-side slider and drag left to touch the boundary of sda1. This enlarges the extended partition.
6.  Next is sda5. You can either resize/enlarge to the left or, move the whole partition to the left and then enlarge to the right.  Goal is to occupy available space.  (see link about gparted & resizing in previous post)

* For the /home, you can try psychocats' tutorial later on (see previous posts')

7.  Review > apply when satisfied > quit and close gparted when finished > exit live session > reboot into Ubuntu > double check df-h in terminal > if satisfied, continue the update.

If you choose to re-do (again 50GB Ubuntu) :

1.  Defrag Vista
2.  Use Vista's disk management tool to shrink Vista (having about 47GB unallocated space)
3.  Close and exit Vista and boot into the liveCD and live session for gparted.
4.  2-check partitions are unmounted.
5.  Highlight and delete these partitions in order (sda6, sda5, sda3).  You ought to end up with about 50GB unallocated.  Review and apply.
6.  Left Click on unallocated space > **partition** menu > **new** > make **EXTENDED** and **use all space**.  Review and apply.
7.  Click inside newly-created extended.  You will make 3 partitions.
8.  Let's make **SWAP** first.  4GB in size.  Format **LINUX SWAP FILE SYSTEM**.
9.  Next, well make a 15GB partition and format EXT3.  This is for root (/).
10. Last is another EXT3 partition and 'use all remaining space'.  This is for /home later.
11. Review, apply and when created, quit gparted.
12. Still in same live session ... select INSTALL.
13. When you get to the partitioning stage (step 4, I think), select **MANUAL**.
14. Select the SWAP partition and click **EDIT** (button below). Set it to **USE **and **SWAP** *type*
15. Next, select the 15GB partition and edit. Set it to **USE**...**EXT3**...and **/** *type*
16. Lastly, select the remaing partition.  Set to **USE** ... **EXT3** ... and **/home** *type*.

Continue with the install.  Once done, boot into Ubuntu.

Note: I am thinking that as this is a re-install, GRUB will re-write itself again unto the MBR as well as delete the old Ubuntu.  It will re-write but, if on boot up, you are given 2 Ubuntu (not kernels) options, we'll just edit the menu.lst later on.

That's it.  Back-up.  Make sure power cable is plugged. ***Post back if you need clarifications***.

We can do the shared partition later on .. taking it from sda1 again.

Good luck.

---

### Post by cvandor on 2009-08-17
alright thanks.  ill will post back after.

---

### Post by cvandor on 2009-08-18
ok so i defragged C: but when i tried to shrink it i was given a maximum of 12977MB to shrink by because "size of available shrink space can be restricted if snapshots or pagefiles are enabled on the volume".  i googled this and found a variety of options, but none that i am comfortable with.

---

### Post by raymondh on 2009-08-18
> **cvandor said:**
> ok so i defragged C: but when i tried to shrink it i was given a maximum of 12977MB to shrink by because "size of available shrink space can be restricted if snapshots or pagefiles are enabled on the volume".  i googled this and found a variety of options, but none that i am comfortable with.

Yes, you have to disable pagefiling, etc.  Windows also has this habit of writing files all over the disk and some of them are immovable (i.e. MFT).

If uncomfortable with that ..... 12977mb is about 12GB.  Add that to your existing 2.3 and you'll have about 14-15GB.  You can still have a decent Ubuntu.  At that size, I suggest you forego the separate /home.  Also keep SWAP to minimum.  Your option whether to resize or re-install... (either can work) but for simplicity, just resize root (/) and don't touch swap.

EDIT : if you have the original Vista installation disk (not the OEM-supplied recovery disk), you can use gparted to resize and then use the Vista installation disk to fix any errors.  [See this link.]("http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/")

Good luck.

---

### Post by cvandor on 2009-08-18
After doing some more research, I found a website where a guy is explaining how to dual boot windows vista and windows 7.  Although the OS are not the same, he went on to solve the problem i described above.  [http://www.brighthub.com/computing/windows-platform/articles/22459.aspx](http://www.brighthub.com/computing/windows-platform/articles/22459.aspx).  Apparently the program, PerfectDisk, can solve the problem of immovable (including MFT) files even when disable pagefiling, snapshots, etc. doesn't.  It's supposed to be a more capable disk defragmenter.  I'm trying the 30-day trial now.

---

### Post by raymondh on 2009-08-18
> **cvandor said:**
> After doing some more research, I found a website where a guy is explaining how to dual boot windows vista and windows 7.  Although the OS are not the same, he went on to solve the problem i described above.  [http://www.brighthub.com/computing/windows-platform/articles/22459.aspx](http://www.brighthub.com/computing/windows-platform/articles/22459.aspx).  Apparently the program, PerfectDisk, can solve the problem of immovable (including MFT) files even when disable pagefiling, snapshots, etc. doesn't.  It's supposed to be a more capable disk defragmenter.  I'm trying the 30-day trial now.

Cool.  Post back if you run into "stumbling blocks" ... no pun intended :)

---

### Post by cvandor on 2009-08-18
Okay i was able to increase that shrink space successfully to about 219GB, which is definitely sufficient.  I will proceed with your original instruction of 47GB.

---

### Post by cvandor on 2009-08-18
The install went perfectly.  I also fixed a problem with my sound.  Now, what should i do for the shared partition?  Also, am I correct in saying that installations are saved to the /home partition? Or is it /? Or, am I completely wrong and do not understand?  I expect it is the latter.  In addition to the shared partition, can you explain to me how the files, programs, drivers, etc. are divided between the partitions, as well as whether or not I will have to manually direct the computer to put those things in their respective partitions.

---

### Post by raymondh on 2009-08-18
> **cvandor said:**
> The install went perfectly.  I also fixed a problem with my sound.  Now, what should i do for the shared partition?  Also, am I correct in saying that installations are saved to the /home partition? Or is it /? Or, am I completely wrong and do not understand?  I expect it is the latter.  In addition to the shared partition, can you explain to me how the files, programs, drivers, etc. are divided between the partitions, as well as whether or not I will have to manually direct the computer to put those things in their respective partitions.

Congratulations =D>

Proceed with the initial update and enjoy your new Ubuntu.

You are correct .... your Ubuntu install is in root.  That's why if you ever need to re-install 9.04, you rewrite/reformat over root and do not format /home.  Having a separate /home makes such re-installation more convenient since you don't have to reinstall your previous settings, etc.  It does not guarantee that you will lose files ... hence the need for regular back-ups.

See this article about the [linux filesystem]("http://www.freeos.com/articles/3102/").

Can you share again the new layout/gparted?

The process to create a data/media partition will be the same.  I think (without seeing the new gparted) you already have 2 primary partitions and 1 extended.  You can still add another primary partition.

Again, congratulations.

---

### Post by cvandor on 2009-08-18
heres the GParted image.

---

### Post by cvandor on 2009-08-18
here it is

---

### Post by cvandor on 2009-08-18
3rd time's a charm.:)

______
forgot to hit upload.

---

### Post by raymondh on 2009-08-19
The process (shrink from sda1 > create a new PRIMARY, Format NTFS, label CALVIN -if you wish) will be the same.  

If unhappy and you decide otherwise, delete THAT new "calvin" partition and then extend sda1 to occupy it again.

Happy Ubuntu-ing.

---

