---
title: "Updates Broke compatibility with something"
date: 2006-10-15
forum: Hardware &amp; Laptops
---

### Post by an.echte.trilingue on 2006-10-15
A strange thing is happening:

I installed dapper on my desktop about three months ago, and then i left on a business trip for a while.  At installation, everything worked perfectly.  I ran an update when I got back a few weeks ago, and now something is seriously broken in the video department.  

The card is an integrated prosavage8.  The box still detects it properly:

```
root@desktop:/home/admin# lspci | grep Savage
0000:01:00.0 VGA compatible controller: S3 Inc. VT8375 [ProSavage8 KM266/KL266]
root@desktop:/home/admin#
```

HOWEVER, when I use the savage driver (with or without DRI), the machine becomes very unstable.  It hard crashes if I start anything that has a splash screen (like OpenOffice), or anything that uses lots of memory, such as QT apps.  If I use the vesa driver, the problem is less pronounced, but it still happens.  It also contiues if I use the original kernel on the install CD (2.6.15-26-386) so I am pretty sure the problem is not a regression in the kernel.

This is my version of xorg.conf that uses the savage driver and crashes most: [ATTACH]17610[/ATTACH]

And this is my version of xorg.conf that uses the vesa driver and crashes less, but still crashes:[ATTACH]17611[/ATTACH]

Does anyone know what gives?

thanks
-mat

---

### Post by dmizer on 2006-10-15
try this thread:
[http://www.ubuntuforums.org/showthread.php?t=241254&highlight=updates+break+xserver](http://www.ubuntuforums.org/showthread.php?t=241254&highlight=updates+break+xserver)

---

### Post by an.echte.trilingue on 2006-10-16
No, it is already version 10.4;

Thank you very much for your help, though.  Do you have any other ideas?

I am really stumped.  I suppose I can just switch between the two configs depending on what I need to do and see if a dist-upgrade to edgy when it is released will help things. 

Take care,

mat

---

### Post by dmizer on 2006-10-17
have you tried
```
sudo dpkg-reconfigure xserver-xorg
```
in my opinion, making changes that way is preferable to manually editing xorg.conf.  you might have more luck.  if you've already done that, i'm not too sure what to tell you.

on a whim ... you might try adding: acpi=off to your kernel arguments in grub.  shot in the dark, but it might do what you need.  shouldn't hurt anything either way.

---

