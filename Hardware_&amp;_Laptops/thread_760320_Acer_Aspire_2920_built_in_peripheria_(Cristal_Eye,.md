---
title: "Acer Aspire 2920 built in peripheria (Cristal Eye, mic, headset jack)"
date: 2008-04-20
forum: Hardware &amp; Laptops
---

### Post by csmozes on 2008-04-20
Hi there, 

Pliiz help. I am an Ubuntu beginner but read all the posts found here - still no good results. 

My Egika detects the built in Cristal Eye webcam of my Acer (T5450, X3100) but saying that there is a problem when opening the Acer Cristal Eye webcam. "Seems that the videodrives is not supporting any of the color schemes used by Egika. Please check the kernel documentation to detect the suported palettes" 

I tried to instal Kopete reading here that Kopete can set the Cristal Eye properly - not mine. 

How to proceed? 

Many thnx. 

Other issues might be to set the built-in mic as well as the jack of the headset to work. 

mozes

---

### Post by linuxwizard on 2008-04-20
You may have to work with the settings > Open Ekiga > Edit > Preferences > Video > Video Devices > try changing some of the settings.( Video Plugin if it shows V4L change to V4L2)

---

### Post by FredB on 2008-04-21
> **csmozes said:**
> Hi there, 

Pliiz help. I am an Ubuntu beginner but read all the posts found here - still no good results. 

Welcome.

> My Egika detects the built in Cristal Eye webcam of my Acer (T5450, X3100) but saying that there is a problem when opening the Acer Cristal Eye webcam. "Seems that the videodrives is not supporting any of the color schemes used by Egika. Please check the kernel documentation to detect the suported palettes" 

I have an Acer Aspire 5520 with hardy on it. Cheese recognized the webcam and use it without problem.

> I tried to instal Kopete reading here that Kopete can set the Cristal Eye properly - not mine. 

Are you sure Kopete will use it ? How about KDE-like cheese software ?

> How to proceed? 

Many thnx. 

Other issues might be to set the built-in mic as well as the jack of the headset to work. 

mozes

Cannot help here, sorry :(

---

### Post by csmozes on 2008-04-21
Hi pals, 

Thank you for welcoming me. 
As a beginer it took me some time to understand what compiz and such expressions would be. Their meaning are still unclear for me but I made progresses. 
I updated my Ubuntu to 8.04 and the webcamera works well with Skype but not with Egika (the same massege is given). The front headphone jack is working as well but there is no more microphone. Any suggestions what and how to do? 

mozes

P.S. The starting up panel is embarrasing: I have the 8.04 (...) 16 and its recovery... as well as the 14 and recovery. For what are these good for? 
:confused:

---

### Post by chritoph on 2008-05-07
Awfully, I suffer from the same problem:
Neither the internal microphone nor the microphone front jack work for me.
Help!:(

---

### Post by imho74 on 2008-05-18
I did not solve the problem yet but I think I have done a step in the right direction:

I have written the following line in "/etc/modprobe.d/snd-hda-intel.modprobe", this file must be created, and "/etc/modprobe.d/alsa-base" (at the bottom in the last line):

```
options snd-hda-intel model=acer position_fix=0 enable=yes
```

After a restart I have started alsamixer and I have turned on all channels as far as they will go. Now I can hear my voice through the speackers. But I can't record it with the sound recorder.

Maybe this will guide you to your next successful step with the mic.

Regards,
imho

---

### Post by imho74 on 2008-06-22
There is hope for the proper use of the microphone: I tested the live CD of OpenSuSE 11.0 with kernel 2.6.25 and the mic works out of the box. It seems that we have to wait till october and the problem will be solved with Intrepid Ibex. :)

---

### Post by imho74 on 2008-06-25
I was always wondering why my Cristal Eye webcam works sometimes and sometimes not. I thought that I need another package/program to get it work. Now I know that the installation of my dvb-t stick is the reason why the uvc based webcam did not work anymore.

Here is a solution for that: [http://lists.berlios.de/pipermail/linux-uvc-devel/2008-February/003088.html]("http://lists.berlios.de/pipermail/linux-uvc-devel/2008-February/003088.html")

---

