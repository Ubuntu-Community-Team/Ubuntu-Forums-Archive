---
title: "Problem with latest Nvidia Drivers"
date: 2017-02-26
forum: Hardware
---

### Post by georgesgiralt on 2017-02-26
Hello !
A fortnight ago  I bought an MSI GP62-7QF laptop.
To make it work I was forced to install 16.10 Ubuntu release instead of the desired 16.04 LTS version I wanted.
T+IT ran fine for some days, then I had to install some updates (including the latest Nvidia drivers) and since then, I experience the same graphic anomaly as this thread : [https://ubuntuforums.org/showthread.php?t=2353732](https://ubuntuforums.org/showthread.php?t=2353732) 
I have this behaviour every time I awake the laptop from sleep. 
Only solution, for now, is to shut the X server down and restart it. 
I would be delighted to have a proper solution for this very annoying problem (because in my case, the Unity menu disappears entirely into little coloured squares... )

thanks a lot in advance for your help.

---

### Post by Autodave on 2017-02-26
Did you install an Nvidia driver? If so, which one and where did you get it from?

---

### Post by georgesgiralt on 2017-02-26
Hello 
Thank you for your answer. 
I followed a French tutorial for a GP62-6QF (which is basically the same with one earlier revision of Intel processor).
It asked for this (pertaining to the NVidia drivers )
```

sudo add-apt-repository ppa:graphics-drivers/ppa
sudo add-apt-repository ppa:kranich/cubuntu
sudo apt-get update
sudo apt-get install nvidia-367 nvidia-libopencl1-367 nvidia-opencl-icd-367 nvidia-prime nvidia-settings mesa-utils prime-indicator

```
And about 3 days ago the NVidia drivers got updated. I cannot tell which version was installed because I can't find any logs containing the list of updated packages... Sorry.

---

### Post by Autodave on 2017-02-26
If you go into *Settings -> Nvidia, *it will tell you what version you are using. I currently am running 375.39. However, I install mine right from the repositories. If you want to try the one(s) in the repositories, you *must *uninstall the one you have running now before you get another one.

---

### Post by georgesgiralt on 2017-02-27
So I checked. The version is 375.39 ....

---

### Post by georgesgiralt on 2017-03-04
Any clues as to how to revert to the 367 version I had which was running fine ?

---

