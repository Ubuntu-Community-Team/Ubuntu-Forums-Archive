---
title: "nVidia hardware Driver Problems"
date: 2009-03-27
forum: Installation &amp; Upgrades
---

### Post by chizzops101 on 2009-03-27
Hello, 

Dell Inspiron 8000 , Geforce2 Go
Intrepid Ibex

After the Intrepid load and update everything works fine until I activate the nVidia hardware drivers. The screen goes to black upon restart. 

I've seen this problem around the forums and I found a suggestion:

add the following line to /etc/modprobe.d/options

    options nvidia NVreg_SoftEDIDs=0 NVreg_Mobile=2

After I did this my system hangs at the ubuntu splash screen. When I hit ctrl-alt-F1 I get a message that says:

kinit: No resume image, doing normal boot...

Again, many other people seem to have had this problem, but I get no login. I can restart, go to the grub menu and get to the root command line. 

I have no idea what to do now, other than reinstall the OS and update. That would bring me back to where I started: How do I get my nVidia drivers working correctly (I would like to utilize the 3d environment and dual monitors).

Thanks for any help, as I am going slightly crazy down here in Florida....

---

### Post by klemes on 2009-03-27
Try the newest NVIDIA drivers available through the NVIDIA website.
That solved my problem with an older videocard.

---

### Post by chizzops101 on 2009-03-27
Yeah I think that is my next idea. Looks like I will have to reload and update Intrepid. Hopefully the new drivers will work.

Thanks

---

### Post by chizzops101 on 2009-03-30
After a lot of searching and testing, EnvyNG ended up working for me. It installed the 96.43.09 driver version. Everything looks like its working.

The updated drivers on nVidia's site never did work.

---

