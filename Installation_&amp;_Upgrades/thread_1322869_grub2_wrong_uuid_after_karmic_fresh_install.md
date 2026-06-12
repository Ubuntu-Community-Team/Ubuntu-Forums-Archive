---
title: "grub2 wrong uuid after karmic fresh install"
date: 2009-11-11
forum: Installation &amp; Upgrades
---

### Post by thomas_122 on 2009-11-11
Hello all,

First of all, I might very well be wrong, but I've looked in the forums and haven't found anything to help.

So here is the think. I upgraded from jaunty to karmic four days ago, and after encountering quite a few issues I decided to rather do a fresh install from a cd, since I had my home on a different partition anyway.
However, I have two main problems:
- when I want to shutdown, everything goes well until the laptop is supposed to power off, when at this time it restarts instead (it was already doing this with the upgrade).
- but more importantly, when I restart, it doesn't boot. I see a "grub loading" message and that's all. I figured something was wrong with grub so I booted from a "live" usb stick, and looked at the boot settings. First I was quite surprised to see that no "/boot/grub/menu.lst" was created.
In order to fix that I did chroot, update-grub and I get:

[FONT=System]root@ubuntu:/# update-grub
Searching for GRUB installation directory ... found: /boot/grub
findfs: unable to resolve 'UUID=f703660f-ae56-4c27-a9e4-6a1c4b6fa482'
Cannot determine root device.  Assuming /dev/hda1
This error is probably caused by an invalid /etc/fstab
findfs: unable to resolve 'UUID=cfa9dbad-d0a3-43c2-90b9-bc56910056ed'
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.31-14-generic
Found GRUB 2: /boot/grub/core.img
Found kernel: /boot/memtest86+.bin
sed: warning: failed to get security context of /tmp/fileUJHAi7: No data available
sed: warning: failed to get security context of /tmp/file9xwBgQ: No data available
Updating /boot/grub/menu.lst ... done

When I do an "[/FONT]ls -l /dev/disk/by-uuid", the two UUID above are indeed showing up. Therefore my question is why didn't grub create a menu in first place, and how can I get update-grub to grab the right stuff.
Or do I have it totally wrong since I remember reading somewhere that karmic comes with grub2?

Any kind of help will be deeply appreciated. I have to go to work but I'll follow the thread and post additional info tonight if needed.

PS: I loved jaunty, it worked flawlessly out of the box for me, and I'm quite exited with karmic but I'm a bit disappointed with the ugly brown screen when the OS loads. I liked the orange progress bar, why is that gone?

---

