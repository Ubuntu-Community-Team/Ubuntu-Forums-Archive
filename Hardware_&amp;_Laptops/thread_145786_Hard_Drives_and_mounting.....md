---
title: "Hard Drives and mounting...."
date: 2006-03-17
forum: Hardware &amp; Laptops
---

### Post by chopsbuntu on 2006-03-17
I've searched and searched on here, have seen similar problems, but not quite close enough to help at all, so...

One of my brothers has been having problems with his WinXP Pro machine for the last few days. The biggest problem that happened yesterday was that he had his PC on in the morning, checked his email, etc, etc and everything was fine, then shuts it off before leaving for work. He then comes home in the evening, turns the PC back on, goes to check his email only to find that the PC can't see the internet. It sees all the PCs on the network, but not the internet. So after he had me screwing around with it for about an hour last night, he asked me to just put Linux on it since he was fed-up with Windows... Who isn't these days?! :twisted: 

Anyway, he has his PC set up with two Seagate Baracuda 80GB SATA drives; one for the OS and the other for storage. I have since formatted and installed Ubuntu on the main drive, and since the storage drive was originally NTFS, we put the drive in my WinXP server PC, copied all of his files onto one of my drives, then deleted the partition since WinXP wouldn't allow me to format his drive to FAT anything, only back to NTFS... Damn Windows sucks! :evil: 

So now the drive is back in his Linux box, I used gparted and tried FAT32 and ext3. Either way, Ubuntu still sees it as NTFS, but gparted sees at as either FAT32 or ext3, depending on which way I have it formatted at that time.

No matter what I do, I cannot get Ubuntu to see that drive. On top of that, I do not know how to mount a drive anyway, but I'm not even worrying about that until I can get this drive seen by Ubuntu. 

I have been wracking my brain for the last couple of hours and have given up for the night. He just wants that drive on there so he can store his pictures and documents on it that he uses on a regular basis

**Can someone please help me out on this?** I can assure you that your help will be greatly appreciated by the both of us! Thanks. ;)

---

### Post by randal on 2006-03-17
Try looking in /dev.
There are some hdaN's (N = positive integer)
But I don't know how to pin point which one is which.

OR

try System >> Administration >> Disks
It will show all the secondary storage drives in your system and their partitions as well.

If you've successfully pinpoint which hdaN you want to mount:

sudo mount -t ntfs /dev/hdaN <some argument I forgot*>
*I think that argument is a directory that you need to address when you want to get to that drive.

I hope this helps. And I think after you shut down your system and log on again, you need to go through the same process to have that disk mounted.

---

### Post by aysiu on 2006-03-17
Can you post the output of these three commands? ```
sudo fdisk -l
df -h
cat /etc/fstab
```

---

### Post by chopsbuntu on 2006-03-17
Ok, here's everything I've got in this exact order...

1) System >> Administration >> Disks
2) Accessories >> System Tools >> GParted
3) sudo fdisk -l
4) df -h
5) cat /etc/fstab

---

### Post by chopsbuntu on 2006-03-17
Well, a little later this morning just for the heck of it, I tried running through GParted again and for whatever reason everything worked fine this time. The drive is mounted and is showing up as 74.3GB under Vfat. \\:D/ 

Don't ask me how or what I did differently, because as far as I know, I didn't do anything different from last night. My bro should be rather happy when he comes home tonight and sees everything working the way it should.

Thanks guys for everything! ;)

---

### Post by chopsbuntu on 2006-03-17
Alright, now there's a few new problems...

Issue 1) Is there a program similar to Windows Explorer where you can easily navigate through and view anything on either the main hard drive or the storage drive, and view them as thumbnails?

As of right now, the only way we can view anything on that storage drive is by going to "System >> Administration >> Disks", then once you put in your password, select that drive, click on "Partitions", then hit the browse button. I have to admit, doing it this way really sucks and it's pissing my brother off.

I cannot figure out how to make a shortcut of that drive to the desktop either. I'm guessing that storage drive really isn't "mounted"? What does that mean anyway?!

Issue 2) Earlier today when I was working on his computer, I was able to browse images and files on my WinXP server through the network on his Ubuntu computer. Now for whatever reason when he clicks on an image file off of my server, it says that it can not open that file type. They are just regular .jpg files like all the others, and they were working just fine earlier today.

What gives?!?! This crap is even starting to get to me, and I've been happy with Ubuntu on my two PCs for well over a month now. Plus with him giving me attitude over all of this isn't helping matters any either. :confused: :confused: :confused:

Again I ask, please help!

---

### Post by chopsbuntu on 2006-03-19
Anyone? Anything?

---

### Post by aysiu on 2006-03-19
Sorry. Somehow this thread got off my radar.

If both GParted and *sudo fdisk -l* say it's a Linux partition, I'm willing to go with it being a Linux partition. It's weird that Disks Manager sees it as NTFS.

Try this: ```
sudo umount /dev/sdb1
sudo mkdir /second_drive
sudo cp /etc/fstab /etc/fstab_backup
sudo nano /etc/fstab
``` Add in this line ```
/dev/sdb1 /second_drive ext3 defaults 0 0
``` Save (control-X), confirm (y), and Exit (Enter). Then ```
sudo mount -a
sudo chown -R chopsbuntu:chopsbuntu /second_drive
sudo chmod -R 775 /second_drive
``` Then go to the folder called /second_drive and see if you can go in.

If that doesn't work, try ```
sudo umount /dev/sdb1
sudo nano /etc/fstab
``` and change ```
/dev/sdb1 /second_drive ext3 defaults 0 0
``` to ```
/dev/sdb1 /second_drive ntfs nls=utf8,umask=0222 0 0
``` Save, confirm, and exit. ```
sudo mount -a
```

---

### Post by chopsbuntu on 2006-03-20
Hi aysiu!

I tried the codes you posted, and it did create a fold that I was able to go into, but it is empty.

I did do all of this within KDE. Would it make any difference if I am using the terminal in KDE or Gnome while performing the steps you posted above?

BTW, I think it is now being seen as a Linux partition in one place and vfat in another now.

Thanks! I really appreciate your help on all of this. ;)

---

### Post by aysiu on 2006-03-20
[QUOTE=chopsbuntu]Hi aysiu!

I tried the codes you posted, and it did create a fold that I was able to go into, but it is empty.

I did do all of this within KDE. Would it make any difference if I am using the terminal in KDE or Gnome while performing the steps you posted above?

BTW, I think it is now being seen as a Linux partition in one place and vfat in another now.

Thanks! I really appreciate your help on all of this. ;)[/QUOTE] It shouldn't matter whether it's KDE or Gnome. I'm not sure I can help you at this point, since your computer doesn't seem to know what filesystem the drive uses...

---

### Post by chopsbuntu on 2006-03-20
Do you have any idea [U]why[U] Ubuntu is seeing the drive as two different types?

The drive was completely wiped clean, I'm sure of that.

---

### Post by chopsbuntu on 2006-03-22
So that's it?! I guess I'm up $h!t creek then, huh?

Whatever. :evil:

---

### Post by theanorak on 2006-03-22
Let me just check:

you blanked the storage drive and created a new partition, yes? Did you set the partition type to FAT/FAT32/vfat (can't remember what the option is) when you did so?

Then, presumably, you formatted it with fat 32 - this might work:

mkfs.vfat -F 32 /dev/your-drive-here

To make it easily available you need to mount it somewhere on the filesystem. You can choose where you'd like to mount it. Perhaps create a folder off / called "storagedrive" or whatever. Then edit your fstab to mount on startup.

---

