---
title: "Is My PNY Nvidia Geforce 4060 Ti 16Gb VRAM Video Card Compatible with Ubuntu 24.04???"
date: 2024-05-01
forum: Hardware
---

### Post by chaosjs0010 on 2024-05-01
Hello to all, I was just wondering if anyone can help me out with this problem on my Custom Built Computer here??  I have a PNY Nvidia Geforce 4060 Ti 16Gb of VRAM Video Card here and I am wondering if it was compatible first of all with Ubuntu 24.04 and if so How to install Ubuntu 24.04 successfully to a 4tb HDD without the thing going to a blank screen with nothing on it whatsoever and no cursor either?  I can get it to install to the hdd in question and then whenever I reboot and attempt to boot to the hdd in question it will boot straight to the login screen which displays a blank screen with nothing on it and no cursor either also!!  So, I would appreciate any help at all possible here very much..  Thanks for listening in advance and Have a great day ahead in the meantime and stay safe as well!!.. Also at startup I noticed that there is a nvidia DRM Failure error message although I am not exactly sure why or what the exact error message it is because it goes by so fast also!...

---

### Post by Yellow Pasque on 2024-05-01
It should work with the Nvidia 550.xx driver.
Shot in the dark - Try disabling SecureBoot in the BIOS/EFI. If that fixes the problem, either leave SecureBoot off (my personal preference), sign the nvidia modules yourself with mokutil or whatever, or make sure the linux-modules-nvidia-550-generic package is installed to use Ubuntu signed kernel modules

---

### Post by chaosjs0010 on 2024-05-01
Okay, Sounds like a good idea..  One question However,  How do I install the nvidia 550 driver?  I mean should I download it straight from Nvidia's website or How exactly would I go about it for now?  Thanks for the help anyhow though..  I most appreciate it right about now as well..  My secureboot is already disabled in the BIOS also btw.  I made sure of ti as well.

---

### Post by Autodave on 2024-05-01
Get the driver from Ubuntu....never straight from nVidia.  However, I would use the 535 driver.....it has been pretty reliable.  Going with the 550 could bring more problems than it is worth right now.  I am still using the 525 driver to be extra safe.

---

### Post by MAFoElffen on 2024-05-01
I have been supporting high end graphics on Unix and Linux since 2005...

Summarized: I would recommend installing it from the Ubuntu Repo's. If a little gutsy, install the graphics team PPA. That is still more dependable, ad less long time work than installing straight from NVidia.

I didn't always do that. I am advanced in skills, and just went ahead. It takes a lot of work to keep up on what will work, and to keep it maintained. Next, the Ubuntu Dev's do tweak the NVidia driver to work well with Ubuntu, and try to keep it working. 

There are still sometimes challenges, but that is just a part of life of owning an NVidia GPU and running Linux.

Remember a few things:

Modify your Grub2 Boot menu to "always show". Even if the show time is only 1-2 seconds. That will help you, if you have an update and it, all of a sudden, on the next boot, goes to a black-screen (graphics-wise).

Remember the boot-parameter "nomodeset". That will disable NVidia drivers from loading and letting the OpenSource Nouveau driver load, so that you can reinstall your NVidia drivers.

If you have to reinstall an NVidia driver (there are many ways to do that in Ubuntu), I always tell people that I (and NVidia) recommend that yoiu start by removing all traces of the old driver...
```

sudo apt remove --purge nvivia*

```
There are 3 ways to install an Nvidia driver from the repo's:
1) Use the Alternative Drivers tab of the Software & Updates Application.
2) Use ubuntu-drivers:
```

ubuntu-drivers list
sudo ubuntu-drivers install recommended

```
3) Install directly from commandline
```

sudo apt install nvidia-driver-550

```

---

### Post by Yellow Pasque on 2024-05-02
> **MAFoElffen said:**
> Remember the boot-parameter "nomodeset". That will disable NVidia drivers from loading and letting the OpenSource Nouveau driver load, so that you can reinstall your NVidia drivers.

Overly technical note: "nomodeset" or safe graphics mode probably doesn't let nouveau load (especially if it's blacklisted by nvidia driver). It forces generic vesa drivers.

> **Autodave said:**
> I would use the 535 driver.....it has been pretty reliable.  Going with the 550 could bring more problems than it is worth right now. 

I'd try 550 first on a card as new as the 4060Ti for best performance and most features. I'd only bother with older "long-lived" drivers if 550 caused issues.

---

