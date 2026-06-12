---
title: "Ubuntu/Kubuntu 5.10 display problem with Acer Aspire 5014WLMi, Mobility Radeon X700"
date: 2006-01-16
forum: Hardware &amp; Laptops
---

### Post by DarkIye on 2006-01-16
Hello everyone.

I'll keep this short - after installing either Ubuntu/Kubuntu 5.10 (goes without a hitch), and trying to boot up for the first time, I get nothing but a blank screen. Google's turned up [ and [URL="http://www.n-n-a.com/topic.php?p=1937-6067-1"]http://www.n-n-a.com/topic.php?p=1937-6067-1]("http://www.linuxformat.co.uk/index.php?name=PNphpBB2&file=viewtopic&t=1410&view=previous") (the second one being more like my problem, as I can hear a drum sound when I press enter faced with the blank screen). I have a strong feeling this can be easily be resolved by making a minor edit to /etc/X11/xorg.conf, as referred to in both links, but I'm not entirely sure where to make this, not knowing either what model the screen is (no notes on the screen or in the manual, just seems like a plain old LCD flat screen) or if the fact it's a Mobility Radeon that makes a difference. This problem has been bugging me for quite a while (it sprung up a while ago, and after a period of messing around with distros, I left it for a while and put Windows back on), and initial experiments with information gathered from the first link brought about no joy.

Thanks in advance for any help.

---

### Post by Greg2 on 2006-01-16
[QUOTE=DarkIye]I'll keep this short - after installing either Ubuntu/Kubuntu 5.10 (goes without a hitch), and trying to boot up for the first time, I get nothing but a blank screen. [/QUOTE]
Reboot in recovery mode and edit your xorg.conf with:```
 sudo nano /etc/X11/xorg.conf
``` and in the device cell where Ati driver is called, edit by adding the line:```
 Option     “noaccel”
``` Then restart the gui with:```
 sudo /etc/init.d/gdm restart
```
Please note that if you’ve never used nano or pico see man nano.

Now you have a gui but no usable Ati driver... for that go here and follow the instructions:
[http://ubuntuforums.org/showthread.php?t=78466](http://ubuntuforums.org/showthread.php?t=78466)

---

### Post by DarkIye on 2006-01-16
Thanks a bunch. I'll try that now...

---

### Post by kypez on 2006-01-16
hey man I have a toshiba laptop with a ati radeon 256mb x700. Istead of "noaccel" I tried "vesa" and it finally booted up and worked!

---

### Post by DarkIye on 2006-02-04
Nope... neither of those has worked. 'noaccel' and 'vesa' both appear to do nothing.

I'd really like to get this working, as Ubuntu seems to be the only distro I've ever tried which can autodetect everything including the touchpad without any fiddling.

If anyone's interested, this is how the new Section looks like:

```

Section "Device"
     Identifier     "ATI Technologies, Inc. Radeon Mobility X700 (RV410)"
     Driver         "ati"
     Option         "vesa"
     BusID          "PCI:1:0:0"
EndSection

```

The voices in my head are telling me the problem might lie in the 'Screen' Section, so here it is, just in case:

```

Section "Screen"
     Identifier     "Default Screen"
     Device         "ATI Technologies, Inc. Radeon Mobility X700 (RV410)"
     Monitor        "Generic Monitor"
     DefaultDepth 24
     SubSection "Display"
          Depth          1
          Modes          "1280x800" "1024x768" "800x600" "640x480"
     EndSubSection
[This Subsection is repeated 5 times to the number of 6 SubSections, the only thing changing being the Depth from 1 to 4, 8, 15, 16 and 24]
EndSection

```

---

### Post by CalvinK on 2006-02-04
I think you can get a response in [http://doc.ubuntu-fr.org/materiel/liste_portables/toshiba_satellite_m70-148?s=toshiba]("http://doc.ubuntu-fr.org/materiel/liste_portables/toshiba_satellite_m70-148?s=toshiba")
in French). It's about the same graphic card.
I hope this will help you.:-k

---

### Post by Greg2 on 2006-02-04
[QUOTE=DarkIye]
If anyone's interested, this is how the new Section looks like:

```

Section "Device"
     Identifier     "ATI Technologies, Inc. Radeon Mobility X700 (RV410)"
     Driver         "ati"
     Option         "vesa"
     BusID          "PCI:1:0:0"
EndSection

```[/QUOTE]
I believe this section should look like this:```

Section "Device"
     Identifier     "ATI Technologies, Inc. Radeon Mobility X700 (RV410)"
     Driver         "ati"
     BusID          "PCI:1:0:0"
     Option         "noaccel"
EndSection
```

---

### Post by DarkIye on 2006-02-17
Solved it. 'Driver' just had to be set to 'vesa'. No 'Option' involved.

---

