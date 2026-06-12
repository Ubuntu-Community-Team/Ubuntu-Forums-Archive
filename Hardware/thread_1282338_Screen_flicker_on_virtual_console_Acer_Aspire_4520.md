---
title: "Screen flicker on virtual console Acer Aspire 4520"
date: 2009-10-04
forum: Hardware
---

### Post by mo0nykit on 2009-10-04
Hi!

I have just installed Ubuntu 9.04 Jaunty on my Acer Aspire 4520:
> **Acer Aspire 4520**
Nvidia nForce 610m/GeForce 7000m
2GB RAM
160GB HDD (only 12GB + 4GB swap for Ubuntu)After installation, I installed all updates and also the **Nvidia proprietary drivers 180.x**

My problem is, when I switch to a virtual console (Ctrl-Alt-F1), the screen goes blank and flickers with white around the edges, and some thin black horizontal stripes. The same thing also happens during shutdown, I can't see the shutdown splash screen.

When I go back to the X virtual console (Ctrl-Alt-F7), everything goes back to normal.

Here is my guess:

This seems to be a framebuffer problem. Or maybe because Ubuntu doesn't know how to render text-only consoles now that the Nvidia drivers are loaded. I don't know. What could be wrong? How can this be fixed?

Thanks in advance!

---

### Post by mo0nykit on 2009-10-05
I have found a solution over at **#ubuntu**. Many thanks to **stebalien** :)

In your **/boot/grub/menu.lst** file, add a **vga=<framebuffer mode>** option to the command line of the kernel that you are using. Here is the entry for the kernel that I'm using```
title           Ubuntu 9.04, kernel 2.6.28-15-generic
uuid            f58a2a33-2a85-4e31-8eab-fd8394047365
kernel          /boot/vmlinuz-2.6.28-15-generic root=UUID=f58a2a33-2a85-4e31-8ea
b-fd8394047365 ro splash vga=792
initrd          /boot/initrd.img-2.6.28-15-generic
quiet
```Here is a reference page [http://linuxandfriends.com/2008/09/17/vga-modes-used-linux/](http://linuxandfriends.com/2008/09/17/vga-modes-used-linux/)
In that page, framebuffer modes are given in hex. It's still fine to give **vga=0x318** for example. I used decimal notation in my solution.

If you want to google some more about this, the keywords are **vga**, **framebuffer mode**, **linux**

---

### Post by Stebalien on 2009-10-05
You can get the available vga modes by running 'sudo hwinfo --framebuffer'

---

### Post by mo0nykit on 2009-10-05
Thanks for the tip!

---

### Post by rikAtee on 2010-06-09
I am having the same problem on ubuntu 10.04 - however, i also get the problem on the login screen.

on the login screen the flickering sometimes goes away after a few secs but some times does not go away ever and I have to use live CD of 9.10 because even with live cd of 10.04 the same thing happens.

the flickering never goes away on virtual console.

10.04 uses a different version of grub and so the steps showed here don't work for me.

I have tried uninstalling nvidia drivers: didn't help
I have tried reinstalling nvidia drivers: didn't help


An odd thing I have noticed is that the flickering on the login screen occasionally is stopped by moving the mouse. Also, once it was stopped when I pressed space bar lots of times but this was not repeatable. I am not saying this is causation but I am throwing it out there in case it helps.

Any aid for a chap in need?

---

