---
title: "can't boot new installation - initramfs after installing jaunty on raid1"
date: 2009-05-18
forum: Installation &amp; Upgrades
---

### Post by Mip5 on 2009-05-18
Hey Gang,

I installed jaunty onto a server and set it up so that / would be on md0, raid1. Well, on my server, it didn't come up on boot. I got an error indicating "Gave up on root file system..."
and then got dropped into an initramfs (busybox) shell.

When I looked around, I could see that md0 was available, and I was able to chroot into that environment (first make a mount point, and then mount /dev/md0 on that mount point), and view and edit files.
 
I learned today that the cause of the problem was that the raid partition wasn't ready for use by the system when it was needed, but did come up later. 

A friendly user on IRC tipped me off to this, and suggested that I add a delay to the kernel parameters for booting. Bingo! It worked!!

To do this, I had to chroot into the root filesystem: 

mkdir md0
mount /dev/md0 md0
chroot md0

and then navigate to and edit the menu.lst file to add the delay:

cd /boot/grub/
vi menu.lst

and then add: rootdelay=200 to the kernel line (the line beginning with the word "kernel").

Anyway, I wanted to share that with y'all. I spent a pretty good while hunting this down, and hope to save someone else some time.

Peace,

M

---

