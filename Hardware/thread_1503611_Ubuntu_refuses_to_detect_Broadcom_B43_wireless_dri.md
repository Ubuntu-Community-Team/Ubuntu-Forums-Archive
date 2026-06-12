---
title: "Ubuntu refuses to detect Broadcom B43 wireless driver in my laptop, help?"
date: 2010-06-07
forum: Hardware
---

### Post by ThatHippyMan on 2010-06-07
I'm on an older model HP Pavilion dv1000, and Ubuntu just doesn't want to detect the built in wireless device.  Any help would be awesome!

---

### Post by FemmeFatale on 2010-06-07
You need to enable the restricted and multiverse software sources. Once you are done, update your repos using the GUI or 'sudo apt-get update' in your console. Then go to 'Hardware drivers' and enable your hardware.

---

### Post by ThatHippyMan on 2010-06-07
Alright, I did all of this.  Now when I am prompted to update my hardware drivers, I click activate.  From here, Ubuntu gets stuck on the "downloading and installing drivers" screen.

---

### Post by FemmeFatale on 2010-06-07
Try to repeat the procedure of activating the hardware. If no change, check if your local repos are temporary down or your internet connection is working properly. If you still have the same problem, try to install b43-fwcutter package manually.

---

### Post by trundlenut on 2010-06-07
> **ThatHippyMan said:**
> Alright, I did all of this.  Now when I am prompted to update my hardware drivers, I click activate.  From here, Ubuntu gets stuck on the "downloading and installing drivers" screen.

You do have a network connection via ethernet or similar while you try to enable the drivers don't you?

I did make the mistake of trying to do this without a network connection at one point.

---

