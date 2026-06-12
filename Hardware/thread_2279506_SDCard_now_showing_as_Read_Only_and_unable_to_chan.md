---
title: "SDCard now showing as Read Only and unable to change permissions"
date: 2015-05-23
forum: Hardware
---

### Post by kazakore on 2015-05-23
I have a Canon SX280 camera and a Transcend 32GB SD Card I have been happily using since I bought them last August/September (so something like 9 months) with no problems. I go to take some of the photos off the SD card today but all of a sudden all the images are showing as Read Only and will not change when I try and make them Read/Write for more than just the Owner (me.)

I have found a mini-usb cable and I can delete the files if I connect to the camera, rather than use the SD card slow on my computer.

Computer is a Lenovo X230 with built in card reader.

Any idea why this might be? I would like to be able to move and delete files directly from the SD card again! Never had this issue before!


EDIT: Started working by its own accord after an update. Afraid can't give conclusive reasons as to why.

---

### Post by tgalati4 on 2015-05-23
There is a small, plastic switch on the SD card to make it read-only.  I have accidentally pushed it when sliding the SD card into a laptop reader.  Check the position of the switch and change it.

---

### Post by kazakore on 2015-05-23
Had already tried with switch in both position to make sure, plus the fact it then worked while inside the camera rules that out as a possible cause anyway ;)

---

### Post by kazakore on 2015-05-23
Just realised though, I haven't edited, and thus transferred, any photos for some months now and I reinstalled using Ubuntu Studio 14.04.1 (rather than straight 14.04) some point in Vietnam, since last doing photo things. Probably it hasn't worked since the reinstall I just hadn't realised by now. Although fairly sure I used the card slot with a MicroSD>SD adapter and it worked... Actually I used rsync and I now remember there being an error message at the end about it not being able to change read/write permission so possibly suffered from the same fault.

---

### Post by kazakore on 2015-06-01
So over a week and no useful replies. Whatever happened to Ubuntu having a helpful community and this being one of the major things to put it above many of the other Linux distributions?!?!

---

### Post by tgalati4 on 2015-06-01
Reboot your laptop.  Insert the SD card into the laptop's SD card slot.  Open a terminal and post the output of:

```
dmesg | tail -50
```  

Only post the SD card messages.

---

### Post by NoWayWin8 on 2015-06-01
I had this happen with an SD card too. I forget what the cause was, but the solution was to dismount/remove any media shown under /media/username/ and then delete the username folders listed in /media/. Now Reboot and after that the SD card should mount with the correct file permissions.

---

### Post by kazakore on 2015-06-02
> **tgalati4 said:**
> Reboot your laptop.  Insert the SD card into the laptop's SD card slot.  Open a terminal and post the output of:

```
dmesg | tail -50
```  


Only post the SD card messages.

> **NoWayWin8 said:**
> I had this happen with an SD card too. I forget what the cause was, but the solution was to dismount/remove any media shown under /media/username/ and then delete the username folders listed in /media/. Now Reboot and after that the SD card should mount with the correct file permissions.

Typical! It appears to be working as normal now (just moved rather than copied a directory with no complaints.)

I did do a apt-get update && upgrade yesterday, which while on my travels I was doing less often than usual due to rarity of having a decent internet connection, so possibly due to a core component update. Fingers crossed it doesn't return...

Have been finding my laptop getting worrying slow in general at points recently, especially if trying to read and write from my internal hard drive at the same time (only to the extent of say running an upgrade while listening to music, which it used to be fine with before) and it will pretty much grind to a halt. It passed SMART when tested yesterday but I have my suspicions the HDD is on its way out. That doesn't really relate to this thread though, so thanks for your help on this matter :)

---

### Post by sudodus on 2015-06-02
If the root partition '/' (the system disk) is almost full, it will struggle. Remove unnecessary files (for example old kernels), all old documents, downloaded iso files, whatever fills your hard disk drive. It may help you identify where to look for unnecessary files, if you run

```
baobab /
```

and use the whole screen for the pie diagram.

---

### Post by tgalati4 on 2015-06-02
Examine your RAM use during episodes of slowdown:

```
free
```

