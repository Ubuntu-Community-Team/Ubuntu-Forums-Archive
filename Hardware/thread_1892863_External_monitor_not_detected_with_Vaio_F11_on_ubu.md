---
title: "External monitor not detected with Vaio F11 on ubuntu 11.10"
date: 2011-12-08
forum: Hardware
---

### Post by brar on 2011-12-08
Hi,

I have sony vaio f11 series laptop with nvidia 330m graphics card. I am trying to connect my external monitor to it but its not detected by ubuntu 11.10. If I go into "Displays" and press "Detect Displays" nothing happens. My existing laptop screen is shown as unknown. I have Nvidia's proprietary drivers installed. I searched and many people had suggested using "nvidia-settings" but that also doesnot show my external monitor. I have tried using vga as well as hdmi cable and restarted various times but the monitor is not detected. 

Thanks

Solved: Installed the latest nvidia drivers from [http://www.nvidia.com/Download/index.aspx](http://www.nvidia.com/Download/index.aspx) and the monitor started showing in nvidia-settings

---

### Post by brar on 2011-12-09
*bump*

---

### Post by brar on 2011-12-09
I booted using ubuntu live cd and there both of the monitors work. So the nvidia drivers have a problem or I am doing something wrong. Any pointers.

---

### Post by Raval on 2012-02-03
> **brar said:**
> I booted using ubuntu live cd and there both of the monitors work. So the nvidia drivers have a problem or I am doing something wrong. Any pointers.

This is the exact problem I have. With the live CD everything worked but not on the install.

---

### Post by brar on 2012-02-03
> **Raval said:**
> This is the exact problem I have. With the live CD everything worked but not on the install.

Check my OP for resolution. Updating the video drivers from nvidia website fixed my problem

---

### Post by cyrille_bartholomee on 2012-05-02
Had exact the same issue. Found out that live cd is using nouveau drivers and not nvidia. Purged everything except nvidia-common package and rebooted. Now everything works perfect!

---

