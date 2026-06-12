---
title: "How do I get Graphics Drivers without getting errors?"
date: 2013-08-10
forum: Hardware
---

### Post by mrdrprofegan on 2013-08-10
Hello, I have recently switched from Windows 7 to Ubuntu and am very satisfied with the differences and improvements.  There is, however, one problem I have been having that has made me reinstall the OS multiple times.  It seems that everytime I try to install new Graphics drivers both of the bars on my desktop will not appear after rebooting.  I tried installing drivers from the ATI/AMD website and from the additional drivers tab in the software manager and both make the two bars disappear when I try to install new graphics drivers.  I haven't gotten off to a good start with Ubuntu so far, but if some one could help me with this problem it would be greatly appreciated.

---

### Post by SweetAurora on 2013-08-10
Two things, that will help everyone here immensely. 

What Ubuntu version are you using?
What Graphics card is your computer using? "ATI" isn't enough. Card Model please.

---

### Post by Yellow Pasque on 2013-08-10
> What Graphics card is your computer using? "ATI" isn't enough. Card Model please. 
Note: Often, users don't know the exact model, and when it comes to hybrid graphics laptops, all bets are off...
So, it's better to get output of:
```
lspci | grep VGA
```

---

### Post by mrdrprofegan on 2013-08-10
> **kitsuneinari78 said:**
> 
What Ubuntu version are you using?

Right now I'm using 13.04

> **kitsuneinari78 said:**
> 
What Graphics card is your computer using? "ATI" isn't enough. Card Model please.
Sorry about lack of details, after entering lspci into a terminal I got this: *VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Seymour [Radeon HD 6400M/7400M Series]*

---

### Post by mrdrprofegan on 2013-08-12
bump

---

### Post by Yellow Pasque on 2013-08-12
Have you tried manual installation? [http://wiki.cchtml.com/index.php/Ubuntu_Raring_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29](http://wiki.cchtml.com/index.php/Ubuntu_Raring_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29)

---

### Post by mrdrprofegan on 2013-08-12
I have tried downloading Catalyst from the AMD site, I haven't tried this yet though.  Thanks for the help, I'll try this tomorrow since it's getting late.

---

### Post by mrdrprofegan on 2013-08-14
I am still very new to Ubuntu and am currently using Ubuntu 13.04 and have recently tried installing the AMD/ATI Proprietary drivers again, but manually using instructions found here: [http://wiki.cchtml.com/index.php/Ubuntu_Raring_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29](http://wiki.cchtml.com/index.php/Ubuntu_Raring_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29)

Every time I try installing these drivers, the two bars disappear and I'm left with only my desktop.  I have reinstalled Ubuntu multiple times as a result of this same problem, and any help right now would be very appreciated.

---

### Post by Yellow Pasque on 2013-08-14
Why did you start a new thread? [http://ubuntuforums.org/showthread.php?t=2166550](http://ubuntuforums.org/showthread.php?t=2166550)

---

### Post by QIII on 2013-08-14
*Threads **merged***

---

### Post by Yellow Pasque on 2013-08-14
When you get stuck with no bars, press Ctrl+Alt+F1 to get to a terminal. Then, save the Xorg log to your home:
```
cp /var/log/Xorg.0.log ~/
```

Next, you can remove fglrx to get back to a working system (beats reinstalling ;) ): [http://wiki.cchtml.com/index.php/Ubuntu_Raring_Installation_Guide#Removing_Catalyst.2Ffglrx](http://wiki.cchtml.com/index.php/Ubuntu_Raring_Installation_Guide#Removing_Catalyst.2Ffglrx)

Finally, you can share the Xorg log you saved in your home directory (use [ code ][ /code ] tags, or just use pastebin.com)

---

