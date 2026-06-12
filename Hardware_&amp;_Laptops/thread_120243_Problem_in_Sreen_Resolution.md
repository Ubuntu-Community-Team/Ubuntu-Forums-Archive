---
title: "Problem in Sreen Resolution"
date: 2006-01-21
forum: Hardware &amp; Laptops
---

### Post by mr47 on 2006-01-21
I have installed Ubuntu operation system (version 5.10) as second OS  (another OS is Windows XP). When I used "live CD" for trying safely, the sreen resolution was 640*480 and the refresh rate was 60 Hz. So that was inconvient for my eyes. I change them by access System --> Change Resolution, but it has only 640*480 and 60 Hz, I have no another choice. First I thought I used live CD, so cause that problem. 

Then, I installed Ubuntu by "install CD". The install  process seemed successful, no problem happened. But I also CAN NOT change the sreen resolution and refresh rate, even I used the admin (root) account. I don't know why. The Windows system is still normal, the sreen resolution is 800*600 and the refresh rate is 75 Hz.

My computer configurations are: 
[INDENT]Mainboard chipset Intel 845 G
CPU Celeron 2.4 GHz
512 MB DDRam
VGA onboard 
HDD 80 GBs
Monitor CRT 15 inches[/INDENT]

I hope someone can help me to solve that problem. Thanks.

---

### Post by cayamara on 2006-01-21
[QUOTE=mr47]I have installed Ubuntu operation system (version 5.10) as second OS  (another OS is Windows XP). When I used "live CD" for trying safely, the sreen resolution was 640*480 and the refresh rate was 60 Hz. So that was inconvient for my eyes. I change them by access System --> Change Resolution, but it has only 640*480 and 60 Hz, I have no another choice. First I thought I used live CD, so cause that problem.[/QUOTE]
The key is to edit xorg.conf:
```
$ sudo gedit /etc/X11/xorg.conf
```
There, edit the refresh rates to allow higher resolution. My moitor section for example is ```
Section "Monitor"
	Identifier	"JT198x4"
	Option		"DPMS"
	[B]HorizSync	30-65
	VertRefresh	50-75[/B]
EndSection
``` where HorizSync and VertRefresh are the horizontal and vertical refresh rates.

Hope it works ;).

---

### Post by 23meg on 2006-01-21
For further help see [this thread]("http://www.ubuntuforums.org/showthread.php?t=83973").

---

### Post by mr47 on 2006-02-08
Thank you all. Now I have solved this problem. And a happy news is I have change my old monitor to a new monitor (17 inches). I like Ubuntu and thanks again. :KS \\:D/

---

