---
title: "Nvidia gforce 8700 and native resolution problem"
date: 2009-04-27
forum: Installation &amp; Upgrades
---

### Post by lbravo on 2009-04-27
Hello,

I'm trying to get native resolution of 1900x1200 on my dell xps 1730.  I've tried a lot of suggestions, and I can never get 1900x1200 on the drop down for the Nvidia X Server Display Configuration.

I'm now using the proprietary drivers, but have tried other things, such as editing my xorg.config.

Oh, and I've upgraded to jaunty jackalope.

Any ideas?

L.

---

### Post by TheLions on 2009-04-27
did you try using modeline?
[http://en.wikipedia.org/wiki/XFree86_Modeline#External_links](http://en.wikipedia.org/wiki/XFree86_Modeline#External_links)

and did you try change resolution using 'NVIDIA X Server settings'? (System-Administration->)

---

### Post by lbravo on 2009-04-27
modeline?  That looks like I'd just be getting into MORE trouble :)

There is no NVIDIA X server settings choice from my System -> Admin Menu.

Other ideas?  I'm starting to think that it's just not meant to work.

---

### Post by TheLions on 2009-04-27
ok try installing the newest drivers, go here [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates) and add thous to your 'Software repository' or just download this:

64 bit:
[https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates/+files/nvidia-180-modaliases_180.53-0ubuntu2_amd64.deb](https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates/+files/nvidia-180-modaliases_180.53-0ubuntu2_amd64.deb)
[https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates/+files/nvidia-180-kernel-source_180.53-0ubuntu2_amd64.deb](https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates/+files/nvidia-180-kernel-source_180.53-0ubuntu2_amd64.deb)
[https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates/+files/nvidia-180-libvdpau_180.53-0ubuntu2_amd64.deb](https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates/+files/nvidia-180-libvdpau_180.53-0ubuntu2_amd64.deb)
[https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates/+files/nvidia-glx-180_180.53-0ubuntu2_amd64.deb](https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates/+files/nvidia-glx-180_180.53-0ubuntu2_amd64.deb)

32 bit:
[https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates/+files/nvidia-180-modaliases_180.53-0ubuntu2_i386.deb](https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates/+files/nvidia-180-modaliases_180.53-0ubuntu2_i386.deb)
[https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates/+files/nvidia-180-kernel-source_180.53-0ubuntu2_i386.deb](https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates/+files/nvidia-180-kernel-source_180.53-0ubuntu2_i386.deb)
[https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates/+files/nvidia-180-libvdpau_180.53-0ubuntu2_i386.deb](https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates/+files/nvidia-180-libvdpau_180.53-0ubuntu2_i386.deb)
[https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates/+files/nvidia-glx-180_180.53-0ubuntu2_i386.deb](https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates/+files/nvidia-glx-180_180.53-0ubuntu2_i386.deb)

restart and then you should have 'NVIDIA X Server settings'. It can automaticly detect your resolution or you can type in your own.

---

### Post by lbravo on 2009-04-27
I downloaded and installed the above. Now from System -> Preferences I get the NVIDIA X Server Settings.  I had this before, there was just no menu choice for it - it came up when I chose Display.  Anyway, there is no choice for 1900x1200 on the list (still).  The max resolution is 1400x1050.

---

### Post by TheLions on 2009-04-27
press detect displays and if it isn't on the list press advanced

maybe the next step to go:[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

since I m out of ideas... :(

---

### Post by lbravo on 2009-04-27
Nothing happens when I detect displays... and hitting advanced only lets me change panning, which would be annoying.  Starting to think that I should be happy with 1400x1050....

---

