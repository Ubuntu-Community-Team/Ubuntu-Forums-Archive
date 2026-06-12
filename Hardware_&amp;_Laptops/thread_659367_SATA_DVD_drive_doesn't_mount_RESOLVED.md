---
title: "SATA DVD drive doesn't mount RESOLVED"
date: 2008-01-05
forum: Hardware &amp; Laptops
---

### Post by richbl on 2008-01-05
Hello all,

I just ran into an odd situation with my Samsung SH-183L DVD-DL SATA drive. For some reason, Ubuntu (Gutsy) was unable to mount the drive. Since I rarely use this drive, it's possible that it never was correctly identified when I did a clean install (from Feisty to Gutsy).

That said, I have managed to resolve my particular situation. The drive is now functioning exactly as expected.

For others who might find themselves in the same situation, here's a quick procedure that I followed. I hope it helps:

0) Initially, when inserting any disk (CD or DVD), I would get a response from Ubuntu that indicated that the drive could not read the disk. The error read something like "cannot mount volume" with some additional information that "mount point /media/cdrom0 does not exist."

Since I'm fairly new to how Linux handles the mount/unmount of devices, I was clueless.

1) Some searching on the net suggested that I install hwinfo. Good idea. Through Synaptics Package Manager, I installed this little command-line application. What it does is identify all hardware that has been found on your system (similar to Device Manager in Windows).

2) Running hwinfo correctly identified my particular DVD drive as TSSTcorp CD/DVDW SH-S183L, which is correct (TSSTcorp is Samsung in this case). Here's a segment of the output from hwinfo:

```
disk:
  /dev/sda             ST3320620AS
partition:
  /dev/sda1            Partition
  /dev/sda2            Partition
  /dev/sda5            Partition
cdrom:
  /dev/sr0             TSSTcorp CD/DVDW SH-S183L
```
What's interesting to note is that the DVD drive is located at /dev/sr0. Remember this little bit of info.

3) Another new file that I learned about was fstab, located in /etc/fstab. This file, as I understand it, associates devices (in this case, my DVD drive, /dev/sr0) with mount points (/media/cdrom0, the location that Ubuntu was complaining didn't exist). A quick peek at /etc/fstab is below:
```

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
```
Hmmm... now that's interesting. According to what I see in /etc/fstab, Ubuntu is trying to associate /dev/scd0 with the mount point /media/cdrom0. But wait! According to hwinfo, there is no /dev/scd0, instead there's /dev/sr0. Very interesting!

4) So, I'm guessing that this is the problem: I stick a disk in my DVD drive, Ubuntu gets a message that it needs to read the disk, and looks for /dev/scd0. It doesn't exist. That's not good.

5) How to resolve this problem? Edit /etc/fstab is needed. After the edit to the relevant section, here's the updated /etc/fstab entry:

```
#/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/sr0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
```
Notice that I just commented out the original line (just in case I was way off base, I can always go back and uncomment the original line). What I've added is the information that I received when I ran hwinfo. That is, that my DVD drive is really identified as /dev/sr0, not /dev/scd0, as the original /etc/fstab was showing.

6) So far, so good. One more tiny problem: the mount point /media/cdrom0 doesn't exist either. In Linux, a mount point is just a directory (folder) that's created so it's easy to navigate the contents of that device. Since /media/cdrom0 is a directory, I should be able to navigate to it in a terminal (command-line) window. Sure enough, as I suspected, once in /media, there's no /cdrom0 directory. By creating this folder (mkdir cdrom0), I should be good to go.

7) Time to reboot. I'm not sure if I really need to reboot, but all of these years running Windows has me conditioned to reboot whenever I make changes to the system.

8) Once rebooted, inserting a disk into the DVD drive and... success. The drive correctly mounts, and I'm up and running.

If I'm way out of line on my approach or understanding of what happened, and how I resolved this problem (or if there's a better solution entirely), please let me know.

Thanks.

---

