---
title: "Help with Touchscreen."
date: 2010-08-11
forum: Hardware
---

### Post by b1ackcr0w on 2010-08-11
Bus 003 Device 002: ID 0408:3001 Quanta Computer, Inc. 

Hi!

I  have a 21.5" Touchscreen from Aldi (Medion) which I picked up for a  bargain. I had it working for a while, then for reasons of daftness, I  clean installed (Lucid Gnome 32bit Desktop). The usb input that shows up in lsusb is  above. I've also installed xserver-xorg-input-evtouch, and everything  else that had someting to do with touchscreens. All to no avail.

Thanks in advance for any assistance you can lend...

---

### Post by b1ackcr0w on 2010-08-13
Small update...
 
lsmod reveals that the kernel has loaded a quanta module, so the kernel can see it. So I'm thinking xorg or Gnome is the problem?

---

### Post by 0AintLifeGrand0 on 2010-12-02
I have the same problem (Medion Akoya 54009)

also see:
Bus 004 Device 003: ID 0408:3000 Quanta Computer, Inc.
on an lsusb.

Anyone ideas to get this working? 

(PS. 
I'm a newbie Ubuntu user and newbie C/Cpp-programmer and looking for some real-life experience. Although I have little knowledge on linux I'd love to assist to this subject on technical level)

Kind Regards

---

### Post by 0AintLifeGrand0 on 2010-12-05
I got the touch screen working by updating to the Ubuntu 10.10 (beta) release.
Be aware that this release might not yet be fully stable since its only released for test (if I understoof correctly). Please search these forums for problems before updating to 10.10.

I got the following problems:
- Modprob fatal error, GRUB problem... Known issue, no system failure but error message on startup, solution can be found by googling- on modprob error message that you get during startup. Solved now

- Touch function causes failure upon Ubuntu startup,
I'm using the screen as secondary screen on a laptop and the OS seems to have a problem with determining which screen-resolution it should link the "touch" to upon start-up. I **must** plug-in the usb connector of the touch screen after **login** in (so after the "secondary" screen gets correctly initialized.

-Touch function uses incorrect function when I connect it before login, after boot.
I can connect the touch screen after booting up, but before login in. This causes the incorrect resolution to be used for the touch functions. In other words, it uses my primairy screen resolution to map the touch coordinates, while it should use the secondary resolution. 
 
As soon as I have some time I'll report the 2nd and 3rd problem.

Summary, if I plugin the touch screen usb after login it works fine on Ubuntu. 
I wasn't able to install and use gesture tools though.

Kind Regards

---

