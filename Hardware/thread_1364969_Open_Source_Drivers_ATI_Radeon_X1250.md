---
title: "Open Source Drivers ATI Radeon X1250"
date: 2009-12-26
forum: Hardware
---

### Post by stark222000 on 2009-12-26
I uninstalled the open source FLGRX (or whatever it is) graphics card drivers so that i could install the actually proprietary closed drivers from Radeon. I restarted the laptop and i couldn't do anything graphically enabled. I couldn't turn on compiz to extra anymore nor could i watch flash videos in fullscreen. so i said "this sucks a lot more than the open source drivers" (because as it turns out this graphics card isn't supported by them on Karmic yet/ever. so i uninstalled it and installed all the open source drivers i needed and when i restarted it went to a black screen with no way to get to the text based login so i had to start in recovery mode so i could reinstall the crappy ATI closed source driver from the command line.

so my question is, Did i do something wrong so the resolution isn't set right for some reason? or if i just installed the wrong ones, how can I get the open source drivers back and working?

---

### Post by Yellow Pasque on 2009-12-26
[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch)

Also be sure to delete/archive your existing xorg.conf

---

### Post by stark222000 on 2009-12-26
how do i delete my xorg.conf?

---

### Post by Fir3chi3f on 2009-12-26
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf-backup
sudo rm /etc/X11/xorg.conf
```

---

### Post by stark222000 on 2009-12-26
thank you very much guys it worked perfectly.

---

