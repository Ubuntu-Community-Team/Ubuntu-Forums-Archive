---
title: "Slow-ness in normal boot. Flies in failsafe mode"
date: 2008-07-22
forum: General Help
---

### Post by Leion on 2008-07-22
I am not sure why if I were to boot with normal boot, the system crawls. However when I logged in with failsafe mode, the system flies. 

I have removed compiz but the slowness still exists.

Anyone can guide me how to debug and troubleshoot this?

---

### Post by Gunman1982 on 2008-07-22
What do you have installed on the system? webserver? database? what specs does your system has (cpu,ram,gfx)?

---

### Post by Leion on 2008-07-22
> **Gunman1982 said:**
> What do you have installed on the system? webserver? database? what specs does your system has (cpu,ram,gfx)?

my system is a laptop. IBM T43
cpu 1.8GHz
512 MB ram
ATI X300 graphics card

The system was working acceptably with compiz until i did some system upgrade. I think the graphics driver was auto updated. After the upgrade, the system crawls. That is when I removed compiz but the problem does not go away..

---

### Post by Gunman1982 on 2008-07-22
what do you get when you execute 'fglrxinfo' in the console?

---

### Post by Leion on 2008-07-22
> **Gunman1982 said:**
> what do you get when you execute 'fglrxinfo' in the console?

This is what i get in failsafe mode

leion@leionuntu:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI MOBILITY RADEON X300
OpenGL version string: 2.1.7412 Release

---

### Post by Leion on 2008-07-29
bump

---

### Post by caljohnsmith on 2008-07-29
I would temporarily change your menu.lst so that you can see all the system messages on startup; that way you will know exactly what Ubuntu is doing and which processes might be causing it to take a long time.

Try doing:
```
gksudo gedit /boot/grub/menu.lst
```
And for your Ubuntu entry, put a comment ## before the "quiet splash":
```

title		Ubuntu 8.04, kernel 2.6.24-19-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=77677cb5-6e56-4936-a373-80c15de06bca ro [COLOR="Red"]##quiet splash[/COLOR]
initrd		/boot/initrd.img-2.6.24-19-generic
quiet
```
Then watch carefully what goes on the next time you boot.

---

