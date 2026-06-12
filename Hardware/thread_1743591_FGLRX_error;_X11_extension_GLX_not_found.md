---
title: "FGLRX error; X11 extension GLX not found"
date: 2011-04-29
forum: Hardware
---

### Post by Xenland on 2011-04-29
Hello ubuntu users, First post so go easy on me.

This is the third time I've install ubuntu natty, and I've lost count how many tutorials I've took to resolve this issue. I've tried running the ATI drivers from the offical website for my Radeon 56xx(forgot the last 2 numbers). I've tried building packages from the file, the GUI, and installing it from console. I get the same error every time. I would try using the drivers from ubuntu packages but im trying to GPU mine and its required to have these packages for OpenCL to work correctly.

X11: extension not found GLX Dispaly:1
ERROR: couldn't get RBG visual

What do i need to do to solve this issue?


(NOTE: This is an issue with a Dell XPS desktop not a laptop please move this post if it is in the wrong section thanks mods!)

---

### Post by Xenland on 2011-04-29
The problem was I never installed 32-bit libraries which was stated in this tutorial i some how over looked: [http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide)

---

