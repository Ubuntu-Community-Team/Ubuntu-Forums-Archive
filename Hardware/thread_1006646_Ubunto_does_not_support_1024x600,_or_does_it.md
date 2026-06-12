---
title: "Ubunto does not support 1024x600, or does it?"
date: 2008-12-09
forum: Hardware
---

### Post by perstromgren on 2008-12-09
Ubuntu does not support the 1024 by 600 pixel display I have on my Eee 901. If nothing else, it is obvious by the egg-shaped Ubuntu logo at startup. The problem can also be seen by the Gnome desktop that does not show both top and bottom bars.

Or, did I miss something?

Per.

---

### Post by phidia on 2008-12-09
What video card do you have in that and have you looked at/enabled your System > Administration > Hardware Drivers? Also look at Screen resolution from System > Preferences.

---

### Post by perstromgren on 2008-12-09
> **phidia said:**
> What video card do you have in that and have you looked at/enabled your System > Administration > Hardware Drivers? Also look at Screen resolution from System > Preferences.

I have no idea what video card it is using, and the Drivers list you refer to is empty, I'm afriad.

Per.

---

### Post by phidia on 2008-12-09
> lspci | grep VGA entered in a terminal (from Applications > Accessories)
should tell you what your card is. You can look at the Ubuntu video wiki here for ways to get the best function from your card.

---

### Post by perstromgren on 2008-12-30
> **phidia said:**
> entered in a terminal (from Applications > Accessories)
should tell you what your card is. You can look at the Ubuntu video wiki here for ways to get the best function from your card.

Thanks, I will look for it there. At any rate, this is what lspci says:

"00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)"

Per.

---

### Post by steveneddy on 2008-12-30
Ubuntu is capable of this resolution.

---

### Post by eyal_allweil on 2009-02-19
I also have Intrepid Ibex running on an EEE 901, and am stuck at 800*600 - I can't get it back to 1024*600. This option doesn't show up in my System->Preferences->Screen Resolution. But I'm sure I saw it before - I think connecting my EEE to an external monitor somehow "lost" me this option. I'd love to have it back at 1024*600 without a fresh install!

---

### Post by eyal_allweil on 2009-02-25
So I finally solved my problem by using a Xandros-generated xorg.conf meant for the EEE. That allowed me to get 1024*600 on both my external monitor and the EEE's monitor. By increasing the size of the virtual desktop, I could also drop the mirroring and get an extended desktop working.

---

