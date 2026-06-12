---
title: "Can I upgrade my 8.10 to 9.04..."
date: 2009-07-22
forum: Installation &amp; Upgrades
---

### Post by Yanowski on 2009-07-22
[subj]...from local .iso image, 'cause my cdrom on laptop is broken... Or when I can find information to "Upgrading Ubuntu via NFS". Sorry for my English.
P.S. arch i386 (Desktop) and I don't have a fast internet connection, only dial-up :) Thnx.
From Russia with love ;) Yanowski Miron.

---

### Post by dstew on 2009-07-22
It seems you want to install Ubuntu on your laptop, which already has Ubuntu 8.10 on it, but since you have a slow internet connection and no CD-ROM, you need to try to install it over your home network. Is that correct?

Probably the easiest way to do it, assuming you have the .iso on your desktop, is to transfer the .iso to your laptop over your home network, and then set up grub to boot the .iso. Then, you can install it on a new partition just as you would with a CD-ROM. However, you of course will not be able to delete the partition that contains the .iso during installation, but if you want to, you can delete it afterward.

Here is a [How-To]("http://deepbluespaces.blogspot.com/2008/07/install-ubuntu-804-from-hard-disk.html") about it. It was written for installing 8.04, but I am pretty sure it would work for 9.04. It is probably a good idea to create the target partition for 9.04 ahead of time (before you start to install). Then, you won't have to edit the partition table during installation, only format the target partition(s) and designate mount points. Then, if something goes wrong, your laptop should still be able to boot.

Here is [another How-To]("http://sambitnayak.blogspot.com/2009/05/install-ubuntu-904-on-hard-disk.html") for the same thing. Some commands are a little different, but overall the method is the same. Here is the some [Ubuntu Documentation]("https://help.ubuntu.com/community/Installation/FromLinux") for this method.

---

### Post by Yanowski on 2009-07-23
Thanks a lot, **dstew**. I did not expect to see such a comprehensive reply! Unfortunately, I ran and installed Ubuntu from a flash card, pre-recorded it .iso. But that's another story... Once again, thank you very much!

---

