---
title: "Dual monitor support, Intel SandyBridge"
date: 2011-12-10
forum: Hardware
---

### Post by maxxjr on 2011-12-10
I have a laptop with Intel Sandybridge/HD3000 graphics.  

Under Windows, the hardware is capable of supporting two displays (laptop display plus external monitor).

Under XUbuntu/XFCE, I can choose laptop display or the external monitor, but cannot enable dual-displays.  There is no option for extended display.  I can get to a "clone desktop" option, but that does not seem to work either.

Is this a driver issue?  An XFCE issue?  Any suggestions on what I can try to get extended-desktop support?

My testing to this point has just been with the VGA output.  Haven't tried the displayport.  The VGA output did work for extended desktop under Windows.

Intel i5-2430M on a Lenovo T420, XUbuntu 11.10, FYI.


Thanks!

---

### Post by papibe on 2011-12-10
Using the following ppa has been suggested as a way to get the latest versions of Intel video drivers (specially those on sandy bridge processors).

If you don't find a solution soon enough, you may want to try them:
```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get upgrade
```
Then restart your machine.

Hope it helps.
Regards.

---

