---
title: "How Do I Use Open Source ATI?"
date: 2008-05-30
forum: Hardware
---

### Post by Dr Zolygon on 2008-05-30
I'm running Ubuntu 8.04 and have a laptop with a Radeon 9000/9100 gpu(RS300M). I want to know how to use the open source ATI driver.

Thanks in advance.

---

### Post by oVIXx on 2008-05-30
Well theres a few ways. 

The Hardware Drivers software, System-->Administration-->Hardware Drivers, and tick the "Enable" box.

Use the Synaptic Package Manager, System-->Administration-->Synaptic Package Manager, and do a search for "fglrx".

Or you can use the terminal and apt, *sudo apt-get install xorg-driver-fglrx*

---

### Post by Dr Zolygon on 2008-05-30
> **oVIXx said:**
> Well theres a few ways. 

The Hardware Drivers software, System-->Administration-->Hardware Drivers, and tick the "Enable" box.

Use the Synaptic Package Manager, System-->Administration-->Synaptic Package Manager, and do a search for "fglrx".

Or you can use the terminal and apt, *sudo apt-get install xorg-driver-fglrx*

Thanks for the response.

No video drivers show up under Hardware Drivers and fglrx does not support my graphics card(too old).

---

### Post by Dr Zolygon on 2008-05-31
bump

---

### Post by beanhead on 2008-06-05
Hi, i have the exact same card. It used the openGL driver as a default.
You maybe using it now.

---

### Post by thorombolo1 on 2008-06-05
I have an Radeon 8500 and the default drivers work fine for me the only problem I have is the gamma setting but if you go to:
sudo gedit /etc/X11/xorg.con under monitor setting include the line gamma x.x and you are set you can also change the resolution using the system -> preferences -> screen resolution option for this it will choose the correct refresh rate for your system. Hope this helps.

---

