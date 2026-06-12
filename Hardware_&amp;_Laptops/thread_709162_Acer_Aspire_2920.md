---
title: "Acer Aspire 2920"
date: 2008-02-27
forum: Hardware &amp; Laptops
---

### Post by raskolikov on 2008-02-27
Hi. I'm new in linux world, so i'd like to know who have a acer aspire 2920 and Linux 7.10.
My Pc is this one ([http://notebookitalia.it/acer-aspire-2920-ultraportatile-gemstone.html](http://notebookitalia.it/acer-aspire-2920-ultraportatile-gemstone.html)).
The compiz problem with GM965 is fixed, but at the moment i can't use:
webcam
headphone
microphone
Someone have similar problems or have fixed? Thanks
Alberto

---

### Post by 16bit on 2008-03-19
yes, i have a new aspire 2920, just bought 2 weeks ago.
everything seems working find, havent found any major disaster (yet) :)

but for sure the webcam, sound jacks and compiz dont work, i havent check the modem, card reader, pcmcia, and microphone. 

my acer 2920 specs are, Intel core 2 duo T5550, HDD 160 GB, 2 GB DDR2, Monitor 12,1"r, Bluetooth 2.0 + EDR, Video Device : Intel GM965(X3100), Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller. LAN & WLAN OK.

slightly different from yours. Maybe because it is for Indonesian market.

---

### Post by Janzuka on 2008-03-27
Hi!

I'm just about to get an Acer Aspire 2920 laptop, and therefore i'd like to have answers for just a couple of questions, so as not to waste my money in vain ;) I've been an Ubuntu user for a couple of years now and will probably be running Ubuntu on the laptop as well.

1. I've read a few reviews about this laptop, and some of them claim that the fan is annoyingly noisy. Is that true?

2. The manufacturer claims that the battery will last for 4,5 hours. Have you found this to be true?

3. Have you been able to solve the problems you've encountered when using Ubuntu on this particular laptop

Thanks!:)

-Janne-

---

### Post by peterleder on 2008-03-31
how did u manage to enable wifi?

---

### Post by Gamayun on 2008-04-21
I have an Aspire 2920 running Ubuntu 8.04 64bit, standard specs apart from some extra ram and harddrive space.
At the moment there appears to be only one thing not working and that's the microphone. The webcam does not work with camorama, but that's a camorama problem, works in Cheese, Ekiga etcetera - after the V4L2 module was set.
Everything else worked without tweaking.
There are a few power management problems, suspending to ram and shutting down on low battery.
To the questions:
1: My old laptop sounded like a vacuum cleaner, so everything would seem silent in comparison. I don't think it's bad, but you definitely notice when the fan starts and stops.
2: Normally between 2 and 3 hours depending on usage. Maybe a bit more.
3: see above

---

### Post by imho74 on 2008-04-22
I have an Aspire 2920 too and most things work out of the box with Hardy Heron. I have Problems with suspend to ram because the notebook doesn't wake up again. 
There is no S-Video / TV out so I can't watch movies via TV.
After suspend to disk, when the notebook wakes up, the sound doesn't work anymore. If I want to have sound again I've to reboot. 
If have not tested if the microfon or the camera works.

Regards,
Christian

---

### Post by imho74 on 2008-04-23
I had a little success with TV-Out as I've followed the posting of nacho-wan: [http://ubuntuforums.org/showthread.php?t=9106&page=3](http://ubuntuforums.org/showthread.php?t=9106&page=3)
I've put the following lines to the Section "Device" in my xorg.conf

```

Option "monitor-VGA" "VGA"
Option "monitor-TV" "TV"
Option "monitor-LVCD" "LVCD"

```

After I had reboot the computer I had a cloned screen on my TV, but it's monochrom. 

But for this it's necessary that the intel driver is loaded:
```

sudo grep LoadModule /var/log/Xorg.0.log 
(II) LoadModule: "pcidata"
(II) LoadModule: "extmod"
(II) LoadModule: "dbe"
(II) LoadModule: "glx"
(II) LoadModule: "freetype"
(II) LoadModule: "record"
(II) LoadModule: "dri"
(II) LoadModule: "intel"
[...]

```

Regards,
imho

---

