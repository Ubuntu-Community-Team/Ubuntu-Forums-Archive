---
title: "Toshiba Satellite Pro A120 sound problems"
date: 2009-07-01
forum: Hardware
---

### Post by toontastic on 2009-07-01
I've had a search through the forums and on google but most suggestions don't seem to be working for me. Basically I have been given a Toshiba Satellite Pro A120 for work. I quickly installed Ubuntu only to find the sound isn't playing. 

I ran 

```
cat /proc/asound/card0/codec#* | grep Codec
```

Where I recieved 

```
Codec: Realtek ALC262
Codec: LSI Si3054
```

I then made changes in the alsa-base.conf and added the last line as options snd-hda-intel model=basic, options snd-hda-intel model=3stack and options snd-hda-intel model=toshiba none of which seemed to make any difference. 

I have looked in the sound icon and all sounds are at the top and also checked in alsamixer but everything seemed ok in there.

Any help would be much appreciated. Thanks.

---

### Post by toontastic on 2009-07-05
It's been 4 days now I hope nobody minds me bumping this.

---

### Post by mtn on 2009-09-03
I have just upgraded my Toshiba Satellite Pro A120 from Ubuntu 9.04 to 9.10 (early I know!). The sound worked fine with 9.04 but is not working in 9.10. Did you have any joy getting the sound to work on your A120?

---

### Post by toontastic on 2009-09-14
> **mtn said:**
> I have just upgraded my Toshiba Satellite Pro A120 from Ubuntu 9.04 to 9.10 (early I know!). The sound worked fine with 9.04 but is not working in 9.10. Did you have any joy getting the sound to work on your A120?


Fraid not, I tried to install Windows on another laptop the exact same brand however and had the same problem. Turns out it was a BIOS issue and an upgrade on the BIOS fixed the issue for Windows. I've not really had time to look at whether I can upgrade the BIOS through Ubuntu, the software they provided was Windows only.

---

### Post by nate_noob on 2010-02-01
Just in case anyone else is having this problem, try the System, Administration, Hardware Drivers and disable the modem driver (unless of course anyone out there is actually still using dial up!)

My sound now works fine!

Nate

---

