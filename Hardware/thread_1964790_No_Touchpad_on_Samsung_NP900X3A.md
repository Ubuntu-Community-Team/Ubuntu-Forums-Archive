---
title: "No Touchpad on Samsung NP900X3A"
date: 2012-04-24
forum: Hardware
---

### Post by preetsingh on 2012-04-24
I  have one of the newer Samsung Laptops (NP900X3B):
[http://www.amazon.com/gp/product/B006KYY15A/ref=oh_details_o00_s00_i00](http://www.amazon.com/gp/product/B006KYY15A/ref=oh_details_o00_s00_i00) 

I've tried Ubuntu 11.10, beta 12.04, and Fedora, but the mouse is being  recognized as a regular PS/2 mouse.  I can right click using two taps,  but no other multi-touch gestures are supported.  When I go to mouse  settings, I don't have the multi-touch tab either.  synclient says no synaptics driver loaded.

Here are the references I've looked at:
* [https://help.ubuntu.com/community/SamsungSeries9](https://help.ubuntu.com/community/SamsungSeries9)
* [http://jtes.net/2012/03/23/samsung-series-9-2012-np900x3b/](http://jtes.net/2012/03/23/samsung-series-9-2012-np900x3b/)
* [http://ihaveapc.com/2011/01/how-to-configure-mousetracksticktouchpad-in-linux-mint-ubuntu/](http://ihaveapc.com/2011/01/how-to-configure-mousetracksticktouchpad-in-linux-mint-ubuntu/)


 I'm sure this should be a small fix to the driver.  Please help!!   I'm stuck not using Ubuntu because of this.  All other keyboard  shortcuts including backlight and wifi, bluetooth work great.
 

Thanks

---

### Post by cortman on 2012-04-24
Have you made sure the Synaptics driver is installed? Run

```
sudo apt-get install xserver-xorg-input-synaptics
```

---

### Post by preetsingh on 2012-04-24
Correction: The thread title should be for NP900X3B

---

### Post by preetsingh on 2012-04-24
> **cortman said:**
> Have you made sure the Synaptics driver is installed? Run

```
sudo apt-get install xserver-xorg-input-synaptics
```

I've done the apt-get install but still no second tab or multitouch tab :(  Any other suggestions?

---

### Post by cortman on 2012-04-24
> **preetsingh said:**
> I've done the apt-get install but still no second tab or multitouch tab :(  Any other suggestions?

Now try the synclient commands.

---

### Post by preetsingh on 2012-04-25
> **cortman said:**
> Now try the synclient commands.

I get "Couldn't get Synaptics properties.  No synaptics driver loaded?"

---

### Post by ronogara on 2012-05-07
I have the same problem, i.e. get
"Couldn't find synaptics properties. No synaptics driver loaded?"

any thoughts? thanks!

---

