---
title: "external harddrive automounts 2nd partition for root only"
date: 2007-01-15
forum: Hardware &amp; Laptops
---

### Post by danomatika on 2007-01-15
Ok, so this is a not a HUUUUUGE problem, but I'd figure I would ask ...

I have an external harddrive with 2 partitions. All partitions mount fine in Ubuntu, windows, and mac, nothing wrong with the drives, etc.

Just a small annoyance in that the second partition of the drive automounts for root only.  What I mean is, the drive /media folders' permissions are set only for root.  Obviously, this is annoying to have a nice drive icon appear that you cant write to!

I know the first thing that will be said "well just make a line in the fstab and be done with it".  Yeah I could buuuuuuut I don't want to ... I dont want to have to assign it a dev node when I am sure to plug things in to diff usb ports or use the firewire on it.  I have a second external with one partition that works fine and I dont want any crosstalk.

I have tried formatting it as fat32, ext3, and reiserfs and the same thing happens each time.  Originally, the drive was setup using partition magic in windows.  Now that old billy gates and software have been eradicated, I formatted the second partition as resier and this showed up.  Perhaps when I ran gparted it screwed up the partition table some how as it mentioned something about writing to the partiton table .. blahh I don't remember exactly now.

I have about 80 GB I can move off the first partiton to my second drive and try repartition the whole shebang with gparted, but I have a feeling that wouldn't solve this.

So my question is: did I partition the drive incorrectly?  has anyone else noticed this? and of course, is there an easy magic-bullet to it or do I have to write some udev rules (I can but I feel like I shouldn't have to).

I'm not trying to be cocky, just figure that since Ubuntu is already setup so nicely, fixing this instead of writing a static fstab entry would be more useful in the long run.

Cheers

---

### Post by danomatika on 2007-01-17
yeah, so i feel kind of stupid, but it works fine now for some reason.  Both partitions mount for my username.

---

