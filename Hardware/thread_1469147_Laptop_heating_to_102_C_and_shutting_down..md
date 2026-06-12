---
title: "Laptop heating to 102 C and shutting down."
date: 2010-05-01
forum: Hardware
---

### Post by Ikith on 2010-05-01
My laptop has been running up to 102 celsius (Critical?) then shutting down. This is obviously hot and it should obviously shut down but why the hell is it getting this hot? It never ever gets this hot on Windows not even close. Please help.

Actually this is a gaming laptop so it should handle higher heats than that.

---

### Post by tgalati4 on 2010-05-02
Most processors can be destroyed at 110-115C so 100C is a reasonable shutoff temperature.

It's not so much the processor as the substrate and connections that can't take the heat.  

What is the make and model of the laptop?  Are you running from a Live CD or did you install.  What version of Ubuntu?

If you are running any webpages with Flash, then you are doing a lot of software rendering which will cause your CPU to get toasty.  On windows, Flash uses DirectX which takes advantage of hardware/graphics rendering.

---

### Post by Ikith on 2010-05-02
MSI GX630 is the model

Ubuntu 10.04 is installed.

I don't run flash much but when I do I notice it getting hotter but most of what I do is run virtual machines.

What I am now wondering is there a way to change the fan speed to keep the laptop cooler than it usually is or am I SOL?

---

### Post by tgalati4 on 2010-05-02
Boot into the BIOS and see if there are any trip point settings for the fan.  If so, then set to 80C.

There are fan control utilities:

sudo apt-get install acpitool
man acpitool

There are advanced utilities for ibm thinkpads and toshiba laptops.  I don't know what will work with MSI so you will have to experiment.

---

