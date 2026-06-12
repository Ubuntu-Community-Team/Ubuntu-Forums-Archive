---
title: "nVidia driver installation problem"
date: 2008-12-31
forum: Installation &amp; Upgrades
---

### Post by dydo on 2008-12-31
I'm trying to install the nVidia drivers using the method 1 on [https://help.ubuntu.com/community/Latest_Nvidia_Dapper](https://help.ubuntu.com/community/Latest_Nvidia_Dapper)
When I try to execute ```
sudo apt-get install nvidia-glx
``` It tells me to pick a specific package. I decided to install nvidia-glx-177. During the installation, I get a error:
```
Errors were encountered while processing:
 /var/cache/apt/archives/nvidia-glx-177_177.80-0ubuntu2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
I tryed to install using Synaptic Package Manager but I still got the same error. How would I get this to work?
Thanks.

---

### Post by 2hot6ft2 on 2009-01-01
Are you running Dapper? If not what version of ubuntu are you running?

---

### Post by 2hot6ft2 on 2009-01-01
If you're running 8.04 Hardy or 8.10 Intrepid this is how you install the graphics driver.

To install the correct video driver you go to
System>Administration>Hardware Drivers
and select the one it recommends. It will download it and install it.

Then it will require a reboot. After rebooting go back to
System>Administration>Hardware Drivers
and make sure it is set as active.
All done.

Now go to
System>Preferences>Screen Resolution
and set your screen resolution and refresh rate
all done.

Enjoy

---

### Post by dydo on 2009-01-01
I fixed it, thanks for trying to help me. I used the 96 version instead and worked like a charm.

---

### Post by Coder543 on 2009-01-01
Please mark this thread as solved.

---

