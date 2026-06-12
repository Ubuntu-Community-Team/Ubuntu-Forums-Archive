---
title: "installing ATI drivers on laptop"
date: 2008-01-24
forum: Hardware &amp; Laptops
---

### Post by AvengingAngel718 on 2008-01-24
i'm helping a friend set up Gutsy on his laptop. I thought it would be a simple task since i've set up an ubuntu desktop about 3 times before, but for some reason a lot of things dont work on the laptop architecture the way i thought they would, although i'm figuring things out. to complicate matters further, however, he has an ATI graphics card, which of course doesnt have the drivers installed by default and i cant figure out how to install them. can anyone walk me through this? i'm going to look around the forums a bit more and try to figure this out, but any help would be appreciated

---

### Post by ravenon on 2008-01-24
Without knowing what ATI card it is difficult to say which driver to use. One approach, and Gutsy should have configured this way is to use the open source ATI driver. Edit xorg.conf and see which driver is being used; if it says vesa, change it to ati and restart the X-server.

If that does not work, and for some cards it may not, you can put vesa back in the xorg.conf, restart the X-server and then to to System/Administration/Restricted Drivers Manager. It should give an option for installing the proprietary fglrx driver. If not, you can install it through synaptic (search for fglrx) and change the driver line in xorg.conf to fglrx.

Again, all this depends on which card.

---

### Post by bonzini on 2008-01-24
I have a going - on - three - year - old Toshiba with an ATI IGP card.  If this sounds like what you've got I can give you some pretty specific advice.  However, in general, if the video card is a bit older, you probably want to try out both the open source Xorg driver (often called the Radeon driver) and the driver from ATI.  For example, in my case, the ATI driver does not support the 3D and transparency needed for Compiz; so I need to use the Radeon driver.

Good luck.

---

### Post by Yellow Pasque on 2008-01-24
If your card is Radeon 9500 or newer (that includes X-series, X1k-series, HD2k, HD3k). You can use this guide: [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)

---

### Post by Cygoku on 2008-01-24
Get [Envy]("http://www.albertomilone.com/nvidia_scripts1.html").  It installs nVidia and ATI driver for everyone with asslefree! :)

Cygoku

---

### Post by Yellow Pasque on 2008-01-24
> **Cygoku said:**
> Get [Envy]("http://www.albertomilone.com/nvidia_scripts1.html").  It installs nVidia and ATI driver for everyone with asslefree! :)


I've seen more people report success with the guide than with Envy.

---

### Post by Cygoku on 2008-01-27
> **Temüjin said:**
> I've seen more people report success with the guide than with Envy.It's the opposite for me.

plzkthxbye

Cygoku

---

