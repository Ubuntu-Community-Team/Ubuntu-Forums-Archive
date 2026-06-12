---
title: "Brother Printer MFC-J5330DW not installing in 18.04 (64bit)"
date: 2018-10-22
forum: Hardware
---

### Post by Robbyx on 2018-10-22
I have run Brother's full install tool script and the scanner works (runs and scans from the computer), but the printer does not print from my computer. Lsusb shows an entry for Brother so it is connected.

I have tried a test page and the printer does not react. I have tried printing from libreoffice and it does not print.  The only error message in the installation of the cups wrapper deb was:

> Package ia32-libs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  lib32ncurses5 lib32z1

E: Package 'ia32-libs' has no installation candidate


I had previously installed both  lib32ncurses5 lib32z1 

Any ideas what more i should do to install the printer properly?

---

### Post by Robbyx on 2018-10-22
I have checked the cups access via  127.0.0.1:631 and the printer shows in there.

---

### Post by Robbyx on 2018-10-22
I have just run Gtkorphan and find that lib32ncurses5 and  lib32z1 are orphaned packages with an optional priority. Libusb-0.1-4 is also orphaned but with a priority of important. Note that the first two I installed because of the error message in the printer installation.

---

### Post by him610 on 2018-10-22
Surprised that your scanner works, but not your printer. Most of the time it's the other way around. My Brother MFC device connects through my local LAN. I have found the Brother *Driver Install Tool* works very well. From your earlier posts, it appears as if yours is connected by a USB cable. I have not used a USB connected printer in years - I always found they were too much trouble to maintain a viable connection after the computer was powered off. The logically connected USB port seemed to wander. With that said, I would think there is some mis-configuration involved with your issue.

I am not sure the packages you referenced in your earlier posts have any bearing on your inability to print.

Brother support website recommends firmware update for your particular MFC device. Have you accomplished the update yet?

---

### Post by Robbyx on 2018-10-22
I will speak to Customer services. It feels like a something obvious, but I do not know what is holding back the printer. Hopefully I will learn more tomorrow. 

Thanks

---

### Post by VMC on 2018-10-22
What's all the files inside "/opt"

---

### Post by him610 on 2018-10-22
Could you please show the results of...
```
dpkg -l | grep Brother
```

---

### Post by ubu69 on 2018-10-30
I have been having the same problem for several days (Brother MFC-J625DW). I found a solution in this thread: [https://ubuntuforums.org/showthread.php?t=2404947](https://ubuntuforums.org/showthread.php?t=2404947)
One of the suggestions by dino99 is to autoremove unused and possibly conflicting packages. I did the following:

```
sudo apt-get autoremove --purge
sudo apt-get update
sudo apt-get upgrade
sudo reboot
```

After the reboot, I logged back in and printed a test page with no problems.

---

