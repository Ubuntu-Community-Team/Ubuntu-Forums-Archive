---
title: "Digital ATI Radeon X1300"
date: 2009-08-02
forum: Hardware
---

### Post by CynicalVulture on 2009-08-02
Sorry if this has already been solved somewhere.

I'm running ubuntu 9.04. I'm running an ATI Radeon X1300 with dual screens, I believe I'm using the default drivers, but I'm not entirely sure how to check. One screen is an old CRT monitor connected to the analog slot, and I haven't had any trouble with it. The other is a Dell 19" flatscreen in the digital slot. The digital screen has developed an extremely irritating flicker, that tends to be worse after periods of inactivity. I haven't had any luck finding a fix myself, hoping someone here knows a fix. 

Thanks!

---

### Post by NormanFLinux on 2009-08-03
Install the open source drivers. You'll have to fix the xorg.conf file to get the Radeon driver running in place of the standard vesa driver. Updating your drivers will also fix an annoying screen flicker. I have desktop effects and compiz enabled on Kubuntu 9.04. The proprietary ATI drivers do nothing but bring up a black screen.

So far so good.

---

### Post by CynicalVulture on 2009-08-03
Sorry, I'm still learning, could you be a little more in depth? What are the open source drivers called? And how do I need to fix the xorg file? Thanks!

---

