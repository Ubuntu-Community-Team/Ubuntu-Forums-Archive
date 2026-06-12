---
title: "Portage and Emerge for USB Gentoo"
date: 2008-02-12
forum: Gentoo and derivatives
---

### Post by Ominide on 2008-02-12
Hi, I'm trying to make a Gentoo bootable USB linux device (1gb flash) for robots that my robocup team at school, I'm to the point where I need to start installing packages and such on the USB linux.  What I want to know is there a way that I can use Portage and Emerge from my Ubuntu 7.10 or find some way of using my using Portage from the USB and downloading and compiling on the ubuntu files system then pushing the Gentoo build to the USB drive.

Any help would be great, I really don't want to have to install another version of linux on my laptop. 

Thanks all.

---

### Post by Crooksey on 2008-02-14
Surely you just need to chroot into the usb drive?

```

mkdir /mnt/gentoo
mount /dev/usbstick /mnt/gentoo
chroot /mnt/gentoo /bin/bash
```

Or did i mis read your post?

---

### Post by Ominide on 2008-02-15
I believe that will cause the code to be downloaded and compiled on the USB, I was needing a system that would use the HDD of ubuntu as, essentially its scratch / working location.

---

### Post by Crooksey on 2008-02-17
So you want portage to download and install programs to ubuntu?

---

### Post by Ominide on 2008-02-18
I just want to use ubuntu as the host system.  
I have a stage3 setup on the USB drive that will be used as the main hdd of the robot.  What I'm trying to do is get gentoo on the usb to download and build on the HDD of ubuntu that way it doesn't try to build the packages on the USB drive then just move them to the USB drive when it is done building.

This is the process i'm using:
```

mkdir /tmp/portage
cd /mnt/stick
mkdir usr/portage
mkdir var/tmp/portage
cp /etc/resolv.conf etc/resolv.conf
mount -t proc proc proc
mount --bind /usr/portage usr/portage
mount --bind /tmp/portage var/tmp/portage
chroot /mnt/stick /bin/bash
env-update
source /etc/profile

```
Then doing this
```

emerge -v syslog-ng vixie-cron dhcpcd \ 
 grub \
 xorg-server gnome gdm 

```

When I try to run this it spits something at me about the protage tree being correct ... here's exactly what it outputs when i run emerge:

```

Omi-Chan / # emerge -v syslog-ng
--- 'profiles/arch.list' is empty or not available. Empty portage tree?
--- 'profiles/updates' is empty or not available. Empty portage tree?
!!! ARCH is not set... Are you missing the '/etc/make.profile' symlink?
!!! Is the symlink correct? Is your portage tree complete?


```

---

### Post by Crooksey on 2008-02-19
Do you have make.conf setup correctly?

Have you even sync'd the portage tree yet?

---

