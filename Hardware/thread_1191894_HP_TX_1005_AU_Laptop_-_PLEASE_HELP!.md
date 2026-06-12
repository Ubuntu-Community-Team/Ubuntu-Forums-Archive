---
title: "HP TX 1005 AU Laptop - PLEASE HELP!"
date: 2009-06-19
forum: Hardware
---

### Post by redenex on 2009-06-19
I am using TX1005 AU TouchSmart, running Jaunty 64 BIT.


Everything looks super cool, but the external speakers, headphone and microphone does not work. Can some help me activate the jacks?

Also, the sound gets killed at times......

Any idea how to activate the touchscreen and calibration?


Thanks in advance.

---

### Post by redenex on 2009-06-19
How sad! No pointers as yet? :((

---

### Post by Ayuthia on 2009-06-19
Can you post the result of lsusb?  This might help us identify your touchscreen driver.

Also, if you go into the Terminal and type:
```
alsamixer
```What does the upper left hand corner say for the Card and the Chip?  It will help us identify your sound card a little better.  You can press the escape key to exit out of alsamixer.

---

### Post by redenex on 2009-06-20
Thanks a lot for a reply Ayuthia.

Here is what it is:
[B]

Card: HDA ATI SB
Chip: Realtel ALC268[/B]

---

### Post by Ayuthia on 2009-06-20
Try the following in a Terminal:
```
sudo echo "snd-hda-intel model=toshiba" >> /etc/modprobe.d/alsa-base
```

You will most likely need to restart to get the changes to go into effect.

---

### Post by redenex on 2009-06-20
No luck yet, but this is how my alsa-base.conf looks like.

```
# Keep snd-pcsp from beeing loaded as first soundcard
options snd-pcsp index=-2

# added for sound issue
alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel
options snd-hda-intel enable_msi=1



#new

options snd-hda-intel model=laptop enable=1 index=0
options snd-hda-intel enable_msi=1

#options snd-hda-intel model=stac92xx enable=1 index=0
#options snd-hda-intel enable_msi=1

#options snd-hda-intel model=hp-m4 enable=1 index=0
#options snd-hda-intel enable_msi=1 




#jack
options snd-hda-intel index=0 model=3stack-dig position_fix=0 single_cmd=0


options snd-hda-intel model=hp 




snd-hda-intel model=toshiba

```



the last few, I added myself.

---

### Post by Ayuthia on 2009-06-20
> **redenex said:**
> No luck yet, but this is how my alsa-base.conf looks like.

```
# Keep snd-pcsp from beeing loaded as first soundcard
options snd-pcsp index=-2

# added for sound issue
alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel
options snd-hda-intel enable_msi=1



#new

options snd-hda-intel model=laptop enable=1 index=0
options snd-hda-intel enable_msi=1

#options snd-hda-intel model=stac92xx enable=1 index=0
#options snd-hda-intel enable_msi=1

#options snd-hda-intel model=hp-m4 enable=1 index=0
#options snd-hda-intel enable_msi=1 




#jack
options snd-hda-intel index=0 model=3stack-dig position_fix=0 single_cmd=0


options snd-hda-intel model=hp 




snd-hda-intel model=toshiba

```



the last few, I added myself.

Sorry.  The
```
snd-hda-intel model=toshiba
```
should be
```
options snd-hda-intel model=toshiba
```
That should work because you have the same card as mine.

---

### Post by redenex on 2009-06-22
Thanks for your help, I added that line, rebooted..... but no, the external speakers still do not work :(




[B][COLOR="Red"]EDITED TO ADD! YAHOOOOOOO!!!!!!!! YOU ARE MY HERO!!!!!!! After4months since buying this new lappy, I GOT MY external Speakers blasting music!

Thanks a lot. :)[/COLOR][/B]

---

