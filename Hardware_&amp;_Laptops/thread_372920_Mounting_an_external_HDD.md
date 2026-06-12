---
title: "Mounting an external HDD"
date: 2007-02-28
forum: Hardware &amp; Laptops
---

### Post by Cloudy on 2007-02-28
So last night I bought a small, 40GB external HDD to use with my laptop and following this guide ( [http://www.netshiftmedia.com/netshift/archives/2006/09/15/mounting-external-usb-drive-linux.php](http://www.netshiftmedia.com/netshift/archives/2006/09/15/mounting-external-usb-drive-linux.php) ), I did the df command:

```

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/hda1             18414092   4096100  13382612  24% /
varrun                  257908       112    257796   1% /var/run
varlock                 257908         0    257908   0% /var/lock
procbususb               10240        84     10156   1% /proc/bus/usb
udev                     10240        84     10156   1% /dev
devshm                  257908         0    257908   0% /dev/shm
lrm                     257908     17580    240328   7% /lib/modules/2.6.17-11-g

```

So, I'm lost.. which one of those would be my USB HDD? The guide says sda1 is what it's usually mounted as..

Maybe I've got it plugged in wrong, I don't know. There are two USB connectors and I have them both plugged into my USB hub, like I assumed they should be. The red drive light on the external HDD is on, though..

I wish this came with some form of instructions, even for Windows. Bleh.

---

### Post by mac.ryan on 2007-02-28
What I did for my external HD was this:

1. Install gparted from synaptics
2. Use gparted to buldoze the NTFS pre-installed partition
3. Partition and format of the HD they way I wanted

And then it worked "out of the box". The thing I didn't investigated too much is how to rename the disk. Now all of my external HDs are called "usbdisk" (/dev/usbdisk).

Hope this helps...

EDIT: In fact, my HD automounted by default as soon as I plugged it. i have Edgy and a 120 Gb LaCie + 80 Gb Western Digital...

---

### Post by Cloudy on 2007-02-28
> **mac.ryan said:**
> What I did for my external HD was this:

1. Install gparted from synaptics
2. Use gparted to buldoze the NTFS pre-installed partition
3. Partition and format of the HD they way I wanted

And then it worked "out of the box". The thing I didn't investigated too much is how to rename the disk. Now all of my external HDs are called "usbdisk" (/dev/usbdisk).

Hope this helps...

so will it only mount if the filesystem on the USB HDD is ext3 or ext2? I'm confused. I don't think the drive is showing up at all, as evidenced by my df output.

---

### Post by mac.ryan on 2007-02-28
> **Cloudy said:**
> so will it only mount if the filesystem on the USB HDD is ext3 or ext2?

No, it should do it with FAT or NTFS as well. The point is: if your HD is not formatted yet, it can't be mounted. Not knowing what your situation exactly is I just thought to share what my noob experience was...

The bottom line is that if you are using Edgy, and there is a known file system on the disk, the device should be recognised automatically, without having to manually mount it.

> I'm confused. I don't think the drive is showing up at all, as evidenced by my df output.

I am not a linux-guru, but my understanding is the df only works on mounted drives. If you want to see if your external usb drive is "seen" (although not necessarily mounted), I would suggest to see if there is any change in the /dev directory before and after you plug the device in (if the device is seen, a new corresponding directory should be created).

The only other thing I can think of, is that your bios might limit the amount of power on the USB, so that your HD is not powered enough to work properly, or more banally, a damaged USB cable.

---

### Post by Cloudy on 2007-02-28
Alright, thank you. I'm gonna try what you said and report back.

---

### Post by Cloudy on 2007-03-01
Weird.

For whatever reason, the drive will only be recognized if it's plugged directly into the laptop, but not into the USB hub..

---

### Post by mac.ryan on 2007-03-01
Ah-ah... I saw that happening under Windows too... Somebody told me that it depend from the hubs, namely the way they manage the USB 2.0 features, but this is second hand information...

Happy you fixed it though! :)

---

