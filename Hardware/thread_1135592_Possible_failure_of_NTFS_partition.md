---
title: "Possible failure of NTFS partition"
date: 2009-04-24
forum: Hardware
---

### Post by Cmndr Hippofiralkus on 2009-04-24
I'll jump straight into this problem, so please bear with me :P

I've been given a faulty hard drive that has enough valuable data on it to sink a ship but, surprisingly, it isn't working.

1) It is viewable on the bios, seen during start up, and Smart check says it's all tickety boo.

2) Windows Vista however doesn't see it at all, not in the Computer window or in the storage manager.

3) Seeing as how I kiss the ground Ubuntu walks on, I immediately booted into it and tried to mount the drive, and it did give me a little information, but not very much (Just an error message really, but that's better than nothing).

I'll post what the message is Ubuntu chucks up is in a moment, i'm using Windows at the moment.


Thanks to all who may/may not help!

---

### Post by jamessnell on 2009-04-24
First rule of forensics, try your damnest to not change the state of the thing you're working on.

I'd start by using dd to try to grab every byte off the drive in question. If you can resolve the file system error on the file you get out of dd, then maybe consider trying the same fix on the drive.. If the issue is degenerative, then each time you try something on the drive, you may be making it worse, so at least if you're doing a dd, it'll store whatever you get out there and then. Of course, you'll still have a big mess as you'll then need to figure out how to get the data, but at least the data shouldn't be changing at that point.

I wonder what gparted would show you for that drive? Do you see partitions listed as you'd expect? (You could also use fdisk for that).

---

### Post by Cmndr Hippofiralkus on 2009-04-24
I don't think the issue is mechanical degenerative, more along the lines of something codey wodey side like the boot sector or partition tables. 
Unfortunately i'm having difficulties getting Ubuntu running which I will stick my hand up and admit was "my own dumb fault". I have however managed to boot of the livecd and the partition tables seem intact, I just can't mount the drive.

---

### Post by jamessnell on 2009-04-24
Well, there has got to a number of decent tools out there to help correct relatively minor corruptions.. I'd suggest you either keep fishing on the forum and see if someone who knows off the top of their head stumbles on your post, or you can always google the crud outta the subject.

Good luck, I hope you find a simple solution soon! That does suck.

---

