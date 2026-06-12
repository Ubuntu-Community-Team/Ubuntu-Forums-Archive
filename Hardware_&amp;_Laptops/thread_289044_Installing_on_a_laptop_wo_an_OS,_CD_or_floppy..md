---
title: "Installing on a laptop w/o an OS, CD or floppy."
date: 2006-10-30
forum: Hardware &amp; Laptops
---

### Post by J4DED on 2006-10-30
I have recently been given a laptop that I would like to install Ubuntu on. It doesn't have a cd drive or a floppy. Its network card is a pmcia one - not an integrated one so I don't know if it is going to be recognized. The HD is blank and it doesn't boot.

1.) Is it possible to install Ubuntu on this laptop?

2.) If I put the hard drive in another computer (I have an adapter), install ubuntu on it and then put it back in the laptop, will the hardware be recognized or does it have to be installed on the hardware that is going to run it?

I couldn't find this covered in the forums but if it has I apologize and would appreciate the link to the thread.

Thanks.

---

### Post by ahaslam on 2006-10-30
I've never tried anything like it but I'd go with number 2. When the hard drive is back in the laptop, try booting to the CLI & run:

**sudo dpkg-reconfigure xserver-xorg**

As I said, I've no experience in this, it's just an idea ;)

Tony.

---

### Post by J4DED on 2006-11-01
Thanks for the advice,

I was able to pop the hard drive into another laptop to install Xubuntu on it but now I have a problem with finding the correct settings for the video card.

---

### Post by David Corrales on 2006-11-02
Run the command Anthony listed. It's meant for that, reconfiguring the X server. If you need to generate new refresh rates, then you can use **gtf** for that.
Also, I'd switch the driver to *vesa* initially, unless you know the make of the video card. That will help out by giving you a desktop.

---

### Post by J4DED on 2006-11-02
Okay, I've tried a few times but can't get it to work. (No display - black screen)

I've found through google that My video card is a 

[FONT="Courier New"]VGA compatible controller: S3 Inc. 86C270-294 Savage/IX-MV (rev 11)[/FONT]

What settings should I use?

dPa

---

### Post by David Corrales on 2006-11-02
For starters, I'd edit the xorg config file:
**sudo pico /etc/X11/xorg.conf**
and change the driver to "vesa" in order to get a working desktop.

---

### Post by J4DED on 2006-11-03
For some reason the VESA driver doesn't work. When the laptop boots up I do see the splash screen though so I know the display works. Whenever I boot into text mode and run [FONT="Courier New"]**sudo dpkg-reconfigure xserver-xorg**[/FONT] I get a XServer failure after I try to reboot into graphical mode.

---

### Post by David Corrales on 2006-11-04
Try changing the driver to **savage** instead of **vesa**

---

### Post by J4DED on 2006-11-05
Thanks for your help guys.

I was about to give up when the vesa, S3 and Savage drivers weren't working. Some further googling revealed that the 7200 actually had a trident video card. I've played with the settings enough now to get it up and going.

---

