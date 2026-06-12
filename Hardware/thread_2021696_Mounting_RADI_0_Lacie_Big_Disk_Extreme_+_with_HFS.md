---
title: "Mounting RADI 0 Lacie Big Disk Extreme + with HFS"
date: 2012-07-09
forum: Hardware
---

### Post by Zaff on 2012-07-09
Hi guys,
I've posted this in the Mac User section at first but no one seems to know the answer so I'm giving it a shot here. My problem is pretty specific so I haven't been able to find a lot of information on the subject.

I have a LaCie Big Disk Extreme + 1To external hard drive. It's been formatted in Mac with the HFS + File system. This drive is actually 2 different 500 Go HDs in a case set up in RAID 0 for better performances.
Now the problem is that the case seems to be defective because the drive is not being detected when plugged in. So I opened it (the warranty has been void for a while now) and I plugged both disks directly into my computer.

Now using the following command line I was able to recreate the RAID 0 array (as far as I can tell anyway).

```
sudo mdadm -B  -c 256 -l 0 -n2 /dev/md0 /dev/sdc /dev/sdb

```

I can see the disk in nautilus, it's even named My Book 2 and is a 1To disk so that leads me to believe that the RAID is correct. However I can't seem to be able to mount it. I've installed hfsplus hfsutils and hfsprogs but it still won't mount.
The mount command returns a "device is busy" error.

Can anyone tell me what I can do to try and solve the problem ? There is a lot of data on this disk and it would be nice if I could get it back.
Is there a way to see if the problem is with the way I set up the RAID array or if it's something else ? 

Thanks in advance !

---

