---
title: "DV9000 another thread.   10.04"
date: 2010-08-10
forum: Hardware
---

### Post by greenwom on 2010-08-10
Just upgraded to 10.04 on the dv9000 series ( dv9201ca )

Wifi, you still need to do a hardwired connection to download drivers.
The webcam still doesnt' work (tried all the available drivers)

Here's my notes:

Run the install

plug into your network

~$ sudo apt-get update

to see what card you have do this.

~$ lspci 

I hade the BCM4311

~$ sudo apt-get install bcmwl-kernel-source

Goto System -> Administration -> Hardware Drivers

make sure the STA driver is selected.

reboot

wifi done.

Video Drivers:

go back to the hardware drivers section

Goto System -> Administration -> Hardware Drivers

select the recommended driver.

reboot


Not to bad to get up and working, even without a webcam.

---

