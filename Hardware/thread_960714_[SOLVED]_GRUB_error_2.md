---
title: "[SOLVED] GRUB error 2"
date: 2008-10-27
forum: Hardware
---

### Post by jimbob on 2008-10-27
I believe this to be a hardware problem and not specific to Ubuntu so I hope this is the right place to put it.

My problem occurs when trying to boot the first partition on the IDE drive from the SATA drive. GRUB actually fails to recognize the first partition on IDE at all. Booting SATA from IDE works just fine as does booting either drive from a USB dongle. I have tried all the fixes and none work for me.

My BIOS only allows DMA to be enabled or disabled for my drives (it contains nothing about UDMA) and does not seem to change anything.

I have also tried hdparm -d0 /dev/sdx or hdx which only throws off an IOCTL error.

Also adding ide=nodma and nohdparm and all_generic_ide on the kernel line at boot makes no difference.

Hardware:  Gigabyte GA-K8NS (Rev 2.x) nForce3 250 chipset mother board with
Award Bios firmware Ver. F19

I'm about Googled out so any suggestions would be welcome.

---

### Post by phidia on 2008-10-27
Have you tried the [grub super disk]("http://www.supergrubdisk.org/")  
Also look at the grub restore procedure [here]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows").

If that's not helpful then post the output of "sudo fdisk -l".

---

### Post by caljohnsmith on 2008-10-27
For whichever linux distro you have installed on your SATA drive that controls Grub on that drive, how about booting into it and posting:
```
sudo fdisk -lu
cat /boot/grub/menu.lst
```
And let us know what your partitions are if it is not clear.

---

### Post by jimbob on 2008-10-28
Thanks for the replies.  Here are the outputs requested:

---

### Post by caljohnsmith on 2008-10-28
OK, it looks like you have at least two problems that I could find; you have Intrepid installed to hda1, and the new Intrepid release defaults to using a 256 byte inode size for its ext3 file system rather than the older 128 bytes used in Hardy and in prior releases. Unfortunately the Grub version in Hardy and before can't handle the larger inode size, so you will typically get a Grub error 2 if you try to boot one of the newer ext3 partitions. Also, the other problem I think is:
```
title  Ubuntu Intrepid beta on HDA1, kernel 2.6.27-7-generic
root   (hd1,0)
kernel  /boot/vmlinuz-2.6.27-7-generic root=[COLOR="Red"]/dev/sda1[/COLOR] ro quiet splash
initrd  /boot/initrd.img-2.6.27-7-generic
quiet
```
The above should be /dev/hda1 instead of sda1, and that will only work if you have hda mapped to (hd1) in Grub's /boot/grub/device.map file. Personally, I would highly recommend using the UUID for the Intrepid partition instead, similar to the way you have it in your Feisty entry. 

If you want to be able to boot Intrepid from your SATA drive, you could go to packages.ubuntu.com and download the Intrepid version of Grub (0.97-29ubuntu45), and install that to Ubuntu on your SATA drive. That should allow you to access Intrepid. If you download the new Grub package to your desktop, just install it with:
```

sudo apt-get purge grub
sudo dpkg -i ~/Desktop/grub*.deb
sudo grub-install /dev/sda
```
I think that should be all it takes to boot Intrepid, but let me know how it goes. :)

---

### Post by jimbob on 2008-10-28
Thanks but the new grub has too many dependencies to install.

```
root@G-beta:/home/jaspmatt# dpkg -i /home/jaspmatt/Desktop/grub*.deb
Selecting previously deselected package grub.
(Reading database ... 148103 files and directories currently installed.)
Unpacking grub (from .../grub_0.97-29ubuntu45_i386.deb) ...
dpkg: dependency problems prevent configuration of grub:
 grub depends on libncurses5 (>= 5.6+20071006-3); however:
  Version of libncurses5 on system is 5.6+20070716-1ubuntu3.
 grub depends on udev (>= 117-5); however:
  Version of udev on system is 113-0ubuntu17.
 grub depends on ucf (>= 3.004-0ubuntu2); however:
  Version of ucf on system is 3.001.
 grub depends on debconf (>= 1.5.19) | cdebconf; however:
  Version of debconf on system is 1.5.14ubuntu1.
  Package cdebconf is not installed.
dpkg: error processing grub (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 grub

```

