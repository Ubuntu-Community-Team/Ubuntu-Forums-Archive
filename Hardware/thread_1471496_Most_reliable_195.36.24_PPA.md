---
title: "Most reliable 195.36.24 PPA"
date: 2010-05-03
forum: Hardware
---

### Post by wolfe on 2010-05-03
Hey guys, just curious what the most reliable 195.36.24 ppa might be.  I'm looking for full support of my new 470's and need to know where I can pull these drivers from.  I tried the x-swat ppa, but was unable to boot after the upgrade.

My system config if that would help is:

10.04 x64 release
2 gtx 470s in SLI (though I have not configured SLI just yet.)

---

### Post by wojox on 2010-05-03
Why don't you download it from the site?

[http://www.nvidia.com/object/linux-display-amd64-195.36.24.html](http://www.nvidia.com/object/linux-display-amd64-195.36.24.html)

---

### Post by wojox on 2010-05-03
Follow this guide to install it [[HOWTO] Install NVIDIA drivers manually on Lynx]("http://ubuntuforums.org/showthread.php?t=1467074")

---

### Post by wolfe on 2010-05-03
I have tried that, but I think there is a bug with x.32-x series kernels and multi nvidia gpu set ups.

---

### Post by wolfe on 2010-05-03
This bug:


[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/548362](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/548362)

---

### Post by wojox on 2010-05-03
You could try this ppa [https://launchpad.net/~nvidia-vdpau/+archive/ppa?field.series_filter=](https://launchpad.net/~nvidia-vdpau/+archive/ppa?field.series_filter=)

---

### Post by wolfe on 2010-05-03
yeah thats the ppa I have always used in the past.  guess I'll be better served by just waiting until I see 195.36.24 hit the vdpau ppa.

---

### Post by wolfe on 2010-05-04
the vdpau maintainer claims this will not hit his ppa as official support will come from the ubuntu team.  But I thought due to its LTS status drivers don't typically see updated versions on this cycle.  Is that wrong?

---

### Post by Linuxforall on 2010-05-04
Official Ubuntu dev ppa as the latest [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

---

### Post by wolfe on 2010-05-04
many thanks!  this is what I needed, I'll test it on my lunchbreak and report back since there arent any other 195.36.24 threads that I can see.

Just checked the ppa.  I'm really hesitant to use this ppa, I already tried it once and it hosed my system making it non-bootable, even in recovery mode.

---

### Post by wolfe on 2010-05-05
upgraded using the x-swat ppa without issue.  Just thought I'd follow up.  Appears my cards are fully functioning now!

---

