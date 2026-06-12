---
title: "Live was working, now it doesn't"
date: 2008-12-19
forum: Installation &amp; Upgrades
---

### Post by Rick W on 2008-12-19
I booted the live cd this morning and found everything to be great so I went for the install. Also easy. Then the system would not boot. I got the error:

grub loading stage1.5read error

I then found I was unable to boot the live cd any longer. it gave me a endless screen of errors.

I tried making a new boot disk and that did not work. I reinstalled xp with no problem. But i still can no longer boot the live cd.

I was finally ready to put a linux box in to daily use and now this. I had avoided it in the past due to installation issues or driver issues with wireless. what I saw of 8.10 this morning was great, all of my devices worked, I was ready to go. 

I have searched the forums and tried adding options to use only ide, or no pnp, but still nothing. Please, any assistance is appreciated.

-Rick

---

### Post by Partyboi2 on 2008-12-20
What are the errors you are getting when you try to boot the live cd?

---

### Post by Rick W on 2008-12-22
ata1.00: execption Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
ata1.00: DMSMA stat 0x65
ata1.00: cmd c8/00:00:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
ata1.00: res 51/40:02:06:00:00/00:00:00:00:00/e0 Emask 0x9 (media error)
ata1.00: status { DRDY ERR }
ata1.00: err {UNC }

---

### Post by Partyboi2 on 2008-12-22
The only thing I could suggest is to check your hard drive with smartmontoolshttp://smartmontools.sourceforge.net/

---

