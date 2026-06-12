---
title: "How I got Intel sound working with my HP nx7400 laptop"
date: 2006-12-06
forum: Hardware &amp; Laptops
---

### Post by finni on 2006-12-06
UPDATE for Gutsy:

How to stop Firefox (watching videos in Youtube, etc..) from owning the whole sound card;

1. Find and install **alsa-oss** deb-package with synaptic. (or with installer of your choice)

2. Modify the file: **/etc/firefox/firefoxrc** with the following command in terminal:
```

finni@ubuntu:~$ sudo gedit /etc/firefox/firefoxrc

```
- find the following line from the firefoxrc file:
```

FIREFOX_DSP="none"

```
.. and change it to the following:
```

FIREFOX_DSP="aoss"

```
..and save the file and close gedit.

3. Restart Firefox and now the Firefox doesn't own the whole sound card when you are surfing the web anymore!

--

Hardware setup:
The HP NX7400 
- Intel 945GME motherboard (82801G / ICH7 family)
- AD1981 audio codec 
- recognised correctly by the default Gutsy (**snd_hda_intel** alsa driver)



--
Old entry:
> 
I'm a senior noob user with linux and ubuntu. (Well, few years and two laptops and three pc's) :) 

I was experiencing choppy sound and short system freezes every time any sound were played with default install of Dapper on my HP nx7400 laptop. 
Couple months I endured it, removed any system and IM sounds to reduce lagging, but still every time I used the web browser with video or audio content or watched anything with mplayer the same problems arose. So I got the problems with my system narrowed to sound card, that it was not somehow working as well as it could.

After thorough googling I found out that I could try to use different parameters with the hda-intel module and as I had HP laptop I tried adding the following in the end of '/etc/modprobe.d/alsa-base' -file :
```
options snd-hda-intel **model=hp**
```

I rebooted the laptop and sound started working without chopping and no more short system freezes. :D 

--

lspci output: 
```

$ lspci | grep Audio
0000:00:1b.0 0403: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)

```

codec info:
```

$ cat /proc/asound/card0/codec*  | grep Codec
Codec: Analog Devices AD1981
Codec: Generic 11c1 Si3054

```

P.S. I will post the links to the sources where I found the info later on.


---

### Post by finni on 2007-05-09
UPDATE: With Ubuntu Feisty 7.04 my HP nx7400 laptop's soundcard (HDAintel) seems to work out of the box. :guitar:

---

### Post by finni on 2007-06-14
:?:

Umm, does anyone know why sound seems to get occupied by Firefox?

For example if I have a youtube clip running, it occupies the sound card and other applications cannot use it at that particular time. Sometimes other sounds might get through, but they sound pretty garbled.

If anyone knows a solution, I would appreciate it.

---

### Post by nobodie on 2007-06-14
This can work with older HP's that have the motherboard that runs the ICH7 family of drivers, but the newest ones use the ICH8 family. The desktop package is working with the new ALSA 1.0.14 download and update the driver, utils and lib packages for joy, but the 1.0.14 update does not help the laptops. In fact my DV6510U can load FF but the xserver crashes, as for the sound, fuggetaboutit. I finally used SIDUX to get a desktop, but still no sound. I expect that there will be something out for them soon, but there is no date that I have been able to find out about.

---

### Post by finni on 2007-12-21
SOLVED: 

Finally found a solution. (See first post.) :guitar:

---

