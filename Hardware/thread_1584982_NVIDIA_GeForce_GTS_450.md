---
title: "NVIDIA GeForce GTS 450"
date: 2010-09-29
forum: Hardware
---

### Post by Flatline-kun on 2010-09-29
I was wondering if anyone has tried installing an NVIDIA GeForce GTS 450 video card yet...I don't see anything in the drivers or compatibility lists. I was looking to get one...nice dual DVI...but don't want to spend the cash unless there are drivers for it.

---

### Post by cascade9 on 2010-09-29
Not quite yet there arent. Well, its possible that the GTS450 will work with the newest beta drivers (260.19.04) but the GTS450 isnt listed in the 'supported products' page for the 260.19.04 drivers, so that isnt likely. 

If you just after dual DVI, a GT220/240 would be a better choice. No need for a gamers card unless you are actually a gamer. ;)

---

### Post by PresenceofMind on 2010-09-30
GTS 450 is not 100% supported......

---

### Post by garfonkee on 2010-10-01
I bought the GTS 450 just today (because my 8800 broke), and installed it in my ubuntu. Ran glxgears and it ran at 50k frames per second, faster than the 23k frames per second that my 8800 was running.

edit: would love to know what part of the 450 isn't supported, just in case

---

### Post by j0nny on 2010-10-12
I installed a Nvidia Geforce GTS 450 last night - ran > sudo apt-get install nvidia-current and then enabled the drivers through System->Administration->Hardware Drivers

Civ5 ran a charm!

---

### Post by peterdc on 2011-08-05
> **j0nny said:**
> I installed a Nvidia Geforce GTS 450 last night - ran  and then enabled the drivers through System->Administration->Hardware Drivers

Civ5 ran a charm!
I followed these instructions and it worked fine with one monitor but when I tried to enable a second the PC would just freeze and require a manual reboot.

What I did to get the correct drivers installed and both monitors enabled was this:

Download driver from: [nVIDIA Driver Downloads]("http://www.nvidia.com/Download/index.aspx?lang=en-us") (for me [280.13 for 64 Bit]("http://www.nvidia.co.uk/object/linux-display-amd64-280.13-driver-uk.html") but there's also [280.13 for 32 Bit]("http://www.nvidia.co.uk/object/linux-display-ia32-280.13-driver-uk.html")).

Reboot the PC and at the logon prompt screen, press CTRL+ALT+F1 to get to a terminal screen & login.

Stop Gmome from running
```
sudo /etc/init.d/gdm stop
```Navigate to the directory where the driver was downloaded
```
cd /path/to/driver/download
```Run the driver installation
```
sudo sh ./NVIDIA-Linux-x86_64-280.13.run
```Then, follow all on-screen instructions and allow the installer to edit the X config file at the end of the installation.

Reboot and driver is working and monitors are running at their native resolution.

---

