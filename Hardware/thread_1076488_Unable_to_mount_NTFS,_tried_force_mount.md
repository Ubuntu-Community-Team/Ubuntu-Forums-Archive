---
title: "Unable to mount NTFS, tried force mount"
date: 2009-02-21
forum: Hardware
---

### Post by LT.Was on 2009-02-21
When I tried to force mount my NTFS hard drive, I used:

sudo mkdir /media/disk
sudo mount -t ntfs-3g /dev/sdc1 /media/disk -o force

I got an error saying:

" Input/Output error NTFS is either inconsistent, or you have hardware faults, or you have SoftRAID/FakeRAID hardware. In the first case run chkdsk /f in Windows then reboot int Windows TWICE. The usage of the /f parameter is very important!
If you have SoftRAID/FakeRAID then you first must activate it and mount a different device under the /dev/mapper/directory. Please see the 'dmraid' documentation for details."

Anyone know what to do so I can see my files on the drive?

---

### Post by taurus on 2009-02-21
Aren't you able to boot your windows anymore on /dev/sdc1?

Some people have reported some success using TestDisk to fix that problem with ntfs filesystem.

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by LT.Was on 2009-02-21
The drive isn't my system drive (it's an external storage HD), but Windows recognizes it, but can't read any information off it. That's why I thought maybe Linux would be able to get the files off it.

---

### Post by caljohnsmith on 2009-02-21
Did you run "chkdsk" on it yet? That's probably the best place to start. You can do that by booting your Windows Install CD and going to the "recovery console", or you can do it within Windows by opening a "cmd" window, and then do:
```
map
```
That will show the drive letters of all the partitions, and then do:
```
chkdsk /r X:
```
And replace "X" with the drive letter of the partition in question. Let me know what that returns, and we can work from there if you want.

---

### Post by LT.Was on 2009-02-21
Ok, I'll run chkdsk on it now, and put out what it returns here soon.

---

### Post by LT.Was on 2009-02-22
I ran chkdsk twice, although I'm not sure if it completely finished either time. Both times it told me that the drive was NTFS, the volume name was 'ATTITUDE', and then it went forward to 'restore orphaned files' (a few of those), and then it said it fixed some 'clusters'. I think that it got stuck on the (5 out of 5) part. It said 0 percent completed for about an hour and a half, so I just exited. I'm not sure if this is normal or not.

---

### Post by caljohnsmith on 2009-02-22
So if you try and mount the partition again in Ubuntu, do you still get the same result as in your first post?

---

### Post by Tobi-fp on 2009-02-22
If i were you i would get myself a copy of hirens bootcd.. 
--> [www.Hiren.info](www.Hiren.info)

Then boot up in Mini xp or mini 95 or maybe just fix the system with other utilities..

Greets

---

### Post by LT.Was on 2009-02-22
Just tried mounting in Ubuntu again, and I received the same error message as before.

---

### Post by LT.Was on 2009-02-22
I guess I'll try some of Hirens system utilities now.

---

### Post by caljohnsmith on 2009-02-22
I would first give testdisk a try to see if it can help repair your NTFS partition:
```
sudo apt-get install testdisk
sudo testdisk /dev/sdc1
```
Choose "proceed", "none", "Advanced", "Boot", the "Rebuild BS"; if testdisk gives you a warning that the "Extrapolated boot sector and current boot sector are different", then choose "Write". After that, try mounting the sdc1 partition again and let me know what it says. If that doesn't work, go through the testdisk procedure again, but this time choose "Repair MFT" instead of "Rebuild BS". Then try mounting the the partition again and let me know what happens.

---

