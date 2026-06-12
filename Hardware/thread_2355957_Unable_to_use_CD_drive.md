---
title: "Unable to use CD drive"
date: 2017-03-18
forum: Hardware
---

### Post by boxcorner on 2017-03-18
Hello
Could one of the clever people here help me, please?
Since changing from Ubuntu to Kubuntu, I have been unable to use the CD drive in my Lenovo Z570 laptop.
While I noticed this problem a while ago, I have procrastinated doing anything about it because I rarely use it. 
Now I need to use it, it's become a more pressing problem.
The drive opens and closes okay, without any difficulty.
After closing the drive, I can hear a whirring sound, so it appears to be running.
What I have tried : 
File manager Dolphin > Devices (only the hard drive is listed)
Settings > System > Hardware 
here I'm stuck because I don't see anything that looks like a CD drive listed, either in the Driver Manager, nor under Removable Devices
What do I need to do to get Kubuntu to recognize the CD drive?
How what do I have to do to get it mounted automatically, whenever I boot my laptop?

---

### Post by cariboo on 2017-03-18
First you should see if the system is actually detecting the disk in the drive. Run dmesg, and you should see something similar to this:

```
[ 9802.577936] ISO 9660 Extensions: Microsoft Joliet Level 3
[ 9802.621290] ISO 9660 Extensions: RRIP_1991A
```

---

### Post by boxcorner on 2017-03-25
Many thanks for your reply.
When I ran dmesg I was surprised by the length of the output, so won't post it here in case I infringe some rule. 
I've scrolled up and down, through the output and cannot see anything that begins with ISO 9660

---

### Post by RobGoss on 2017-03-25
Hello and welcome, You can post the results for output using the **code tags,** place your codes between the code tags. Please see this help page for guidance [https://ubuntuforums.org/showthread.php?t=2171721](https://ubuntuforums.org/showthread.php?t=2171721)

---

### Post by him610 on 2017-03-25
this command line utility will show a nice summary of your drives...
```
inxi -d
```

---

### Post by boxcorner on 2017-04-03
Thank you

---

### Post by boxcorner on 2017-04-03
Thank you
```

rdh@rdh-Ideapad-Z570:~$ inxi -d
Drives:    HDD Total Size: 750.2GB (58.7% used) ID-1: /dev/sda model: WDC_WD7500BPVT size: 750.2GB
           Optical: /dev/sr0 model: MATSHITA DVD-RAM UJ8B1AS dev-links: cdrom,cdrw,dvd,dvdrw
           Features: speed: 24x multisession: yes audio: yes dvd: yes rw: cd-r,cd-rw,dvd-r,dvd-ram
rdh@rdh-Ideapad-Z570:~$ 

```
Whilst the drive is included above, from Dolphin all I see are two hard drives.
I don't understand why the drive isn't listed under 'Devices' in Dolphin.

---

### Post by boxcorner on 2017-05-20
I still have this problem:

the CD drive in my laptop does not appear in Dolphin
```

rdh@rdh-Ideapad-Z570:~$ sudo cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/mapper/kubuntu--vg-root /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=828f6d27-5236-4341-bc58-99e41f70f90b /boot           ext2    defaults        0       2
/dev/mapper/kubuntu--vg-swap_1 none            swap    sw              0       0
/dev/disk/by-id/ata-MATSHITADVD-RAM_UJ8B1AS_SCB1526631 /mnt/ata-MATSHITADVD-RAM_UJ8B1AS_SCB1526631 auto nosuid,nodev,nofail,x-gvfs-show 0 0
rdh@rdh-Ideapad-Z570:~$ 

```
ata-MATSHITADVD-RAM_UJ8B1AS_SCB152631

What do I need to do to able to use the drive in Kubuntu?

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
[B]
Ok, I managed to get it working
[/B]
This is what I did :
I Googled "how to play dvd in kubuntu"
Then I visited
[https://itsfoss.com/play-dvd-ubuntu-1310/](https://itsfoss.com/play-dvd-ubuntu-1310/)
followed the instructions 
now it works
hope this helps someone else ...

[B]Aarrgh ! 
I spoke too soon
[/B]After rebooting my laptop, when I try to open a DVD in VLC 
I get :
  [COLOR=#ff0000]Playback failure:[/COLOR]
 [COLOR=#000000]DVDRead could not open the disc "/dev/sr0".[/COLOR]
 [COLOR=#ff0000]Your input can't be opened:[/COLOR]
 [COLOR=#000000]VLC is unable to open the MRL 'dvd:///dev/sr0'. Check the log for details.
So, now I'm stuck again.
Any help would be much appreciated.
[/COLOR]

---

