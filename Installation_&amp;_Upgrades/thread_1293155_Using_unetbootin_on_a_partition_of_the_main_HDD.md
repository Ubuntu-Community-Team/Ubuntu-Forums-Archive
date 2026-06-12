---
title: "Using unetbootin on a partition of the main HDD"
date: 2009-10-16
forum: Installation &amp; Upgrades
---

### Post by Jayferd on 2009-10-16
Hey all,

So my friend has this dinosaur of a computer which can boot from neither cd nor usb, and I'm attempting a Xubuntu install.  I told him to do something which I'm testing on another dinosaur I've got kicking around.

Since it's only got one IDE port (augh), I decided to try something radical.  I plugged it's HDD into an extra IDE on my computer and partitioned it with gparted, using the following partition scheme (approximately):

sda2 10G ext4
sda3 25G ext4
sda4  1G swap
sda1  2G ext3.

Then I used unetbootin to put the Xubuntu Karmic beta livecd environment on sda3.  Then I put the thing back into my dinosaur computer, and it booted just fine into the beautiful new xfce4 desktop.

BUT,

I went to install the thing (without running any other programs first), and told it basically not to do anything with the partitions, except I assigned sda1 to / and sda2 to /home.

The thing threw up an error that it couldn't make changes to the partition table because it couldn't unmount /cdrom.  The contents of /cdrom look like the contents of the livecd, so I'm assuming that's sda3, which it obviously can't unmount because that's where I'm running from.  It threw up the same error when I set sda3 to mount at /cdrom.

But didn't I basically tell it not to make any changes to the partition table?  Is there any way of doing this that won't cause ubiquity to try to unmount itself?

Thanks a ton,
--Jay

---

### Post by Jayferd on 2009-10-16
Bumpitty bump bump.

A guy on #ubuntu suggested using debootstrap, but I think that's a rather unsatisfying solution.  I'd like to install xubuntu from the image that's actually on the hdd.  (and not have to manually create my fstab and stuff).

---

### Post by stlsaint on 2009-10-16
well all you did was mount the livecd to a partition from what i can tell. but when you run the livecd via a actual cd than the contents are shared within ram and installed onto the hdd...you are trying to mount a partition and at the same time use it to isntall something else on the same hdd...im not seeing that as working! can you do a network install on that machine? [NetworkInstall]("https://help.ubuntu.com/community/Installation#Server%20and%20network%20installations")

---

### Post by Jayferd on 2009-10-17
Hm.  Yes, that's exactly what I did.  The live cd is not only mounted in the filesystem, it's actually running from sda3, on the main HDD.

Maybe it's impossible, then, but I think that's sort of sad.  Since it doesn't have to make changes to the partition table, you'd think it could just copy the files, install the packages and be done with it.

---