Both *firefox* and *google-chrome* use a lot of RAM with a lot of tabs open.  When you hit swap, your system will slow down to a crawl.

---

### Post by kazakore on 2015-06-03
> **sudodus said:**
> If the root partition '/' (the system disk) is almost full, it will struggle. Remove unnecessary files (for example old kernels), all old documents, downloaded iso files, whatever fills your hard disk drive. It may help you identify where to look for unnecessary files, if you run

```
baobab /
```

and use the whole screen for the pie diagram.

That's a new tool to me, thanks.

I don't use my root/home that much, I have a separate partition for all my data, and very rarely let / go below 15GB free space or so. Currently at 22.7GB free on root.

I do know that the slow down often (or rather used to only) occurs when my Rubbish Bin starts getting full and Data drive starts getting full. An empty of the Rubbish Bin used to bring it back up to good speeds pretty much without fail but it's lately started to be slow even after a cleanup (as I say mostly noticeable if reading and writing which is why I suspect the hdd. If I would have to guess I would say it's the seek time when moving the head where it struggles.)

> **tgalati4 said:**
> Examine your RAM use during episodes of slowdown:

```
free
```

Both *firefox* and *google-chrome* use a lot of RAM with a lot of tabs open.  When you hit swap, your system will slow down to a crawl.

Yeah I use free quite regularly. I have only ever seen my system using Swap once and typically have around 1.5GB of my 4GB free when I check... (Taking the minus buffers/cache number.)

---

### Post by sudodus on 2015-06-03
You can check the S.M.A.R.T. status of the hard disk drive. It is usually shown in a UEFI/BIOS menu, and also in the programs 'gnome-disks' in 14.04 LTS or newer or 'palimpsest' in 12.04 LTS. You get a more advanced tool, if you install ***smartmontools*** and run ```
sudo smartctl
```

Problems with the file system might be fixed with ***e2fsck*** (for linux ext file systems)
```
sudo e2fsck -f
```
and if you want to engage the ***badblocks*** program to mark bad blocks (to avoid searching them)
```
sudo e2fsck -cf
```

But I recommend that you replace the disk if the number of bad blocks is increasing.

---

### Post by kazakore on 2015-06-03
Ran the SMART included with the Lenovo Win7 install on the other partition I never wiped. Seemed very basic but came up clean.

Downloaded gnome-disk-utility and ran Extended SMART self-test from gnome-disks. Both seemed to pass OK. (I have to say the Gnome utility gives a lot more useful information than the Lenovo one!)

I have heard bad stories about badblocks and fsck if you don't know exactly what you are doing, ie recommendations to make sure to only run in analyse mode as they often do more damage than good if you try and repair with them. I will have a further look though, thanks. :)

---

### Post by kazakore on 2015-06-03
Although SMART entry 1.

Read Error Rate. Norm:113 Threshold:34 Worst:99 Status:OK
From that you would think it needs to go below 34 to hit the threshold and hit the alarm (which seems a weird way to work with error rate!)
But then a tooltip says "Frequency of errors while reading raw data from the disk. A non-zero value indicates a problem with either disk surface or read/write heads."
So why is that showing as OK?


EDIT1.

$ sudo e2fsck -fn /dev/sda5
e2fsck 1.42.9 (4-Feb-2014)
Warning!  /dev/sda5 is mounted.
Warning: skipping journal recovery because doing a read-only filesystem check.
Pass 1: Checking inodes, blocks, and sizes
Deleted inode 131077 has zero dtime.  Fix? no

Inodes that were part of a corrupted orphan linked list found.  Fix? no

