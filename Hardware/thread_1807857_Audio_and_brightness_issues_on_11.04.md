---
title: "Audio and brightness issues on 11.04"
date: 2011-07-19
forum: Hardware
---

### Post by salmontres on 2011-07-19
Hi guys,

Two things aren't working well in this fresh install of 11.04 on my laptop. The laptop is a Toshiba Satellite L755-S5271.

First, I can't adjust the brightness of the display. If the charger is plugged in, the brightness is set to max. If not, then it's set at a very low brightness. Ubuntu doesn't read my laptop's brightness adjuster buttons, and I don't know how to change it within the OS. Anyone else having similar difficulties?

Second, Ubuntu doesn't read my headphone jack. I have audio through my speakers, but I can't channel it to the headphones. Under 'sound preferences', all I find is the main speakers as a source of output. When I plug in my headphones, the audio continues to only come out through the speakers for some reason.

---

### Post by tptgeek on 2011-08-20
> **salmontres said:**
> Hi guys,

Two things aren't working well in this fresh install of 11.04 on my laptop. The laptop is a Toshiba Satellite L755-S5271.

First, I can't adjust the brightness of the display. If the charger is plugged in, the brightness is set to max. If not, then it's set at a very low brightness. Ubuntu doesn't read my laptop's brightness adjuster buttons, and I don't know how to change it within the OS. Anyone else having similar difficulties?



I've ran into this problem myself, and it seems that this is a common problem with the satellite series of laptops. A few other threads I've looked up suggest editing the /etc/default/grub file using gedit or your other favorite text editor. It is suggested that you insert 'nomodeset acpi_backlight=vendor' into the GRUB_CMDLINE_LINUX_DEFAULT line. I have however tried this, and it hasn't helped, and has only resulting in crashing unity upon reboot. Could you also provide information regarding whether you are running the 64 11.04 OS? There is another option which I am looking into, which requires using a bash script and binding it to said keys. I'll let you know how it turns out once I try it. You should consider looking at this forum (from which I pulled lots of info): [http://ubuntuforums.org/archive/index.php/t-1321403](http://ubuntuforums.org/archive/index.php/t-1321403)

---

### Post by .... on 2011-08-20
For headphones, try:
```
echo "options snd-hda-intel model=thinkpad" | sudo tee -a /etc/modprobe.d/alsa-base.conf
```
Restart before trying your headphones.

---

### Post by tptgeek on 2011-08-22
Oh, another quick question. Do your suspend, hibernate, screen lock, and wifi on/of switches work??

---

### Post by wahahe1 on 2011-08-22
> **.... said:**
> For headphones, try:
```
echo "options snd-hda-intel model=thinkpad" | sudo tee -a /etc/modprobe.d/alsa-base.conf
```Restart before trying your headphones.
Thank you so much. The code worked for the audio problem. I've been trying to fix it for days now. Also for brightness you should be able to right click the top or bottom panel and click "add to panel" then there should be a brightness tool there called "Brightness Applet".

---

