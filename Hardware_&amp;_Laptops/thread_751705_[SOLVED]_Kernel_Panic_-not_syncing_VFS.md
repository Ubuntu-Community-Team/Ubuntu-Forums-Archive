---
title: "[SOLVED] Kernel Panic -not syncing: VFS:"
date: 2008-04-10
forum: Hardware &amp; Laptops
---

### Post by greenstar on 2008-04-10
My PC was running when there was a power outage in my area. I came back to it later (wasn't present for power outage). I tried to power up my Gutsy box and all I can get it to do is:
```
Kernel Panic -not syncing: VFS: Unable to mount root fs on unknown-block(0,0)
```

So I loaded up the live CD and went in to see if my drive was functional. I was in fact able to browse the /, /home and every other partition on the drive.

I tried running sudo update-grub from the live CD and get this:
```
Searching for GRUB installation directory ... 
-e No GRUB directory found.
 To create a template run 'mkdir /boot/grub' first.
 To install grub, install it manually or try the 'grub-install' command.
 ### Warning, grub-install is used to change your MBR. ###
```

This despite being able to browse to the grub directory and see the files.

Anybody know what this means? Do I need to install Ubuntu fresh? I'd be effing po'ed if I had to install Gutsy again this close to the Hardy release.

At first, I thought this was a grub problem, but now I'm starting to doubt that assessment.

Greenstar

---

### Post by greenstar on 2008-04-10
Thank you to those who viewed my post with the intent of helping, even if you didn't know the answer. My thanks for your time & effort anyway.):P I am going to have to reinstall because I cannot wait any longer as this machine is the one I run my business from and it *has* to be working. I'm posting this so that no one else wastes their time trying to help fix this.:)

Greenstar

---

