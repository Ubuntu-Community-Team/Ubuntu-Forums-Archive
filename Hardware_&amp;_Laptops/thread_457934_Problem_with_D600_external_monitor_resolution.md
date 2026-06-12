---
title: "Problem with D600 external monitor resolution"
date: 2007-05-29
forum: Hardware &amp; Laptops
---

### Post by knaveofdiamonds on 2007-05-29
Hi,

This seems to be a persistent problem, but one that I can't find any solutions for:

[http://ubuntuforums.org/showthread.php?t=436814](http://ubuntuforums.org/showthread.php?t=436814)

[http://ubuntuforums.org/showthread.php?t=422810](http://ubuntuforums.org/showthread.php?t=422810)

[http://ubuntuforums.org/showthread.php?t=392425](http://ubuntuforums.org/showthread.php?t=392425)

To recap:

I have a Dell Latitude D600 connected to a 20" Dell monitor through VGA. The external monitor should support 1600x1200 @ 60 Hz. Ubuntu 7.0.4 is installed. Graphics Card is "ATI Technologies Inc Radeon R250 [Mobility FireGL 9000]"

Despite putting the "1600x1200" mode in my xorg.conf, it doesn't work - the external monitor is "Stretched" (presumably to fit the height of 1050 pixels which is the laptop limit).

Ideal setup would be to have Dual head setup (which I have working apart from the resolution on the external monitor) - next best would be to have just the external monitor showing the correct resolution. I'm not bothered by any 3D stuff.

Things I have tried

* Tried using the flgrx driver - this broke X completely
* Tried using "ati" and "radeon" drivers - switching between the two made no difference.
* Tried using "MonitorLayout" "CRT,LFP" - this gave me a blank laptop screen, and didn't fix the external resoultion

Any help with this would be much appreciated.

Thanks
Roland

---

### Post by FerhatBingol on 2007-05-29
your solution is "915resolutions".

I have D620 and a blog entry about the same problem. [http://linux.ferhatbingol.com/?p=7](http://linux.ferhatbingol.com/?p=7)

Basically the problem in my side was the wide screen but you may have some other window size. so here is a step by step possible solution

1) Go to Synaptic Package manager and install 915resolutions
2) Open a shell and "su" to be root
3) Get your resolution list with "915resolutions -l"
4) Choose one of the unnecessary one and replace it with command "915resolution <MODENUMBER LIKE 5c> 1600 1200 32"
5) restart it with /etc/initd/915resolution start

shutdown Xserver and login back again.
 [restarting computer resets your Video BIOS and go back to defaults, so do not restart, just restart Xserver]

Good luck and mail or msg ms if you need help..

---

### Post by knaveofdiamonds on 2007-05-29
Unfortunately this doesn't work for me; I get the message:

Wrong chipset detected. 915resolution only works with Intel 800/900 series graphic chipsets.

when installing it.

A couple of other things to mention:

The resolution the monitor actually is at is 1680x1050 - giving dpi of 104x87 (instead of 96?)

Tried setting the modeline to ModeLine "1600x1200" 162.0 1600 1664 1856 2160   1200 1201 1204 1250 +hsync +vsync 

Tried setting the DisplaySize to 408 306

Neither worked.

---

### Post by FerhatBingol on 2007-05-29
915resolutions is not the only one... search for just "resolutions"

---

### Post by supremedalek on 2008-03-23
Resurrecting the old thread, AFAIK 915resolutions is for intel chipset while the D600 uses ati.

---

