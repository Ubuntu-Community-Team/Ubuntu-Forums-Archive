---
title: "Laptop resolution for nvidia 9600gt"
date: 2008-08-31
forum: Hardware
---

### Post by ubunt_user on 2008-08-31
I have a geforce 9600gt card on my laptop with Ubuntu 8.04 installed.
The installation went smooth. But I am having problem with my screen resolution. It gives me only 2 options : 640x480 and 800x600
I know that card supports more than this since I use higher resolution when working in Windows. Searched the forums and came to know something about installation of nVidia drivers to increase the resolution.
As I am quite new to Linux I am not aware if this will increase the res.
If it is,then can some please guide about how to install these drivers and the configurations to be done?
Thankyou.

---

### Post by IntuitiveNipple on 2008-08-31
As you know something about the nvidia driver options, is the system using the Nvidia driver from the Ubuntu Restricted Drivers (System > Administration > Hardware Drivers) ?

If so, have you installed the nvidia-settings utility and used that? If not, from a command-prompt do
```

sudo apt-get install nvidia-settings

```
You'll find the program at Applications > System Tools > Nvidia X Server Settings.

You should be able to successfully configure the display using that.

---

### Post by ubunt_user on 2008-09-02
Great. The nVidia chkbox at System > Administration > Hardware Drivers did the trick. 
But 2 things here : 
1. I get a much larger list of resolutions to choose from as compared against Vista. S,o can I go ahead and say select 1440x900 (example) resolution even if its not displaying in Windows but coming as an option in Ubuntu?
2. Since the resolution list is getting populated, so I still need to install nvidia-settings?

---