It is gratifying however to know what the problem is with the inode thing.
I'm surprised that more users haven't encountered it.

I had already tried replacing /dev/sda1 with /dev/hda1 and that made no difference.  It worked interchangeably with the Hardy installation on sda3/hda3 however so I became convinced it was something else.

---

### Post by caljohnsmith on 2008-10-28
I guess I'm not too surprised to see that the new Grub has a bunch of Intrepid package dependencies that prevented you from installing it; but if I'm not mistaken, really the only thing you need from that new Grub package is the newer version of the Grub stage1, stage1.5, and stage2 files. Those are the files that would make it possible to access the newer ext3 partitions. 

If you want to give it a try, we could install just the newer boot files, and I'll bet that would be all it takes to boot Intrepid from your older Ubuntu on the SATA drive. It wouldn't hurt to try, because you could easily go back to the older files if for some reason it doesn't work. It's up to you if you want to give it a shot, and I think there is a high likelihood of it working. Let me know if you're interested. :)

---

### Post by jimbob on 2008-10-29
Yes, I am definitely interested but not quite sure how to proceed.

Can I somehow get the new grub off the Intrepid CD?

---

### Post by caljohnsmith on 2008-10-29
I don't have the new Intrepid CD yet, but I looked through my Hardy CD and couldn't find those Grub files anywhere; so I assume the Intrepid CD is the same. Yet obviously they have to be on the CD when Grub gets installed, but they just may be compressed or something like that I assume. So instead of using the Intrepid CD, with the Intrepid Grub package on your desktop still, do the following:
```
cd ~/Desktop
mkdir New_grub
dpkg-deb -x grub*.deb New_grub
sudo mkdir /boot/grub/backup
gksudo nautilus &
```
With the file browser that comes up with that last command, please move the following two files from the /boot/grub folder into the /boot/grub/backup folder:
```

e2fs_stage1_5
stage2
```
Next go to the your Desktop in the file browser, and navigate to the following folder (assumes you are using the i386 version):
```
New_grub/usr/lib/grub/i386-pc/
```
Then copy the e2fs_stage1_5 and stage2 files from the New_grub directory above and paste them into your /boot/grub directory. Next reinstall Grub with:
```
sudo grub
grub> device (hd0) /dev/sda
grub> root (hd0,0)
grub> setup (hd0)
grub> quit
```
And please post the output of all the above commands. If everything went smooth with no errors, go ahead and reboot, and let me know if you still get the error 2 when booting Intrepid (hopefully not). :)

---

### Post by jimbob on 2008-10-30
I got all wrapped around the axle trying to use nautilus as per your procedure so I'm just going to do it via the command line.   Nautilus complains that I don't have permission to copy into the grub folder.

Anyhow without any mods the existing grub now shows this- 

```
grub> find /boot/grub/stage1
 (hd0,0)
 (hd0,3)
 (hd1,0)
 (hd1,2)
 (hd1,3)

```

The partition I'm on now is recognized as (hd1,2) so shouldn't your code read thus?

```
sudo grub
grub> device (hd1) /dev/sda
grub> root (hd1,2)
grub> setup (hd1)
grub> quit
```

---

### Post by caljohnsmith on 2008-10-30
OK, when you say you are in (hd1,2), is that your Gutsy install on sda3? Are you sure that is the one that controls Grub in the MBR of sda? How about first running:
```
sudo dd if=/dev/sda bs=1 skip=1049 count=2 2>/dev/null | hexdump
```
That should return "ff02" if your sda3 gutsy install controls Grub. If it does return "ff02", then yes, proceed with those Grub commands exactly as you have them written. :)

---

### Post by jimbob on 2008-10-30
caljohnsmith you're a genius !! 

Everything works great.  Thank you again.

---

### Post by caljohnsmith on 2008-10-30
That's great news, jimbob; I'm glad our experiment worked. Cheers and have fun Ubuntu-ing. :)

---

