---
title: "Drivers for Custom Built Computer"
date: 2011-08-07
forum: Hardware
---

### Post by Thattallkid53 on 2011-08-07
I just built a computer with the AT31ION-I Delux Motherboard/CPU by ASUS.  I got the computer running however it seems to be running in minimum graphics mode.

I assume this is because my drivers for the motherboard are not installed since the CD that came with the board does not work in Ubuntu.

1) is this a logical assumption or is there another reason why my ubuntu is running low resolution graphics

2) does ubuntu offer an easy way to install hardware drivers?  (especially since I think this will be an issue with my wireless card, etc etc)

Thanks again!

-Chris

---

### Post by BrandonC19 on 2011-08-07
Welcome to the Forums.

Ubuntu does not require drivers in the same way Windows requires them. If you can tell the hardware is functioning in Ubuntu, then the correct driver is already found, and everything should be running smoothly.If not, there will be a message explaining this to you.

As for the "minimum graphics mode" is there a popup message at login that says this? Can you post a screenshot of your desktop so I can help you further?

   And as for installing drivers, there may be a closed source driver for your video card. Go to System>Administration>Additional Drivers and check to see if there is anything listed.

---

### Post by .... on 2011-08-08
```
sudo apt-get install nvidia-current
```

---

