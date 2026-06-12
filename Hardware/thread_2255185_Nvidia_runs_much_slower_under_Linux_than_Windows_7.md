---
title: "Nvidia runs much slower under Linux than Windows 7"
date: 2014-12-02
forum: Hardware
---

### Post by uwe-bungto on 2014-12-02
I am using a Nvidia K2000 with the Nvidia binary driver - version 331.38
I ran a comparison between windows 7 and Ubuntu 14.04 on my duel boot box.

Is there any way to get more speed out of the Linux drivers; update or tweaking???

---

### Post by carlwsnyder on 2014-12-03
According to nVidia, the binary driver you should be using is the 310.xx series driver. Ref  [http://www.nvidia.com/object/linux-display-amd64-310.40-driver](http://www.nvidia.com/object/linux-display-amd64-310.40-driver)

Did you install your driver by the standard Additional Drivers menu choices?

---

### Post by uwe-bungto on 2014-12-03
> **carlwsnyder said:**
> According to nVidia, the binary driver you should be using is the 310.xx series driver. Ref  [http://www.nvidia.com/object/linux-display-amd64-310.40-driver](http://www.nvidia.com/object/linux-display-amd64-310.40-driver)

Did you install your driver by the standard Additional Drivers menu choices?
I used Settings-> Additional drivers  in 14.04 It doesn't even show the 310 series drivers Just the 331.38 and the 331.38 updates which I am using.

---

### Post by carlwsnyder on 2014-12-04
You can attempt to use the drivers from nVidia to see if they are any better, although you will have to use the instructions on the nVidia site instead of simply using the repositories.  They should be safe enough, but won't probably auto-update and may require that you manually update your kernel.  Check on installation requirements.

On some nVidia systems, I have even found the **nouveau** driver worked better than the closed source drivers.

Update: I just checked, and my Xubuntu 14.04 installation is actually using the 173.xx driver for my nVidia GeForce 7025 rather than the recommended 304.xx driver because it worked better.

---

