---
title: "Jaunty 9.04 won't install on Dell Inspiron 3700"
date: 2009-06-22
forum: Installation &amp; Upgrades
---

### Post by 1915flyer on 2009-06-22
Dell Inspiron 3700, 450Mhz, 512M memory, 20MB hard drive, CD, etc.

Hardy 8.10 installed with no problems and works fine. I cannot get Jaunty 9.04 to install or run the live CD. 

I first tried upgrade from 8.04 and that didn't work. Then the live CD install, then the alternate CD. Once the install worked, but when I rebooted, it never got to the login, bailing out of graphics mode to the black screen/white text.

When it crashes, the display usually shows Segmentation Faults, sometimes many, many of them. Several times it gets to the point where it has loaded the kernel modules OK, but never progresses after starting to load manual drivers.

I've tried turning off serial and parallel ports in the bios. Progress seems to go further then, but I still get the terminations or hangs.

Some of the fault messages (pretty close anyway):
rm: cannot remove /tmp/.clean
mkdir: cannot create dir /temp/.X11-unix
init: rc-default main process (1370), terminated with status 139
udevd-event[1174] path_id/devices/platform/pcspkr/input/input2/event2 abnormal exit

Where to go from here, or is it hopeless? Thanks for any help.

---

### Post by 1915flyer on 2009-06-24
Knoppix 6.0 live CD won't run either. It looks for /dev/hda and doesn't find it, looks for USB and then goes to debug mode. I assume for some reason it can't find or continue with the CD either. It must be able to read it at first because it starts loading. 

I'm running the same Knoppix live CD on a different computer to post this.

Looks hopeless for an upgrade from Ubuntu 8.10 for the Inspiron.

---

### Post by chris1972 on 2009-07-14
Hi,

I have exactly the same Dell Inspiron 3700 laptop and had exactly the same problem, with the progress bar just stopping or hanging during boot-up, segmentation faults and getting errors like
```
init: rc-default main process (1576) terminated with status 139
```
```
udevd-event [931]: '/sbin/modprobe -b pci:v00001179d000...' ... abnormal exit
```
```
rm: cannot remove '.tmp/.clean': read-only file system

```
I came across this thread which provided a workaround.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/357724]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/357724")

So, I modified /etc/modprobe.d/blacklist.conf adding the line
```
blacklist radio_maestro
```

and now I can boot just fine.

I think that this module is required by our sound cards so will have to be loaded manually once ubuntu is started.  e.g.
```
root# modprobe radio_maestro
```
But, hopefully this is just an interim workaround until the 2.6.30 kernel is released.

Other laptops seem to suffer from the same problem
Compaq Armada E500
Compaq Armada M700
Toshiba Satellite 4100XCDT

Best Regards,
Chris

---

### Post by 1915flyer on 2009-07-14
Thanks for the information about the hardware problems.

So far, I've only gotten to a full installation one time out of about 10 attempts, and it wouldn't boot after that - just a crash. I don't remember whether this was with the LiveCD or the alternate CD.

I don't understand how to blacklist anything unless I can get something to install in the first place.

Very much of a noob on this.

Tyler

---

### Post by chris1972 on 2009-07-14
Hi Tyler,

I'm assuming that you have 9.04 Ubuntu installed on your hard-drive from the alternate CD but just cannot boot into it.

You should, however, be able to boot into Intrepid using your old Ubuntu 8.10 LiveCD.  This will allow you to access your Jaunty file-system on the hard-disk (if you configured your Jaunty filesystem as the default which is ext3).

Once booted into 8.10, open a terminal window, and first check which partition you've installed 9.04 on.  For me, the device I installed on was /dev/sda1 but you may have something else.
```
sudo fdisk -l

Disk /dev/sda: 4871 MB, 4871301120 bytes
255 heads, 63 sectors/track, 592 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000686ae

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         529     4249161   83  Linux
/dev/sda2             530         592      506047+  82  Linux swap / Solaris
```

Mount the filesystem, being careful to replace /dev/sda1 with the device you installed to.
```
sudo mkdir /mnt/jaunty
sudo mount -t ext3 /dev/sda1 /mnt/jaunty
```

Change directory to modprobe.d
```
cd /mnt/jaunty
cd etc
cd modprobe.d
```

Take a back up of the blacklist.conf file and then edit it
```
sudo cp blacklist.conf blacklist.conf.bak
sudo nano blacklist.conf
```
In nano, you can use the arrow keys to move around.  <Ctrl>o will save and <Ctrl>x will exit.

Once in nano, add a new line to blacklist.conf with the following text.
```
blacklist radio_maestro
```

When the file is saved, shutdown and remove the 8.10 CD and you should be able to power-on and boot into 9.04 Jaunty.

I had my Jaunty filesystem configured as the non-default ext4 which isn't compatible with the Ubuntu 8.10 LiveCD, so I ended up downloading and burning the LiveCD from sysresccd.org which does have ext4 support.  I then did a similar set of steps to above ( but without the sudo because it logged me in as root already), and specifying ext4 in the mount command.

In jaunty, everything seems to work fine (including sound), so I'm not sure what the radio_maestro is used for anyway.  If you do find you need it, you can always load it manually
```
sudo modprobe radio_maestro
```

Hope this works for you. 

Best Regards,
Chris

---

### Post by 1915flyer on 2009-07-17
At last, it works!

I must have done something wrong the first time as I had to go into recovery mode to boot at first. Then there were some issues with shutting down completely.

Second install worked perfectly. Many thanks for the help. :popcorn:

Tyler

---

