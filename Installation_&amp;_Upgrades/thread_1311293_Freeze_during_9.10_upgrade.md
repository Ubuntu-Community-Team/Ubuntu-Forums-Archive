---
title: "Freeze during 9.10 upgrade"
date: 2009-11-02
forum: Installation &amp; Upgrades
---

### Post by g-raf on 2009-11-02
Now i'm computerless, using my friends computer to post. I tried to upgrade to ubuntu studio 9.10 using the update manager and the computer froze halfway through installation. I thought it was going to be a smooth upgrade, but it was my stupid mistake for assuming that. Now my computer doesn't boot...i can't even boot the recovery kernels. Instead, during the boot, i get this:

One or more of the mounts listed in /etc/fstab cannot yet be mounted:
(ESC for recovery shell)
/: waiting for /dev/disk/by-uuid/b0a9333e-41b8-4807-b4a4-6d277be937c5
/tmp: waiting for (null)
swap: waiting for UUID=fd8e9e31-2d77-4927-a7e5-0f52af3cb9de

At this point, I push ESC. Then i get this:

mountall: Cancelled
init: mountall main process (814) terminated with status 1
General error mounting filesystems.
A maintenance shell will now be started.
CONTROL-D will terminate this shell and re-try.
root@(none):~#

And now i don't know what to do. How can i fix my system? How can i resume the upgrade or downgrade back to jaunty? I basically just need a computer to use and don't want to lose any of the files i have on my computer. I have lots of important work and it will be a serious tragedy to lose it all if i need to do a fresh install from disk.

---

### Post by prshah on 2009-11-02
> **g-raf said:**
> 
One or more of the mounts listed in /etc/fstab cannot yet be mounted:
(ESC for recovery shell)
/: waiting for /dev/disk/by-uuid/b0a9333e-41b8-4807-b4a4-6d277be937c5
/tmp: waiting for (null)
swap: waiting for UUID=fd8e9e31-2d77-4927-a7e5-0f52af3cb9de


I had the same problem on my laptop (Though I had completed the upgrade successfully). The only way I could solve it was by commenting out the offending UUID in /etc/fstab; fortunately it referred to my fat32 Windows partition and not "/" or "/home". I still have to leave it commented out; everytime I enable it I land up with the same error as you.

This means that my Windows partition is now not automatically mounted; I have to doubleclick it in Nautilus to mount it. This also means that my documents created in that partition are not indexed by Google Desktop.

I suggest you try to comment out the stated UUID from your /etc/fstab, if it does not refer to a linux partition. To access the file, you will need a live CD; boot off it, open a terminal (Applications-Accessories-Terminal), then use the following commands:```
sudo mount /dev/sdX9 /mnt -o defaults,rw
sudo pico /mnt/etc/fstab
#comment out the relevant UUIDs
#Ctrl-X to quit pico; save when prompted
sudo umount /mnt
sudo reboot

```

replace /dev/sdX9 with the linux partition ID that contains the "/" (root) filesystem.

---

