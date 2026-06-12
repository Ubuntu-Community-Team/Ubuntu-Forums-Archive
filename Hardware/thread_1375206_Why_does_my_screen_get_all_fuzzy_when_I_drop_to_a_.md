---
title: "Why does my screen get all fuzzy when I drop to a command line?"
date: 2010-01-07
forum: Hardware
---

### Post by josephellengar on 2010-01-07
Any time that I logout or change my tty to one that is at command line, the screen on my laptop gets fuzzy.  It's hard to explain, but it's kind of like looking through stained glass.  Also, if I log back in or change back to tty7, it doesn't get un-fuzzy.  I have to restart.  Anybody have any idea why this would be?  The computer I'm using is in my sig.

---

### Post by josephellengar on 2010-01-08
Anybody have any ideas?  (or ... bump)

---

### Post by Dougie187 on 2010-01-08
Just so you know, it's typically not a good idea to bump within the first 24 hours.

Do you have your graphics drivers installed? And if so, which version?

---

### Post by josephellengar on 2010-01-08
> **Dougie187 said:**
> Just so you know, it's typically not a good idea to bump within the first 24 hours.

Do you have your graphics drivers installed? And if so, which version?

Oh, sorry.  I do have my graphics driver installed (it's allowing me to use compiz effects and all).  According to the Nvidia X server settings thing the version is 185.18.36.

---

### Post by Dougie187 on 2010-01-08
Have you tried any other versions? you could go back to the 173 ones and see if they work, or you could go up to the 195 ones and see if they work as well.

---

### Post by josephellengar on 2010-01-08
> **Dougie187 said:**
> Have you tried any other versions? you could go back to the 173 ones and see if they work, or you could go up to the 195 ones and see if they work as well.

How do I change it?  My hardware drivers box doesn't give me any options- just that driver.

---

### Post by eldragon on 2010-01-08
if its the video mode you are talking about. its ok to have a low resolution screen under textmode. and since you have a LCD whose native resolution is not a multiple of the standard vga resolution, you get an upsampled version of the 640x480 display.

intel graphics already have what we call kernel mode setting (KMS) which basically lets the kernel set the video mode and you get a native resolution console.

with the nvidia propietary drivers, there isnt much you can do about it.

---

### Post by josephellengar on 2010-01-08
> **eldragon said:**
> if its the video mode you are talking about. its ok to have a low resolution screen under textmode. and since you have a LCD whose native resolution is not a multiple of the standard vga resolution, you get an upsampled version of the 640x480 display.

intel graphics already have what we call kernel mode setting (KMS) which basically lets the kernel set the video mode and you get a native resolution console.

with the nvidia propietary drivers, there isnt much you can do about it.

No, it's not the resolution that changes.  What changes is that everything is really fuzzy- and this is even when I'm not in textmode.  It's kind of hard to explain  Once I drop to textmode everything starts to vibrate and kind of overlap, even when I start X again.  And I know that it's not supposed to be doing that because when I take a screenshot, it shows how it's supposed to look.

---

### Post by badllama77 on 2010-01-27
This is a known problem that will be fixed in future nvidia 195.xx releases.  
see the following:
[http://www.nvnews.net/vbulletin/showthread.php?t=141204&page=3](http://www.nvnews.net/vbulletin/showthread.php?t=141204&page=3)

---

### Post by AlexZaim on 2010-01-27
Go to NVIDIA's web site and download the latest driver.
Download it in sure/easy place (like ~/Desktop)
Press ctrl alt f1 > log in > run the driver
You may need root priveleges. Try ```
sudo sh /location/to/driver 
``` 

Ps: use the tab key to generate the drivers name, in stead of writing it by hand. Like "~/Desktop/NV[tab-key-press]"

---

