---
title: "Blackerry Storm (how to mount?) 8.10"
date: 2008-11-22
forum: Hardware
---

### Post by zackiv31 on 2008-11-22
So I was fortunate enough to pickup a BlackBerry Storm today from Verizon, but like all new things, isn't very Intrepid Friendly.  Vista picks it up fine and can copy to it, but not out of the box for Intrepid.

How Can I mount the drives of my blackberry so I can copy/move data around on it.  When I plug it in I notice two drives *** sg1, and sg2... I think these are the correct ones?  Vista Picks up 1 1GB drive (no idea what this is, maybe applications), and 1 8gb drive (MicroSD card).

If I try to manually mount I get some error about no block device or something.  Any suggestions?

Note: This is purely for media, so anything to simply mount the drive will suffice.

---

### Post by solarlore on 2008-11-22
Found your post trying to solve the same problem myself! You're going to need to look inside your options menu to enable mass storage support and then also set it to enable automatically whenever you connect.

---

### Post by zackiv31 on 2008-11-22
Great, thanks for the tip! Automounts great!

---

### Post by AdamGott on 2008-12-04
Well crap, this doesn't work for me.  I have Mass Storage Mode set to ON, Auto Enable set to ON, and MTP set to ON.

I have tried with MTP set to OFF and no luck with that either.

---

### Post by mariner09 on 2008-12-04
I have a bold and usually when I plug it in I get asked if I want to enable mass storage, then the devices mount on the desktop.  The 1gb device is the internal memory and the other device would be the card.

---

### Post by AdamGott on 2008-12-04
I checked my dmesg and the blackberry is there, I have two USB Drives listed in my 'Computer' folder but when I double click I get 'Unable to Mount Location - No Media in Drive' errors.

Well crap, I tried a different USB port and now I see two Blackberry folders, problem solved I guess...

---

### Post by kezdetj on 2008-12-06
I have a similar problem.  I love my Storm, but I can't seem to mount it or use it as a wireless modem connected by USB.  I could use my old LG ENV as a modem easily, but not my Storm.  :(

---

### Post by kak on 2009-01-09
There appears to timing bug in the drivers for this device.  It will not automatically mount the drives on insert.  After the usb device icon shows up, double click, select the drive (media card) or device (bb internal), click properties, select the policies page, change the policy from what ever it is, then hit ok.  The drive will mount for you.  Unfortuneately you need to do this every time you insert the bb.

---

