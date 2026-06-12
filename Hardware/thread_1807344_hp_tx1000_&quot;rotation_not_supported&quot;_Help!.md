---
title: "hp tx1000 &quot;rotation not supported&quot; Help!"
date: 2011-07-18
forum: Hardware
---

### Post by izbm on 2011-07-18
hey i have been using ubuntu on my hp tx1000 for a few months now.
My touch screen on it when i had vista was a little of in landscape mode but in portrait it worked great. 
I want to get it into portrait mode so i can use the tablet part again, But in the options for monitor it says rotation not supported i downloaded some other software and it says the same thing. 
Help please? Going on a trip soon and would love for it to work

---

### Post by Favux on 2011-07-19
Hi izbm,

Welcome to Ubuntu forums!

Which release of Ubuntu are you using?  Do you know what video chipset it has?
```
lspci | grep VGA
```
Does:
```
xrandr -o right

```
in a terminal rotate it to right portrait?  To get back to normal i.e. landscape:
```
xrandr -o normal

```

---

### Post by izbm on 2011-07-19
i belive im running 11.04 or whatever the latest version is, i a running a nvidia as for my chipset im also not sure it has a nvidia geforce go 6150

lspci | grep VGA
00:05.0 VGA compatible controller: nVidia Corporation C51 [Geforce Go 6150] (rev a2)


For the first code you gave me about xrandr i got


xrandr -o right
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  154 (RANDR)
  Minor opcode of failed request:  2 (RRSetScreenConfig)
  Serial number of failed request:  14
  Current serial number in output stream:  14

And the other one didnt do anything. Help? 
Im trying a diffrent version of the video driver so i gotta restart ill post if it changed things but i not sure

---

### Post by izbm on 2011-07-19
got the same error after i used the different driver :\

---

### Post by Favux on 2011-07-19
Are you able to use the proprietary Nvidia driver?  If so could you post the contents of your xorg.conf in /etc/X11.

---

### Post by izbm on 2011-07-19
Excuse my ubuntu noobness, i have no clue what you just asked haha

---

### Post by Favux on 2011-07-19
Well there's the open source or Xorg drivers for Nvidia.  Or if you want to use Nvidia's own proprietary drivers you go to Additional Drivers and it will detect what proprietary non-open source drivers are available for your system.  Including video drivers.

The xorg.conf is a configuration file.  In newer releases like Natty it might not even be there in the /etc/X11 directory because configuration is handled elsewhere like in xorg.conf.d .conf files etc.  But the Nvidia proprietary driver still uses it and will create a xorg.conf if needed.

---

### Post by izbm on 2011-07-20
I just upgraded to pinguy and i can rotate, BUT Its horribly inaccurate lol
Well thanks for your help good sir

---

