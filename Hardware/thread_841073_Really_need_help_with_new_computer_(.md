---
title: "Really need help with new computer :("
date: 2008-06-26
forum: Hardware
---

### Post by kripkenstein on 2008-06-26
I am at the end of my rope here...

I bought a new computer (specs at the bottom). From what I read online it should work fine with Ubuntu. And when I do a fresh install, it works great, then a few hours later I start to get strange errors: downloaded files and packages are corrupt, compilation of large projects gives varying output files.

But when I run hardware diagnostic checks everything is fine! I tried memtest, cpuburn, I scanned for bad sectors (read-write test), and after a week of this frustration I installed Windows on a partition... and it seems to work fine :( Also I checked temperatures, they are ok, and I even tried to run the CPU cores on 'powersave' which keeps them even cooler, but no change.

I tried installing Fedora 9 (which has a later kernel), but the same problems occur.

Is it possible that there is some subtle bug in Linux with my hardware? It's been a week and I'm starting to worry I won't be able to run Ubuntu any more.

Problem is, I can't tell the store my hardware is faulty since Windows runs ok... so I'm stuck with this, unless I find an actual hardware problem.

Any ideas?


Specs:
```

Core 2 Duo E8400
Gigabyte EP35-DS3L motherboard
Gigabyte 9600 GT NVidia video card

```

---

### Post by cdtech on 2008-06-26
Did you try running:
sudo dpkg –configure -a

Then do:
sudo apt-get autoclean && sudo apt-get autoremove
sudo apt-get update && sudo apt-get upgrade

---

### Post by kripkenstein on 2008-06-26
> **cdtech said:**
> Did you try running:
sudo dpkg –configure -a

Then do:
sudo apt-get autoclean && sudo apt-get autoremove
sudo apt-get update && sudo apt-get upgrade
Thanks, but no, that doesn't help. My system is up to date.

But every now and then, on even a fresh installation, I get corrupted downloads, both files and packages. It makes it impossible to work in Ubuntu.

---

### Post by Thanoulis on 2008-06-26
Did you try to change your download server? System->Administrator->Software Sources. That's all i can tell...:(
Sometimes a Linux kernel recognizes a faulty hardware while win32 still run ok...i had kind of a same problem some year ago with a second hand P3 600MHz.(While win32 booted and run ok, my GNU/Linux distros hang all the time...after 6 months the CPU died...while in win32...:))

---

### Post by kripkenstein on 2008-06-26
> **Thanoulis said:**
> Did you try to change your download server? System->Administrator->Software Sources. That's all i can tell...:(
Sometimes a Linux kernel recognizes a faulty hardware while win32 still run ok...i had kind of a same problem some year ago with a second hand P3 600MHz.(While win32 booted and run ok, my GNU/Linux distros hang all the time...after 6 months the CPU died...while in win32...:))

Yeah, I tried different servers, and also I get corrupted downloads from websites (I've been downloading large files and md5sum-ing them... this leads to good results in Windows but sometimes corrupt files in Linux).

---

### Post by kripkenstein on 2008-06-30
I'd really appreciate any ideas as to what to do next, I'm almost at the end of my rope here...

The current situation is that fresh installs of Ubuntu on this computer eventually get messed up, because downloads are corrupted. Typically I download updates and a few of those packages are invalid, which leads to a broken system (even after fixing the broken packages).

Also, if the install is lucky enough to work until I can compile stuff, then compiling leads to unpredictable results: compile the exact same project, sometimes the result is ok, sometimes the resulting executable crashes on startup.

However, Windows runs fine on this machine.

I tried to scan for bad sectors, I ran memtest, cpuburn, everything seems fine... but nothing is fine :(

---

### Post by stchman on 2008-06-30
> **kripkenstein said:**
> I am at the end of my rope here...

I bought a new computer (specs at the bottom). From what I read online it should work fine with Ubuntu. And when I do a fresh install, it works great, then a few hours later I start to get strange errors: downloaded files and packages are corrupt, compilation of large projects gives varying output files.

But when I run hardware diagnostic checks everything is fine! I tried memtest, cpuburn, I scanned for bad sectors (read-write test), and after a week of this frustration I installed Windows on a partition... and it seems to work fine :( Also I checked temperatures, they are ok, and I even tried to run the CPU cores on 'powersave' which keeps them even cooler, but no change.

I tried installing Fedora 9 (which has a later kernel), but the same problems occur.

Is it possible that there is some subtle bug in Linux with my hardware? It's been a week and I'm starting to worry I won't be able to run Ubuntu any more.

Problem is, I can't tell the store my hardware is faulty since Windows runs ok... so I'm stuck with this, unless I find an actual hardware problem.

Any ideas?


Specs:
```

Core 2 Duo E8400
Gigabyte EP35-DS3L motherboard
Gigabyte 9600 GT NVidia video card

```

Are you running Hardy?

That 9600GT video card will take some tinkering to get it working.  I have a P35 mobo and a Core 2 Quad that run very well.

---

### Post by kripkenstein on 2008-06-30
> **stchman said:**
> Are you running Hardy?

That 9600GT video card will take some tinkering to get it working.  I have a P35 mobo and a Core 2 Quad that run very well.

I followed one of the howtos for the card (on these forums), and it worked great almost immediately, actually. No problems there.

It's everything else that doesn't work right, it seems...

Edit: Yeah, running Hardy.

---

