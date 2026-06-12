---
title: "X Server dead after install, nvidia drivers"
date: 2005-12-18
forum: Installation &amp; Upgrades
---

### Post by astutzmann on 2005-12-18
Sorry if this is a dumb thread from this n00b.  I have read how to upgrade the nvidia drivers but without the graphical interface (X crashes at boot), how do I download the new drivers from Nvidia to my machine from the console?  I believe that my issue will be fixed my the new drivers but I can't figure out how to get the .run to my machine, dumb huh?  Looking for NVIDIA-Linux-x86_64-1.0-8174-pkg2.run

Ubuntu 5.10 (have it running fine on other machines (Dell 450 and Athalon 1000))

AMD - 64 - 3500
BioStar Motherboard, Tforce 6100 with onboard Nvidia Geforce 6100
512mg ram
80 gig IDE (for now), 200 gig Sata (for later data)

Thx in  advance,

Alf

---

### Post by MartinG on 2005-12-18
This is where to get the drivers:

[http://download.nvidia.com/XFree86/Linux-x86/1.0-8174/NVIDIA-Linux-x86-1.0-8174-pkg1.run](http://download.nvidia.com/XFree86/Linux-x86/1.0-8174/NVIDIA-Linux-x86-1.0-8174-pkg1.run)

Sorry, that's the 32-bit one. Try this:
[http://download.nvidia.com/XFree86/Linux-x86_64/1.0-8174/NVIDIA-Linux-x86_64-1.0-8174-pkg2.run](http://download.nvidia.com/XFree86/Linux-x86_64/1.0-8174/NVIDIA-Linux-x86_64-1.0-8174-pkg2.run)

---

### Post by astutzmann on 2005-12-18
Thanks for the quick response.  sorry, perhaps I didn't explain.  I understand how to download them and get them fro NVidia.  I have downloaded to my other machine fine.  Now, how do I get them to the machine that has only a console, no graphical interface at all?  I was thinking perhaps to burn to a cd and then get them off the cdrom dev??????  Other than that, I was looking for a command in console that could go get the file natively.

Alf

---

### Post by MartinG on 2005-12-18
Has the machine w/o X got web access? If so you can use wget, as in:```
wget http://download.nvidia.com/XFree86/Linux-x86_64/1.0-8174/NVIDIA-Linux-x86_64-1.0-8174-pkg2.run
```

This will download it to your home directory.  If no net access, how about a network link to your "working" machine?

---

### Post by astutzmann on 2005-12-18
thx so much, I'll try that

---

### Post by astutzmann on 2005-12-18
thx again, was able to download with wget, then with sudo chmod 777 was then able to run it, but by now I have borked too many things in my system so gonna try a fresh install and then the drivers.  Thanks alot for your help.

Alf

---

### Post by MartinG on 2005-12-18
Ok. Best of luck!

---

