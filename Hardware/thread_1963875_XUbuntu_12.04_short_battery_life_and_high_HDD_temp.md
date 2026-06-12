---
title: "X/Ubuntu 12.04 short battery life and high HDD temperature"
date: 2012-04-23
forum: Hardware
---

### Post by Zingam on 2012-04-23
When I am running Xubuntu 12.04 the battery gets emptied much faster than on Windows. Also another and bigger problem for me is that the HDD get much hotter than under Windows -  about 15% hotter (if normally the HDD under Windows is 35C under Linux gets at least 40C while idling).

Well, maybe its because I am using a Wubi installation. Anywhen when I use Ubuntu on a virtual machine under Windows - the disk does not get that hot or at least I haven't noticed such a problem.

On Windows even when I am watching movies or using something similar (like streaming data from the disk), disk never get as hot as on Linux when idling. That's not very pleasant on a small notebook.

---

### Post by qorrow on 2012-04-28
I confirm this problem. My Laptop HP gets very hot while using Ubuntu 12.04. I don't have this problem with other Linux distributions. I don't  know if this is related to the new kernel or to compiz or it is a problem with ATI graphics cards?

I hope there is a solution because Ubuntu 12.04 is a good release and I wish to use it. Thanks

---

### Post by Lamukra on 2012-04-28
I confirm the problem with heat levels and fan speed... These became better when I installed Proprietary driver for my ATI Radeon HD 5650 card. Heat levels went to much better state. Hope it helps!!!

---

### Post by Rapture1781 on 2012-04-30
I confirm the same problem with Dell Studio 1557 (italian) and ATI 4570... 75°. :(

I'm very disappointed...

---

### Post by forreststevens on 2012-05-01
Shame, same here, Dell XPS1340, Intel P9500, nVidia proprietary drivers.  Any help would be appreciated...

---

### Post by narya on 2012-05-04
Same problem running ubuntu 12.04 on a hp dv7  laptop :( ati proprietary drivers in use.

---

### Post by scalvo on 2012-05-04
Same problem with fans. I have an Asus I7 N61jq and Ati Mobility Radeon 5730...

The fan speed issue is really anoying. Using opensource drivers is always at maximum and really noisy.
Using propietary drivers once in a while it gets better, but still not working properly.

It works perfectly in Ubuntu 10.10. Could this have something to do with kernel>3???

---

### Post by 23senick on 2012-05-12
My experience similar, and others too...

[http://ubuntuforums.org/showthread.php?p=11929007#post11929007](http://ubuntuforums.org/showthread.php?p=11929007#post11929007) 

I started on 11.10 with sensors showing average temperature for CPU etc of 67 degrees if not doing too much.  After many tweaks, Jupiter, power saving, upgrade to 12.04 this was down to around 61 degrees.  I then gave in and reverted to proprietary drivers which gave me another 3 degrees improvement or so, idling at 57-58 degrees.  But HDD still seems about 40 degrees

---

### Post by lancecherry on 2012-05-15
I confirm this problem by x220i. So i stay in 10.04 because of kernel 2.6.*

---

### Post by lilmagnus on 2012-05-15
Apparently this is a kernel problem as many have indicated. Should be fixed in 3.3 kernel and higher levels. Laptop-mode-tools seems to have helped [here]("http://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=2&ved=0CG8QFjAB&url=http%3A%2F%2Funix.stackexchange.com%2Fquestions%2F30582%2Fwhy-does-linux-heat-up&ei=yRyzT8uAG7KM6QGCyuHLCQ&usg=AFQjCNFVkmTRwCCBccstwIZEfNQZY5iqjw&sig2=1vK9lP9jNg5BrVmsufHKJQ") and a compile of kernel 3.3 helped [here]("http://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=1&ved=0CGoQFjAA&url=http%3A%2F%2Fforums.linuxmint.com%2Fviewtopic.php%3Ff%3D49%26t%3D90671%26p%3D575198&ei=yRyzT8uAG7KM6QGCyuHLCQ&usg=AFQjCNFf0eUUNXRVLNkyCZnQZGFe0L4lNg&sig2=hSNYakiRWGVTiTeSoV49fA"). Many ways to a solution or workaround I suppose.

---

### Post by Ms. Daisy on 2012-05-24
Here's a workaround:

[http://www.dedoimedo.com/computers/ubuntu-pangolin-nvidia.html](http://www.dedoimedo.com/computers/ubuntu-pangolin-nvidia.html)

---

### Post by aquiles87 on 2012-05-30
I have the same problem. My laptop is HP Pavilion  with NVIDIA Geforce 8400 and I use dual boot system(Windows Vista and Ubuntu 12.04 ls). My video card heating up to 60C on Ubuntu - when I use windows that happens only when I'm playing games.What bothers me more is the HDD which heating up over 50C - when I'm on Windows max temperature is 40-45C.
Does anyone found solution?
I like Ubuntu a lot but this overheating problem is serious because I can't afford to change HDD and video card every month. If there is no solution I'll have to use only Windows.

---

