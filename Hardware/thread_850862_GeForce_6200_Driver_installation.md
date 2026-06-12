---
title: "GeForce 6200 Driver installation"
date: 2008-07-06
forum: Hardware
---

### Post by Simscape on 2008-07-06
Alright, I have a EVGA GeForce 6200.
I downloaded the latest drivers from nVIDIA.
Pressed Ctr-Alt-F1.
Typed "sudo /etc/init.d/gdm stop"
Gave me a messaged saying the Gnome display stopped.
Typed "/home/cody/Desktop/NVIDIA-Linux-x86-173.14.09-pkg1.run"
Loaded the driver installation. I went throught tell it said it needed to compile the kernel, it said I did not have "libc" installed.
Whats up? I looked in the package manager, and searched "libc" everything that came up was installed.

---

### Post by overdrank on 2008-07-06
> **Simscape said:**
> Alright, I have a EVGA GeForce 6200.
I downloaded the latest drivers from nVIDIA.
Pressed Ctr-Alt-F1.
Typed "sudo /etc/init.d/gdm stop"
Gave me a messaged saying the Gnome display stopped.
Typed "/home/cody/Desktop/NVIDIA-Linux-x86-173.14.09-pkg1.run"
Loaded the driver installation. I went throught tell it said it needed to compile the kernel, it said I did not have "libc" installed.
Whats up? I looked in the package manager, and searched "libc" everything that came up was installed.

Hi and just a thought but it maybe referring to build-essential. You may need to install.

---

### Post by sdennie on 2008-07-06
As overdrank said, it sounds like you don't have the proper build utilities installed.  Before running the installer, try:

```

sudo apt-get install build-essential

```

Also, if you install the nvidia drivers from the website, just installing them probably won't be enough.  You may want to follow a guide like this: [http://ubuntuforums.org/showthread.php?t=797270](http://ubuntuforums.org/showthread.php?t=797270)

---

### Post by stewy79 on 2008-10-19
I wish people would write back to let us know how things worked out, I want to buy this card, but it would be nice to know if it works in ubuntu or not.

---

