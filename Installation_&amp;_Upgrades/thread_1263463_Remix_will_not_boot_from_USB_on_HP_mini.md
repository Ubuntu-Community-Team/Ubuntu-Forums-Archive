---
title: "Remix will not boot from USB on HP mini"
date: 2009-09-11
forum: Installation &amp; Upgrades
---

### Post by cannyej on 2009-09-11
I just bought an HP mini 2140 having read that it worked well for installing the Ubuntu remix.  The computer comes with XP preinstalled.  I would prefer a dual boot if possible, but would be happy to settle for just Ubuntu.

I have created a bootable USB drive.  I have successfully booted from the USB on my MacBook Pro, however, it does not work on the HP.

When I turn the computer on, I press F9 to select a boot disk.  It takes me to a menu where I can select the computer hard drive or the USB disk.  When I select the USB, the screen goes blank, and nothing happens from then on.  

I have tried pressing some keys.  Eventually they make a beeping sound every time I press one, but nothing else happens.  There is no cursor.  

I have tried going into the BIOS settings and changing a few things, but nothing has worked so far.  In response to another post on the forum, I tried disabling the dual core processing, but that did not work.

Any advice would be greatly appreciated.  :)

---

### Post by Sivik on 2009-10-20
I am having this same problem.  I put the ubuntu cd on the usb drive and I get a blank screen with a blinking curser and nothing happens.  What are we doing wrong?

---

### Post by dandnsmith on 2009-10-20
Sounds like it might be machine specific -
no problems with AA1 booting it from usb, or with booting from external CD

---

### Post by shyster on 2009-11-03
I have an HP Mini 110 & I'm having the same issue trying to get karmic to boot. Jaunty, however, was booted & installed from usb, but I think there was an img file for jaunty that I used?

Update: Sucessfully booted & installed karmic via jump drive using UNetbootin.

---

### Post by binks11 on 2009-11-10
I recently bought the HP mini 311 that comes with Windows 7. I then installed Ubuntu 9.10 (not the netbook remix )from the usb drive into a separate partition and all went okay. But then trying to boot into linux after the install fails. Just gives a blinking cursor after selecting Ubuntu from the Grub boot loader.

Then tried re-installing ubuntu into that partition a couple times trying ext3, ext4... no luck. Same issue, wont boot. Also sometimes gets stuck when trying to boot from the USB. Prepared the usb using 
unetbootin (does not work 100% of the attempts) and then USB-Installer-U910 which worked better.

Finally gave up and removed ubuntu partition and grub... Pity cause 9.10 looks so promising!

---

### Post by frenchiewhite on 2009-12-16
same problem... using san disk cruzer 4gb on a Eeepc 1000h.
Dark screen and a blinking -
... trying to install Ubuntu 9.10

---

### Post by darkod on 2009-12-16
Dark screen and blinking sometimes could be video driver issue. Have you tried Try Ubuntu option first to see if it will run OK?

---

### Post by frenchiewhite on 2009-12-17
I already have ubuntu on it. but something broke, so the only possibility I have is to install ubuntu new. and the problem is, I'm leaving soon, and my Eeepc has no Internet (<- the Problem, the thing that broke...)

---

