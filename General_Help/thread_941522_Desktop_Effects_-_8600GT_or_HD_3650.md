---
title: "Desktop Effects - 8600GT or HD 3650"
date: 2008-10-08
forum: General Help
---

### Post by teabeartom on 2008-10-08
Hi,

I currently have an ati x300 mobility video card and have been unable to ever get compiz working AND play video without tearing.

After three years, the time has come to get a new computer (desktop this time.)  I am debating between the NVIDIA 8600gt card or the ATI Radeon HD 3650, both with 1 GB VRAM.  Does anyone have any experience running these with compiz?  I want to make sure that they can play video smoothly while running compiz.  With the ATI, do the open source drivers work well, or do I have to go proprietary?

Also, have the proprietary ATI drivers improved over the past year?  Are NVIDIA's linux drivers still the better of the two?  

Alternatively, if there is a cheaper video card that will do the trick, please let me know.  I will be running at 1920x1200 resolution if that makes a difference.  Thanks in advance for any suggestions!

I will be getting an intel core 2 quad Q9550 2.83 ghz.  When the video teared on my laptop with Compiz installed, the CPU maxed out (1.73 ghz pentium-m), so perhaps the processor will be good enough to stop video tearing...

---

### Post by reahjw6 on 2008-10-08
Hey i use a xfx 8600gt and have had no problems at all.
Sorry cant help with other gpu.

---

### Post by loomsen on 2008-10-08
I have a 8600M GT, no problems with Ubuntu.
If you prefer debian you should prepare for some xorg.conf hacking.
NTL, I actually run Intrepid, and everything works fine for me. Just added my Toshiba LCD to my xorg.conf and everything works just fine, compiz, two separate screens, which makes basically two computers out of one. Each screen is configurable through compiz. This is only of interest if you plan to run two screens with different resolutions.

However, a good friend of mine has an Ati card, and has to suffer way more than me. For example Ati currently doesnt support TV-outs at the moment. Tho I'm sure they will in the future, it's often like that. nVidia is clearly ahead with driver support for linux machines, so I'd recommend buying the 8600GT rather than any Ati card. At the moment my bud isn't even able to run simple clone-output.

Just my 2ct tho.

---

### Post by teabeartom on 2008-10-09
Thanks!  

I think I will go with the 8600gt then.  I wasn't sure if ATI had become good enough in the past year, but if there still are some bugs, I would prefer to live without them.

---

### Post by presence1960 on 2008-10-10
I have an Nvidia 8600GT and have had absolutely no problems. Have my desktop effects at custom, use compiz and plays video no problem. Used EnvyNG for driver and all is well. I find this card is an exellent product.

---

### Post by el-mar01 on 2008-10-10
NVIDIA drivers are far superior to ATI drivers.

---

### Post by loomsen on 2008-10-10
#2 && #3
*signed*

---

### Post by borlosky on 2008-11-12
i use 8600gt (only 512m vram in mine though), and everything runs flawlessly.

---

### Post by hardyn on 2008-11-12
Suse / ATI have been working hard on the radeonHD project; the opensource ATI driver... they have come A LONG way in 6mo... its actully pretty exciting.  I would bet a fully featured opensource driver in 1 year.

its development can be monitored at phoronix.
[http://www.phoronix.com/scan.php?page=article&item=radeonhd_122_123&num=1](http://www.phoronix.com/scan.php?page=article&item=radeonhd_122_123&num=1)

---

### Post by impact on 2008-11-12
> **hardyn said:**
> Suse / ATI have been working hard on the radeonHD project; the opensource ATI driver... they have come A LONG way in 6mo... its actully pretty exciting.  I would bet a fully featured opensource driver in 1 year.

its development can be monitored at phoronix.
[http://www.phoronix.com/scan.php?page=article&item=radeonhd_122_123&num=1](http://www.phoronix.com/scan.php?page=article&item=radeonhd_122_123&num=1)

It will be great, one day. :) But right now, NVIDIA and their closed driver is probably the best bet.

Edit: apparently not all is great for the 8600GT - [http://www.theinquirer.net/gb/inquirer/news/2008/07/09/nvidia-g84-g86-bad](http://www.theinquirer.net/gb/inquirer/news/2008/07/09/nvidia-g84-g86-bad)

---

### Post by Skripka on 2008-11-12
> **hardyn said:**
>  I would bet a fully featured opensource driver in 1 year.

its development can be monitored at phoronix.
[http://www.phoronix.com/scan.php?page=article&item=radeonhd_122_123&num=1](http://www.phoronix.com/scan.php?page=article&item=radeonhd_122_123&num=1)

Hmmm...considering the proverbial "room full of monkeys typing on GNU eMacs" could write better drivers than ATi, I'd hope so, for the sake of suffering ATi users ....

---

