---
title: "Need to change graphics driver but need a plan"
date: 2010-09-21
forum: Hardware
---

### Post by brevardo on 2010-09-21
I have recognized that I need to upgrade by graphics hardware driver. I have installed Jaunty on my Dell Laptop Latitude D620 and it's running very hot & loud. I had the same problem for the past three months with Karmic. The problem that I ran into though was that when I had Karmic I tried to install a better driver and then when I went to reboot I could not see the screen. The screen was broken into four sections and so blurry that I couldn't do anything and I had to reinstall. I happened to have an old Jaunty cd so I reinstalled that. Now I want to attempt to get the restricted driver or the best driver to use for this laptop. However I need to know what to do in case the screen goes unrecognizable again. Is their a way that I can boot and then enter a terminal command from boot? And then what command do I use to get back to where I was previously so I can at least see the screen. Please advise?   Thanks,  Rich H

---

### Post by coffeecat on 2010-09-21
You might want to post details of your graphics card so that people can advise you better. 

If you don't know that and you can still get into a GUI, open a terminal and post the output of:

```
lspci | grep -i vga
```

---

### Post by brevardo on 2010-09-21
Good idea Coffeecat- Here's what it shows:

richard@richard-laptop:~$ lspci | grep -i vga
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
richard@richard-laptop:~$

---

### Post by waynefoutz on 2010-09-21
My daughter has that same machine. The open source driver installed out of the box in Lucid works fine on it.

---

### Post by coffeecat on 2010-09-22
What was the "better" driver that you tried to install? As waynefoutz says, the Intel driver that comes in the box works fine with the 945 chipset. There was a probem with the intel driver and some intel cards with Karmic, but I don't think it affected the 945. I have that chipset on an older laptop and if I remember correctly Karmic was fine. I don't use it now so I'm not sure which was the last version I ran on it.

Anyway, there is no restricted driver for intel cards as far as I am aware. Intel themselves produce the open source driver that comes as default in an Ubuntu installation. The running hot and the screen artifacts suggest the possibility of a hardware problem. Do you have Windows on that machine as well, or just Ubuntu? If Windows, is the display OK when running Windows?

---

