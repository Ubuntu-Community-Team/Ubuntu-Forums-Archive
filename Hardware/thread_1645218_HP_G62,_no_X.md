---
title: "HP G62, no X"
date: 2010-12-14
forum: Hardware
---

### Post by srg86 on 2010-12-14
Hi

I've just bought a new HP G62 Laptop, Win7 is working fine but I can't get X to work with kubuntu 10.10 x86_64.

The Live CD works perfectly, X is running and I can use the normal installer. Installing with either the Desktop or alternate installs works fine.

The problem is when booting the installed system, X and KDM do not work. KDM dumps me into a text based screen. After logging in if I try 'startx' I get:

(EE) /dev/fb0: no such file or directory.

Why does this work on the LiveCD and not on an install?

I'm running:
HP G62 WV689AV
Intel Pentium Dual Core P6100 2GHz 3MB L3 cache
Integrated Intel HD Graphics (built into P6100)
3GB RAM
320GB hard disk.

Everything else on this machine works fine.

Thanks
srg

---

### Post by loonysalmon on 2010-12-26
I am experiencing the same problem with 10.10 amd64.

Please let me know what logs you need posted and I will do my best to get them here so we can work this problem out.

-Thomas Donahue

---

### Post by loonysalmon on 2010-12-29
Alright, so I managed to get a fix for this. :)

When the machine boots up you will be stuck at a terminal.  Log in with the user-name and password that you created while installing ubuntu.  Once you are in, plug an ethernet cord into the PC to attain a network connection and afterwards you need to type the following commands to perform a distribution upgrade.  I am not sure whether or not a normal upgrade would work, however I just put my system up to the latest 11.04 and everything works at this point. ):P ):P 

```
sudo apt-get update
sudo apt-get dist-upgrade
```

You will need to put in your password following the first command.

Allow the system to perform the full distribution upgrade and after it has finished restart your computer.  Let me know if this fixes your problem as it did mine.

Time to fix this TOUCHY synaptics touchpad. :)

-Tom

---

