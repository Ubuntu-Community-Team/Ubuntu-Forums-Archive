---
title: "Help troubleshooting a freeze"
date: 2009-06-03
forum: Hardware
---

### Post by mykrob on 2009-06-03
Got a new laptop today, I am experiencing the occasional lockup on it. When it happens, the cursor moves freely, but nothing responds. No, its not Intel graphics :)

Here is my hardware, I just wonder if there is a certain piece of hardware that may be a suspect here:

[http://pastebin.ca/1447033](http://pastebin.ca/1447033)

Thanks for any info you can provide.

-myk

---

### Post by mykrob on 2009-06-03
I just found this:

[http://ubuntuforums.org/archive/index.php/t-1137136.html](http://ubuntuforums.org/archive/index.php/t-1137136.html)

Gonna try a slightly older nVidia driver and see if it helps, i have the same chipset as the poster.

---

### Post by mykrob on 2009-06-03
Problem persists..

Performed a clean install due to other problems, possibly a bad burn, then installed the latest nVidia Beta 185 driver.

So far so good...

---

### Post by mykrob on 2009-06-04
over 12 hours later, everything is still good. With that said, anyone having issues with nVidia 8200M laptop graphics, try the nVidia 185 beta driver.

[http://www.nvidia.com/object/linux_display_ia32_185.18.04.html](http://www.nvidia.com/object/linux_display_ia32_185.18.04.html)

You will need to be sure to install kernel headers and the package "build-essential". Drop to a virtual terminal (Ctrl+Alt+F1) and turn off GDM with  sudo /etc/init.d/gdm stop

then install the package 

sudo sh NVIDIA-Linux-x86-185.18.04-pkg1.run

Follow the prompts, allow nVidia to configure the X-server, and you should be good..

hope this helps someone

---