Inode 1449859 was part of the orphaned inode list.  IGNORED.
Inode 1573005 was part of the orphaned inode list.  IGNORED.
Inode 3017924 was part of the orphaned inode list.  IGNORED.
Inode 3018038 was part of the orphaned inode list.  IGNORED.
Inode 3019645 was part of the orphaned inode list.  IGNORED.
Inode 3034648 was part of the orphaned inode list.  IGNORED.
Inode 3145933 was part of the orphaned inode list.  IGNORED.
Inode 3146750 was part of the orphaned inode list.  IGNORED.
Inode 3147505 was part of the orphaned inode list.  IGNORED.
Inode 3147695 was part of the orphaned inode list.  IGNORED.
Inode 3147798 was part of the orphaned inode list.  IGNORED.
Inode 3172627 was part of the orphaned inode list.  IGNORED.
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
Block bitmap differences:  -(10946560--10948607) -(10948704--10948725) -(10952704--10958034) -(10960896--10964991) -(12298998--12299000) -12616260 -(12710535--12710537) -12805129 -(12806145--12806146) -12822531 -(12827442--12827453) -12827657 -(12827951--12827959)
Fix? no

Free blocks count wrong (6335135, counted=6321955).
Fix? no

Inode bitmap differences:  -131077 -1449859 -1573005 -3017924 -3018038 -3019645 -3034648 -3145933 -3146750 -3147505 -3147695 -3147798 -3172627
Fix? no

Free inodes count wrong (3478302, counted=3477059).
Fix? no


/dev/sda5: ********** WARNING: Filesystem still has errors **********

/dev/sda5: 429282/3907584 files (0.7% non-contiguous), 9289376/15624511 blocks




Should I boot from a USB key so I can run it properly, rather than run it with the -n option? It cant be run on a mounted filesystem so obviously can't run it on root while using the computer...

---

### Post by sudodus on 2015-06-03
Yes, you should boot from another drive.

If the data on the current drive are very important, you should back it up before repairing. In that case I suggest that you use ***ddrescue***, that comes with the package **gddrescue**. The info page is very well written and helps understanding how to use ddrescue. I suggest that you try according to Examples 1 and 2. ddrescue can often read failing sectors (by re-reading rather than giving up as other tools do). So it is better than standard backup tools for failing drives (or in general, for drives with bad blocks).

```
info ddrescue
```

My experience is that e2fsck works well if the damage is not too big, but take care if there are important data.

---

### Post by james138 on 2015-06-03
I only skimmed through the thread, but in my experience your symptoms are indicative of the nearing death of your card. I could be wrong, but I'd recommend backing up all content and buying a replacement. You don't need to use it immediately, but I'd keep it close at hand.

How long have you had it for? Have you been using it regularly?

---

### Post by kazakore on 2015-06-03
> **sudodus said:**
> Yes, you should boot from another drive.


Sorry my question was more whether the errors in the above message look serious enough for it to be worth doing. My external is too full for me to easily back up everything I would want from my computer now. I think my plan of action is going to be to get a new 2TB drive, put then in my external caddy and replace my 300GB drive in the laptop with the 500GB one I am currently using as external storage. Once I find the time and money anyway... ;)


> **james138 said:**
> I only skimmed through the thread, but in my experience your symptoms are indicative of the nearing death of your card. I could be wrong, but I'd recommend backing up all content and buying a replacement. You don't need to use it immediately, but I'd keep it close at hand.

How long have you had it for? Have you been using it regularly?

Sorry we went rather off topic at some point, actually the same time as I marked the thread as Solved as the card started working as it should do. The card is less than a year old and has only been used in my camera and has never been completely filled (although I do delete from it when I move to the computer.) I have also been in Asia for the entire time, so heat, humidity and altitudes outside of what many would consider normal operation range. Still I think the card is OK but something odd was going on with my card reader in the laptop, which seems to have cured itself (possibly after an upgrade.) The reason I suspect this is "Unable to change permission" or similar messages when rsyncing to a MicroSD in adapter in the same slot previously. As I say seems to be working again now...

But I agree with you that I suspect my hdd is on its last legs! Which is what much of the thread ended up being about. Sorry for the side-track, I was contemplating starting a new thread but when people replied here to what was meant more as an off-hand comment I kept it going as it seemed to be nicely flowing. I know it's bad form but it's the most helpful replies I've had in a long time ;) (Thanks everybody.)

---

### Post by sudodus on 2015-06-03
That is a good plan. Be prepared that your HDD is getting tired. I think you should at least back up your most important files (if you haven't done it already). And when you have time and money, get a new big HDD ...

Anyway, you are welcome back to this thread, when you have hew questions to ask or new experiences to share :-)

---

