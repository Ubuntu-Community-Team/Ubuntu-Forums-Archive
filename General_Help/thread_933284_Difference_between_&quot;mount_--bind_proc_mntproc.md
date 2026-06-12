---
title: "Difference between &quot;mount --bind /proc /mnt/proc&quot; vs. &quot;mount -t proc none /mnt/proc&quot;?"
date: 2008-09-29
forum: General Help
---

### Post by jasper.davidson on 2008-09-29
Say I have a linux distro in /dev/sda1 that I mount on /mnt while I'm running from a different linux (Live CD for example):
```
sudo mount /dev/sda1 /mnt
```
My ultimate goal is to mount all the necessary system directories and other stuff to /mnt so that I can chroot into /mnt and have as much functionality as possible. So I'm confused about what is the difference between the following:
```
sudo mount --bind /proc /mnt/proc
sudo mount -t proc none /mnt/proc
```
Also, how do the following differ:
```
mount -t sysfs sys /mnt/sys
sudo mount --bind /sys /mnt/sys
```
Any ideas? Thanks in advance.

---

### Post by bodhi.zazen on 2008-09-29
I am not sure what you are trying to do or what your question is.

Mount bind is similar to a link. There are times when you can not use a soft link, and hard links will not cross physical partitions, so mount --bind

If you mount /foo and then mount --bind /foo /mnt/foo the contents of /foo are at BOTH
/foo and /mnt/foo

==========

If you are wanting to work with chroots, I encourage you, they are great fun.

May I suggest OpenVZ ? you can install the OpenVZ kernel from the Ubuntu repositories.

[http://wiki.openvz.org/Main_Page](http://wiki.openvz.org/Main_Page)

If you do not wish to use OpenVZ, you will find this educational :

[http://wiki.openvz.org/Debian_template_creation](http://wiki.openvz.org/Debian_template_creation)

Then if you prefer to use straight chroot :

[https://wiki.ubuntu.com/DebootstrapChroot](https://wiki.ubuntu.com/DebootstrapChroot)

[http://wiki.mandriva.com/en/Development/Howto/Chroot](http://wiki.mandriva.com/en/Development/Howto/Chroot)

And for X sessions, be sure to check out :

[How to Xephyr ~ AKA Multiple, nested X sessions - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?p=3816948#post3816948")

---

### Post by jasper.davidson on 2008-09-30
Hey that's great info, especially the chroot links at ubuntu.com and mandriva.com. Thanks for sharing that!

My simple understanding right now is that to make the chroot environment usable, I have to "bind" some of the current system directories like /dev, /sys, /proc to the chroot environment. That basically makes sense to me so far. But what I don't understand is what the difference is (if any) between the two different methods:
```
sudo mount --bind /proc /mnt/proc
```
and:
```
sudo mount -t proc none /mnt/proc
```
So it seems like both of the above commands do sorta the same thing, binding the processes or "proc" to the chroot environment. Is there any difference?

---

