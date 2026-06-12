---
title: "Lost SMP support after installing nvidia-glx"
date: 2006-12-04
forum: Hardware &amp; Laptops
---

### Post by rubberchicken on 2006-12-04
Hi All,

I am pretty new to Ubuntu but have used Slackware for a number of years so find things a little strange to adapt to and hope to get some help with a small problem.

I bought a new laptop and decided to install Ubuntu for 'ease of use' and saw the whole compiz/beryl thing running on a machine and had to try it out.

The machine has a core 2 duo CPU (T7200) and a Nvidia Go 7200.

When I went to install the nvidia-glx package, it replaced the 2.6.17-10-generic kernel with the 2.6.17-i386 kernel and I lost the SMP support for the CPU. Since I was unable to find a 686+SMP kernel, I grabbed the .config file from the headers directory hoping it would contain the settings for the current kernel and then recompiled the source with SMP support turned on but it had lots of issues.

Long story short, what would be the best way to get SMP support back in the kernel again? Hopefully without needing to trawl through all the options.

Oh, and I did get Beryl running on the machine and I have to say it is a pretty sexy desktop to use :P

---

### Post by mathe on 2006-12-07
Had the same problem but using envy installed nvidia driver without messing up SMP:
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)
Very convenient!

Hope it helps,
Mats

---

