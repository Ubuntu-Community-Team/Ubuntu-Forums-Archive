---
title: "Drivers won't download"
date: 2008-12-12
forum: Installation &amp; Upgrades
---

### Post by Minuet on 2008-12-12
Sorry if this is the wrong section but it's still part of the "installation" process. I need to get the new drivers so I can have a higher resolution, as least that's how it worked with my other computer. Anyway, here's the error I get when it tries to download it.

```
W: Failed to fetch http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.24/nvidia-glx-new_169.12+2.6.24.13-18.41_i386.deb
  404 Not Found

```

I know what a 404 is but I don't know how to fix it. Any ideas? Thanks in advance.

---

### Post by 2hot6ft2 on 2008-12-12
Don't know why you're trying to install the drivers that way. I'm sure you have your reason but System>Administration>Hardware Drivers would be the best way.

---

### Post by Minuet on 2008-12-12
Yeah that's what I did. It showed the driver, so I clicked enable, then it started to "download" but I got that error. I already did this on another computer and it worked fine.

---

### Post by ianhaycox on 2008-12-12
Try either the 173 or 177 drivers

---

### Post by 2hot6ft2 on 2008-12-12
The repo may be offline you can chose another which is actually recommended System>Administration>Software Sources the first tab will be open select "Download from" then "Other" then click on "Select Best Server" it will do a short test of servers and find the best one for your location.

This may or may not solve the problem but you will then get your updates and software from the best server for you and your location.

---

### Post by 2hot6ft2 on 2008-12-12
You didn't mention what graphics card you have and Hardware Manager will display the best one for your hardware so I wouldn't recommend just picking one at random while I use the 177 it may not be the best for your card.

Short of getting it thru Hardware Manager my second choice would be using EnvyNG in Applications>System Tools>EnvyNG I think since I don't have it on mine.

---

### Post by Minuet on 2008-12-12
I have a GEFORCE 7600. I'll try that now.

---

### Post by 2hot6ft2 on 2008-12-12
Found this with a quick search [http://ubuntuforums.org/archive/index.php/t-891031.html](http://ubuntuforums.org/archive/index.php/t-891031.html) last post on the page says > It's sorted now.

All I needed to do was to run the updates from the synaptic package manager.

The proprietary driver then updated fine. I'm assuming after the updates, it looked for another file.

Seems there's a newer driver as shown here > If I navigate to [http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.24/](http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.24/) I find that indeed there is no "nvidia-glx-new_169.12+2.6.24.13-18.41_i386.deb" listed there. (Though there is a "nvidia-glx-new_169.12+2.6.24.12-16.34_i386.deb " and a "nvidia-glx-new_169.12+2.6.24.13-19.45_i386.deb"

---

