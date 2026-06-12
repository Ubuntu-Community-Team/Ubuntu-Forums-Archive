---
title: "All in one card reader won't work"
date: 2008-07-15
forum: General Help
---

### Post by SneakPeak on 2008-07-15
Good Day,

I have a generic all in one card reader.  On the front it says USB2.0 ALL-in-1 Card Reader Hi-Speed Certified USB!

It works under windows but I can't get it to run under Ubuntu.

I am running Ubuntu 7.10 Gutsy (Actually Kubuntu)

When I plug it in the power light comes on.
When I plug in a memory card the light for that memory card comes on.
Both lights stay on for about 10 seconds or so and then go off.

My USB mouse works perfectly.
My USB printer works perfectly
My USB scanner works perfectly.
My USB Free Agent hard disk works perfectly

Some help would be greatly appreciated.

Sneaks:(

---

### Post by tamoneya on 2008-07-15
plug the card in and please go to terminal(applications -> accessories -> terminal) and type:```
sudo fdisk -l
```

---

### Post by SneakPeak on 2008-07-15
Hi 

Thanks for the reply.  The output from fdisk -l is attached.  This was done while the lights were still on.

Sneaks

---

### Post by jimmy the saint on 2008-07-15
what is the reuslt of typing "lsusb" in the terminal?

---

### Post by SneakPeak on 2008-07-15
lsusb gives:

Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 12d1:1001  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 004: ID 0bc2:3000 Seagate RSS LLC 
Bus 002 Device 002: ID 03f0:3217 Hewlett-Packard 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 1241:1166 Belkin 
Bus 001 Device 001: ID 0000:0000

---

### Post by jimmy the saint on 2008-07-15
okay, I am pretty sure that the Belkin device is your card reader, but lets make sure.  unplug the device, run lsusb again, and see if that is the entry that is gone.  Once we are sure, we can try to make it work!!

---

### Post by SneakPeak on 2008-07-15
Unfortunately not.  With the card reader plugged in or not I get the same output from lsusb.  I think the Belkin is my 3G card.

---

### Post by tamoneya on 2008-07-15
have you tried plugging it into different USB ports?

---

### Post by jimmy the saint on 2008-07-15
have you tried it with and without a card in it?  may be a sill question, but my built in one isn't recognized until a card is inserted.  sorry I couldn't be more help!

---

### Post by SneakPeak on 2008-07-15
Yes, 3 different ones (USB ports that is).

In the past I got it to work by plugging in a smaller capacity card. (128MB vs. 512MB).   I tried today with a 32MB card but that trick didn't work. I think the trick worked on a previous version of Ubuntu.

I have also tried with the card in and the card out.

---

### Post by tamoneya on 2008-07-15
can you test the reader on another computer to confirm that the reader isnt faulty?

---

