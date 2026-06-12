---
title: "Limited Resolution"
date: 2006-12-16
forum: Hardware &amp; Laptops
---

### Post by mevets on 2006-12-16
Hi,
I have a Gateway® MX6931 Notebook that is capable of 1280 x 800 under windows, but when booted into ubuntu it can only achieve 1024 x 800, I messed around with the Screen Resolution under Prefereces, but i cannot get a better resolution.

I am an absolute newcomer to Linux and am wondering if there is an equivalent to drivers, which under windows,  this machine needs to output 1280 x 800 for Linux.

---

### Post by taurus on 2006-12-16
See what happens if you add the resolution to /etc/X11/xorg.conf!

Applications -> Accessories -> Terminal
```
sudo cp /etc/X11/xorg.conf  /etc/X11/xorg.conf.bak
gksudo gedit /etc/X11/xorg.conf
(scroll down toward the end of the file...)
```
Save it and you need to restart X by <Ctrl><Alt>Backspace or reboot.

---

### Post by mevets on 2006-12-16
It prompts me for a password. I gave it the only password I have created in Ubuntu but it failed. I am stll using the initial account created upon install of ubuntu. should I not be? Should I create another account with less privileges?

---

### Post by taurus on 2006-12-16
No, use the original or first account that you've created during the installing process.  What's the output of this command from a terminal then?

```
groups
```

Are you using Dapper or Edgy?

---

### Post by mevets on 2006-12-17
I managed to get sudo to work. I backed up the conf file, I then went to execute the next cmd and it launched gEdit and scrolled down. I then saved the file. I realized 1280 x 800 was mentioned many times and no mention of 1024  x 800. Despite this the screen resolution UI still will not give me  a choice of resolutions.

I am using Dapper.

---

### Post by macogw on 2006-12-17
try installing 915resolutions and running it to modify how your graphics work.  Intel chipsets seem to have a lot of resolution issues (which is why that package exists).  I have a very similar laptop with the same problem.  We got it working for a bit, but apparently didn't save the changes or something...

---

### Post by mevets on 2006-12-18
I installed 915resolutions using the Synaptic Package Manager. It added a few nore options to Screen Resolution, but I still do not have more than one choice of resolutions.

ps. Im getting 1024 x 768, not 1024 x 800

---

### Post by PrairieShaman on 2006-12-18
I'm having the same problem in Edgy.

---

### Post by pescarra on 2007-01-12
Good day Gens
I got Gateway MX6931 with Ubuntu Edgy installed and I managed to set the proper resolution using 915Resolution from Synaptic after reboot the resolution automatically changed to 1280x800. 
Apart from the screen resolution I'm still not fully satisfy with the whole setup ](*,) , if there is anyone interested I'd like to share tips & Tricks of How to properly set up this laptop

---

### Post by wurzia on 2008-01-05
I get the right resolution on Gateway MX6931  by setting Graphics Card to LCD 1280X1024 and resolution to 1280X800. 
Did you manage to use the microphone?

---

### Post by wurzia on 2008-01-10
use xrandr for resolution. see [http://lilserenity.wordpress.com/2007/10/15/ecstatic-xrandr-12-means-decent-linux-screen-management-at-last/](http://lilserenity.wordpress.com/2007/10/15/ecstatic-xrandr-12-means-decent-linux-screen-management-at-last/)

---

