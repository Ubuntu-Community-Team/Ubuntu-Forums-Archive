---
title: "HP mini 5101 no sound"
date: 2009-09-26
forum: Hardware
---

### Post by tommihl on 2009-09-26
Hi,


I installed Xubuntu+remix on my new netbook. Its working fine but theres this one problem. I cant get the sound. Sound card is detected and the PulseAudio is working fine. I have checked that nothing is muted ect. Theres my lspci because I guess its going to be asked:


```
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 01)
08:00.0 Network controller: Broadcom Corporation Device 4353 (rev 01)
20:00.0 Ethernet controller: Marvell Technology Group Ltd. Device 436c (rev 10)
```ie the following doesnt give anything:
```
speaker-test -Dplug:front -c2 -l5 -twav
```Never had problems like this before :( Thanks in advance!

---

### Post by tommihl on 2009-09-26
anyone?

---

### Post by tommihl on 2009-09-27
im sure that someone knows :(

---

### Post by RoMiONeT on 2009-09-27
hello,

the same problem with me ..  i have no sound , hp pavilion dv6 1205ee with ubuntu 9.04

---

### Post by tom0854 on 2009-09-28
Hey tommihl i also have the HP mini 5101, i haven't tried this yet but the mini 5101 has the same chipset and audio controller as the hp mini 1000(according to the service manuals) so have a look at this post 
[http://ubuntuforums.org/showthread.php?t=1136225](http://ubuntuforums.org/showthread.php?t=1136225)
also another workaround [http://www.ubuntugeek.com/workaround-to-get-sound-on-hp-mini-1000-or-1120-nr-with-jaunty.html](http://www.ubuntugeek.com/workaround-to-get-sound-on-hp-mini-1000-or-1120-nr-with-jaunty.html)
I haven't had a chance to try either of them yet but will confirm results when tested

if your interested in the service manuals
HP mini 1000 - [http://h10032.www1.hp.com/ctg/Manual/c01683469.pdf](http://h10032.www1.hp.com/ctg/Manual/c01683469.pdf)
HP mini 5101 - [http://h18004.www1.hp.com/products/quickspecs/13326_na/13326_na.pdf](http://h18004.www1.hp.com/products/quickspecs/13326_na/13326_na.pdf)

---

### Post by tommihl on 2009-09-28
> **tom0854 said:**
> Hey tommihl i also have the HP mini 5101, i haven't tried this yet but the mini 5101 has the same chipset and audio controller as the hp mini 1000(according to the service manuals) so have a look at this post 
[http://ubuntuforums.org/showthread.php?t=1136225](http://ubuntuforums.org/showthread.php?t=1136225)
also another workaround [http://www.ubuntugeek.com/workaround-to-get-sound-on-hp-mini-1000-or-1120-nr-with-jaunty.html](http://www.ubuntugeek.com/workaround-to-get-sound-on-hp-mini-1000-or-1120-nr-with-jaunty.html)
I haven't had a chance to try either of them yet but will confirm results when tested

if your interested in the service manuals
HP mini 1000 - [http://h10032.www1.hp.com/ctg/Manual/c01683469.pdf](http://h10032.www1.hp.com/ctg/Manual/c01683469.pdf)
HP mini 5101 - [http://h18004.www1.hp.com/products/quickspecs/13326_na/13326_na.pdf](http://h18004.www1.hp.com/products/quickspecs/13326_na/13326_na.pdf)



Thanks for the help! Unfortunately that didnt help me. Although its a known bug so maybe the fix is coming sometime. I forgot to mention that headphones works.

---

### Post by mikerbot on 2009-10-12
I have a 5101. There are plenty of guides for the older models experiencing this problem, and none of them worked for me. It was this guy: 
 
[http://aldeby.org/blog/index.php/how-to-update-alsa-to-latest-version-easily.html](http://aldeby.org/blog/index.php/how-to-update-alsa-to-latest-version-easily.html) 
 
After the script is done downloading and installing and doing its magic, you're presented with a list of options.I used the setting 'HP Laptop with headphone jack switch,' which is number 8. The codec on my machine is AD1984A. Worked like a charm after restart!

Also, I later upgraded to the beta of 9.10, and it still worked, I don't know if that means that 9.10 has better support for the 5101, or it kept my alsa setup.

9.10 works beautifully on the 5101. And my broadcom wireless card had no problems (it asks you very politely if you would like to use the restricted drivers from broadcom) I suggest at least trying out a live copy.

---

### Post by tommihl on 2009-10-25
> **mikerbot said:**
> I have a 5101. There are plenty of guides for the older models experiencing this problem, and none of them worked for me. It was this guy: 
 
[http://aldeby.org/blog/index.php/how-to-update-alsa-to-latest-version-easily.html](http://aldeby.org/blog/index.php/how-to-update-alsa-to-latest-version-easily.html) 
 
After the script is done downloading and installing and doing its magic, you're presented with a list of options.I used the setting 'HP Laptop with headphone jack switch,' which is number 8. The codec on my machine is AD1984A. Worked like a charm after restart!

Also, I later upgraded to the beta of 9.10, and it still worked, I don't know if that means that 9.10 has better support for the 5101, or it kept my alsa setup.

9.10 works beautifully on the 5101. And my broadcom wireless card had no problems (it asks you very politely if you would like to use the restricted drivers from broadcom) I suggest at least trying out a live copy.


That didnt work. But Im putting my hope on 9.10. Wich is going to be released in next week if I remember right. Ubuntu is a good OS but hardware compability is too bad. Even tough that bothers evey UNIX.

---

### Post by mikerbot on 2009-10-25
Well thats weird. Did the script not run correctly or did it just not work? Do you have sound from the headphone jack? A lot of people are just having problems with the speakers. And others report random muting.

---

### Post by tommihl on 2009-10-26
> **mikerbot said:**
> Well thats weird. Did the script not run correctly or did it just not work? Do you have sound from the headphone jack? A lot of people are just having problems with the speakers. And others report random muting.


It ran correctly but it didnt fix the problem :( Headphone jack works fine.

---

### Post by mikerbot on 2009-11-01
Did 9.10 fix it? If it didn't, I'll reinstall and go through all the steps I took again and try to isolate a cohesive workaround, I suspect this will continue to be an issue in the HP 311's and onward. Pain in the butt.

---

