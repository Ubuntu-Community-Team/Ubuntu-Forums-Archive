---
title: "Amilo Pro 2030"
date: 2006-07-10
forum: Hardware &amp; Laptops
---

### Post by acojlo on 2006-07-10
Previous week was a linux hell for me. I've experienced why is linux bad for    someone with very average computer development ability. But, the same experience also made me think the Ubuntu / Kubuntu is great linux distibution. I was mostly going through kernel and video driver compilation and installation of new software. The bottom line with kernel was to stick with 686 dapper drake kernel release.

Concerning this specific laptop, here is what works: cpu fan control, wlan, lan, dialup modem, sound, keyboard, synaptics touchpad, lcd, video, usb ports, cd/dvd combo, microphone and headphone jacks, sata drive. Firewire is detected but I do not have hardware to test it.

Main problem is video driver. Amilo 2030 have VN800 chip which, currently can not be hardware utilised for decoding mpeg2, mpeg4. There are two kinds of VN800 chips and this one in my laptop is not currently supported for hardware optimisation. Other is.

CPU fan control needed optimisation through dsdt.
Video needed compilation of Openchrome drivers and dri compilation.

Installation went well on dual boot system.

Suspend and hibernation are not working. Anyone knows how to get it work?
Few hotkeys on the keyboard do not work.

Software can be easily installed with Automatix and EasyUbuntu.
...

---

### Post by Hellkeepa on 2006-07-10
HELLo!

If you could post how you did those optimilisations, and why, I'm sure there are someone who would appreciate it greatly. ;-)

As for the hibernating / sleep not working, the steps are quite simple. However, it's kinda hit & miss if it'll work properly, as it's still under development. Also, make sure you have at enough swap to store _all_ of your RAM in it, preferably 1.5x your RAM for safety's sake.
Anyway, to activate the hibernate / sleep functions to these steps:
1. Open the "System" menu.
2. Go to the "Preferences" sub menu.
3. Click on "Power management".
4. Open the drop list for "When laptop lid is closed".
5. Select either "Suspend" or "hibernate".
6. This will prompt you to activate the support for this, and warn you about what I mentioned above. Press "Yes" / "OK" (forgot the exact text on it), and you're up and running.

You don't have to save the action, if you don't like. You'll also notice that there are some new actions available in the "log off" screen. ;-)

Happy codin'!

---

### Post by acojlo on 2006-07-10
Well it worked for you - but for me it is "disaster". Hibernate goes and then "puf!" from speakers and laptop is not turned off - it just hangs. Suspend to ram: it goes through procedure, but when I press the power buton - then laptop weaks up but - screen is off and power led is still blinking like it is still in the suspend s3 mod.

> **Hellkeepa said:**
> HELLo!

If you could post how you did those optimilisations, and why, I'm sure there are someone who would appreciate it greatly. ;-)

As for the hibernating / sleep not working, the steps are quite simple. However, it's kinda hit & miss if it'll work properly, as it's still under development. Also, make sure you have at enough swap to store _all_ of your RAM in it, preferably 1.5x your RAM for safety's sake.
Anyway, to activate the hibernate / sleep functions to these steps:
1. Open the "System" menu.
2. Go to the "Preferences" sub menu.
3. Click on "Power management".
4. Open the drop list for "When laptop lid is closed".
5. Select either "Suspend" or "hibernate".
6. This will prompt you to activate the support for this, and warn you about what I mentioned above. Press "Yes" / "OK" (forgot the exact text on it), and you're up and running.

You don't have to save the action, if you don't like. You'll also notice that there are some new actions available in the "log off" screen. ;-)

Happy codin'!

---

### Post by coady on 2007-11-26
> **acojlo said:**
> CPU fan control needed optimisation through dsdt.
Video needed compilation of Openchrome drivers and dri compilation.Hi, could you explain exactly what you did for fan optimisation and building the drivers. It may be useful to other users rather than just mentioning that it needed optimisation, as this is a common and difficult problem.

Also, I have 2GB of RAM and a 5GB swap partition (on the same FSC V2030 laptop). I can use suspend and hibernate on both my Debian and Fedora installations, but it has never worked for me under Ubuntu (I have yet to test it with Gutsy). Gusty, by the way, is the only version of Ubuntu that I have successfully upgraded. All the others died in the process and required clean installs.

---

### Post by nalle on 2008-04-09
This could help with suspend problems:

[http://ubuntuforums.org/showthread.php?t=681461&highlight=amilo+laptop+suspend+problem]("http://ubuntuforums.org/showthread.php?t=681461&highlight=amilo+laptop+suspend+problem")

---

