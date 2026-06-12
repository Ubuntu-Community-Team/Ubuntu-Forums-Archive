---
title: "No USB or nic drivers working"
date: 2013-04-25
forum: Hardware
---

### Post by blokgang on 2013-04-25
Hey Guys

I have an alienware m17x laptop and im dual booting with win8

on fresh install of 13.04 official release my keyboard and mouse will not work.  it also says im disconnected from the network which means my nic drivers dont work either because im hardwired

my mouse trackpad on the laptop also does not work

this happened as well with the daily builds 

any ideas?

---

### Post by blokgang on 2013-04-25
id also like to add everything worked fine on the live cd with the exception of screen resolution which would probably be fixed with the ati driver install

---

### Post by Splace on 2013-04-28
I have exactly the same symptoms. Dual booting windows 8. 64 bit. Works fine in the live cd.

---

### Post by John Br on 2013-04-29
Guys, I had this cursing problem as well. However, I read here that if you make an usb-bootlable drive with the Startup Disk Creator, it would solve the usb and network issues. I had done it with the UNetbootin disk creator because the startup disk creator from ubuntu distro was buggy. I also read about the UFI Bios stuff partitioning problems.

So, the first thing I did was to make this bootable drive.(even with the DVD it did not work) I did it from Linux Mint. the second thing was to make the installation in an 3 partition way, / for the system, /home and swap. All was made clean and organized.

And for my surprise all functions are working now. So I will move on to an Nvidia realated problem.


Hope it helps you out.

---

