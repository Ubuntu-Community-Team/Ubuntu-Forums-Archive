---
title: "Resolution with NVIDIA Quadro NVS 295 larger than monitor"
date: 2009-08-04
forum: Hardware
---

### Post by bensei on 2009-08-04
Hello:


I have just installed Ubuntu 9.04 on a new Desktop (Dell Precision T5500) with graphics card 256MB NVIDIA Quadro NVS 295, DUAL MON, 2 DP. I have attached one flat monitor with 1920x1200 native resolution. I have activated the nvidia accelerated graphics driver (version 180). Using "sudo nvidia-settings" to access and modify settings, my monitor and native resolution are detected.

The problem I encounter is that the screen image is larger than the monitor, i.e. on all four sides (top, bottom, left, right), a chunk of the 1920x1200 resolution is not displayed. Is can be accessed by the mouse, though. This problem occurs both for the login screen as for my actual gnome screen.

I can sort of circumvent this problem by using "nvidia-settings" to change the resolution to 1680x1050 without rescaling, in which case I now have a black margin around my screen area.

Does anyone know about this problem and potential fixes?


Thanks,
Ben

---

### Post by latev on 2009-08-05
I seem to have a very similar issue with my 9800 GT card and my two displays - a DVI 1280x1024 monitor and a 1152x864 VGA projector.

I haven't found the solution yet, but seems to me it's an NVidia driver issue because it happens when I have two displays configured at different resolutions

/see my other posting: [http://ubuntuforums.org/showthread.php?t=1231916/](http://ubuntuforums.org/showthread.php?t=1231916/)

Unplugging /NOT disabling/ the second one enables me to select the right resolution and have my monitor function properly. See if this works for you
/I know this is NOT a solution at all/

---

### Post by bensei on 2009-08-05
Thanks for the info.

In my case, the problem occurs with just a single monitor.

I was wondering whether the type of connection could be a problem, but everything works perfectly under Windows.

Are there any known issues with the latest nvidia driver?


Thanks,
Benni

---

### Post by bensei on 2009-08-10
bump (please help)

---

### Post by latev on 2009-08-10
Yes, 99% it's a linux drivers issue. The worst thing is that there's nothing you can do about it but wait for somebody else to eventually solve your problem. I gave up the battle again /for the Nth time/ and installed vista - I'm able to watch TV now and my projector configuration works properly too.
I'll give Linux another try in mid 2011 probably

---

### Post by Musashi 360 on 2009-08-20
Maybe this could help: [http://ubuntuforums.org/showpost.php?p=7819514&postcount=7](http://ubuntuforums.org/showpost.php?p=7819514&postcount=7)

---

