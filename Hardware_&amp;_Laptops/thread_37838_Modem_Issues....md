---
title: "Modem Issues..."
date: 2005-05-28
forum: Hardware &amp; Laptops
---

### Post by HedsUp on 2005-05-28
I've recently switched distros and I started out with Kubuntu but decided to install Ubuntu too as I kinda figured that there were some extra goodies and niceties in the Gnome side of things. I like it very much and most things are working great thanks to these forums and the step by step instructions people put on here so that even if I don't understand what I'm coding I get the results.

Anyway, all this to say that I'm having an issue with my modem. Normally I connect through a network on DSL and that's been fine from day one. Our line for our DSL is down so I thought I would try my modem. By the way I'm on a Dell Inspiron 1100 laptop and everything is integrated--the modem is a BCM V.92 56K on COMM 3 (that's what the windows side says).

I looked everywhere that I could think to find to try and find the modem I even when through KPPP and tried all of the drop down "modem" components except for the USB ones and everything said "cannot open modem". What can I do to get Ubuntu to recognize the modem?

Also, when I was running Suse 9.2 and Mandrake 2005 Limited Edition 10.2 I could see and open the windows drive. I am currently unable to access the windows drive from within Ubuntu at all. Any ideas on that one too? Thanks for your help!

---

### Post by andlinux21 on 2005-05-29
[FONT=Comic Sans MS][SIZE=3][COLOR=Navy]Did you check to see if that was a <winmodem> if so you maybe out of luck[/COLOR][/SIZE][/FONT]

---

### Post by ::DoGG:: on 2005-05-29
In my guess it`s a winmodem so You won`t probably able to use it under linux (lets just say that some of the hardware is emulated in driver under windows, so the modem is small and cheap, but it make it unusable under linux).
What kind of filesystem You have on windows partition ?
You probably have to mount it by yourself and add it to /etc/fstab so it will mount it automatically every boot.

---

### Post by aum11 on 2005-05-30
Yes, I also have a win modem on a dell laptop(conextant).
It is not working under Ubuntu.
My windows partition is ntfs.
What can I do please?

---

### Post by ::DoGG:: on 2005-05-30
so ok, put hose line in fstab:
```
/dev/hda5       /mount_point   ntfs    defaults,umask=000  0       0
/dev/hda1       /mount_point   ntfs    defaults,umask=000  0       0

```
As a "mount_point" type any directory that you want to mount partition under, but it must be created befor mounting the partition, so create directories first.
Then change /dev/hda1 to match the you windows partition name ( i assume that /dev/hda1 will suit You too cause it`s the first partition of device, so probablyit would be your C windows partition.

---

