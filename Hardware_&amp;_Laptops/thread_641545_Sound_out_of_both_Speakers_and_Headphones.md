---
title: "Sound out of both Speakers and Headphones"
date: 2007-12-15
forum: Hardware &amp; Laptops
---

### Post by tofaffy on 2007-12-15
I have an Acer Aspire 3050 (AMD Sempron/Realtek HD)

When I plug my headphones into my laptop, I get sound from both the laptop speakers and the headphones. I've tried turning down the PCM volume and turning the headphones on in gnome-volume-control. Still no luck. Thanks in advanced!

---

### Post by Greenmanspirit on 2007-12-22
I have been having this same problem. I am using a hp laptop dv1000 series. I tested this with both ubuntu 7.10 and kubuntu 7.04 on both a desktop and laptop. All configurations giving the same problem as tofaffy said.

---

### Post by Bartender on 2007-12-22
Acer 5920 here.  Intel audio.  Same deal - headphones don't kill the lappy speakers, regardless of "Switch" box in the gnome volume control applet.
Also, I only get the right channel on the lappy, but headphones sound fine.

---

### Post by LuisC-SM on 2007-12-22
> **tofaffy said:**
> I have an Acer Aspire 3050 (AMD Sempron/Realtek HD)

When I plug my headphones into my laptop, I get sound from both the laptop speakers and the headphones. I've tried turning down the PCM volume and turning the headphones on in gnome-volume-control. Still no luck. Thanks in advanced!
Open a terminal and use
```
$ alsamixer
```
From there you can mute, unmute and get the volume higher or lower
Cheers
Luis

---

### Post by LuisC-SM on 2007-12-22
> **Bartender said:**
> Acer 5920 here.  Intel audio.  Same deal - headphones don't kill the lappy speakers, regardless of "Switch" box in the gnome volume control applet.
Also, I only get the right channel on the lappy, but headphones sound fine.

Maybe this thread can hellp you
[http://ubuntuforums.org/showthread.php?t=494467&highlight=Acer+5920+here.+Intel+audio](http://ubuntuforums.org/showthread.php?t=494467&highlight=Acer+5920+here.+Intel+audio)
Cheers
Luis

---

### Post by miscast on 2008-01-01
Hey guys, I had this exact problem and found a fix for my Toshiba Satellite A200-1DA.

The problem seems to be with the Intel High Definition Audio soundcard (lspci | grep -i audio will give you the name of your soundcard).

The solution seems to revolve around editing/creating a configuration file in /etc/modprobe.d (you can edit alsa-base for example) and inserting an 'options' line.

The command is of the form options snd-hda-intel model=[MODEL], where selecting the correct [MODEL] can fix the issue (and when I say correct I don't necessarily mean the actual model of your chipset, you just have to select one that fixes this!!!).

The [MODEL] that fixed the issue for me was 'lenovo' (took LOTS of googling to find that one... lost link to site I found it on though). I also needed a reboot.

So in conclusion, here is the method I used to fix the issue:

```
$ sudo vi /etc/modprobe.d/sound-hackery
options snd-hda-intel model=lenovo
[save file]
[reboot]
```

I know this issue is duplicated in several places but I don't have time to post in every one, if anyone wants to link to this (if this does indeed help anyone) then please do.

---

### Post by wollanooo on 2008-01-23
strangely enough, the trick from LuisC-SM of opening alsamixer works for me.
It looks like it is a separate entity from the gnome volume control

---

