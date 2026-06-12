---
title: "Ubuntu 8.10 installed---GRUB not working!"
date: 2008-11-28
forum: General Help
---

### Post by lu6cifer on 2008-11-28
I just installed Ubuntu 8.10--The partition is there (Checked w/ a livecd), but GRUB isn't coming up. I went to the GRUB help site and followed the commands, but they didn't work either....

Any ideas?

---

### Post by pumkinut on 2008-11-28
A listing of what you actually did from the GRUB webiste would help.  Also, where did you install GRUB?  Was it to the MBR or the HDD or to the /boot directory/partition?  It makes a difference.

---

### Post by lu6cifer on 2008-11-28
I followed the instructions here (The Quickstart):
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#Quick%20Start](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#Quick%20Start)

But when I tried to find GRUB, it said something like "Error 15: File not found" (even after the second command it suggested) 


I thought GRUB just came with Ubuntu? I haven't tried installing it to the MBR yet--how would I do that?

---

### Post by lu6cifer on 2008-11-28
I was installing Ubuntu on my laptop---The partition is there (I checked with gparted), but when I reboot, GRUB is not there. I looked on some help guides, and they told me to type things like, "find /boot/grub/stage1" but all that came up with was "Error 15: file not found" I tried, root (hd0, 5) (the drive/partition that ubuntu is on) but it told that the partition or something doesn't exist.

Lastly, I tried removing the ubuntu ext3 partition with Livecd and Gparted, but it said I had to unmount all logical partitions higher than 6, or something like that---All partitions were definitely unmounted when I did this..


Any ideas on how to reinstall GRUB or how to delete the ubuntu partition?

---

### Post by bapoumba on 2008-11-28
Threads merged.

---

