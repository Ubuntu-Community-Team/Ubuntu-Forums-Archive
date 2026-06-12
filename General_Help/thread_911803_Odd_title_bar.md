---
title: "Odd title bar"
date: 2008-09-06
forum: General Help
---

### Post by glitch17 on 2008-09-06
the title bars on my active window often messes up with my visual effects set to normal. I have no extra visual things installed just Ubuntu 8.04's default. I used Envy to install my GeForce Go 6150 drivers so I doubt that is the problem could you pleas help thanks.

---

### Post by overdrank on 2008-09-06
> **glitch17 said:**
> the title bars on my active window often messes up with my visual effects set to normal. I have no extra visual things installed just Ubuntu 8.04's default. I used Envy to install my GeForce Go 6150 drivers so I doubt that is the problem could you pleas help thanks.

Hi and welcome, you may look at the FAQ's link in my signature and install emerald to help and also CCSM to help with the window decoration.

---

### Post by glitch17 on 2008-09-06
thanks but is there anyway to keep the original tile bars rather than replacing them

---

### Post by overdrank on 2008-09-06
Hi and I do not have the answer but I have moved the thread to  Desktop Effects & Customization and hopefully some one here will know. :)

---

### Post by Shazaam on 2008-09-06
I have noticed that too. Usually if you click the bar the problem goes away. Follow overdrank's advice.

---

### Post by Genius314 on 2008-09-06
> thanks but is there anyway to keep the original tile bars rather than replacing them

There are emerald themes that mimic the standard Ubuntu titlebars. You could use one of those themes, if you decide to use Emerald.

---

### Post by silverglade00 on 2008-09-09
I have been messing with this problem for a week. I understand your frustration. I just fixed it on my computer, so hopefully it will fix yours too. 

If you don't have it, install fusion-icon.

```
sudo apt-get install fusion-icon
```

Run it from the Applications-System Tools menu.

Right-click it in the Notification Area and choose Compiz Options.

Check Indirect Rendering.

Enjoy your stable title bars.

Notes: This is on a Nvidia Quadro FX 1400 with the drivers installed from EnvyNG. YMMV.

---

### Post by silverglade00 on 2008-09-09
Well, that fixed it for a while and got rid of a lot of static I was seeing in my wobbly windows. However, I just opened a terminal and it happened again. Back to the hunt...


Checking Loose Binding was even better, but still had the problem.

---

### Post by gldearman on 2008-09-09
I didn't have that problem, but I had similar problems when I used Envy to install the drivers for my NVIDIA card.  So, don't necessarily assume that the driver was installed correctly.  I had to manually change my xorg.conf file.

Specifically, I had to add this line:
```
Option "AddARGBGLXVisuals" "True"
```
To the "Device" section of my xorg.conf

These pages may help:

[http://wiki.compiz-fusion.org/Hardware/NVIDIA](http://wiki.compiz-fusion.org/Hardware/NVIDIA)
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

---

### Post by silverglade00 on 2008-09-09
I got excited, but then I looked and that was already set. Hopefully that will help the original poster though.

---

### Post by gldearman on 2008-09-09
> **silverglade00 said:**
> I got excited, but then I looked and that was already set. Hopefully that will help the original poster though.

Sorry to get your hopes up for no reason.  I do know that, at least sometimes, the line has to appear in the "Screen" section of xorg.conf as well as/instead of in the "Device" section.  Look at [thread=831385]_this guy's_[/thread] xorg.conf for an example.  Don't ask me why or how you know where to put it.

I also know that, at least at one time, there was a bug requiring you to add the line
```
Option "DisableGLXRootClipping" "True"
```
to the "Device" and/or "Screen" sections of xorg.conf when running compiz with nvidia drivers.  But I don't know why, what GLX root clipping is, or whether that bug has been fixed anyway.  So, I don't know if that is any help.

Anyway, unless you've done it already, check those two links I posted:

[http://wiki.compiz-fusion.org/Hardware/NVIDIA](http://wiki.compiz-fusion.org/Hardware/NVIDIA)
[https://help.ubuntu.com/community/Bi...erHowto/Nvidia](https://help.ubuntu.com/community/Bi...erHowto/Nvidia)

They have a whole bunch of other common bugs and fixes for running compiz-fusion with nvidia drivers.  Hope I was able to help you.

---

