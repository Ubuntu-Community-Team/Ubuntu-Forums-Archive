---
title: "Help installing Nvidia drivers"
date: 2008-02-03
forum: Hardware &amp; Laptops
---

### Post by ondo311 on 2008-02-03
When I try to apply the advanced appearce theme stuff it tells me

> The software source for the package

nvidia-glx-new

is not enabled

Then it says

> Please run "Apperance/Desktop Effects" again after restarting the computer, when the new graphics driver is active.

sooo wen i go into the downloader thingy i cant find that..... i'm just confused

---

### Post by linuxwizard on 2008-02-04
Go to > System > Administration > Restricted Drivers Manager > click on Enable on the line that shows Nvidia accelerated graphics driver > the driver will be installed for you > than you will have to restart computer > After restart go to > System > Preferences > Appearance > click on Visual Effect tab choose which one you want to use.

System > Preferences > Advanced Desktop Effects Settings >you can setup plugins, enable or disable, change settings

Hope this helps and what you were looking for to do.

---

### Post by rphil2008 on 2008-02-04
Hello, newbie here. Apologies to the original poster. I thought I'd just ask the question here since the titile of the thread is a help request for Nvidia driver update. 

I have downloaded updated NVidia Drivers from nvidia for linux pc. I want to use this to update my Ubuntu Linux 7.1 at my home pc having no internet connection. I have no command line experience at Linux and I am concerned I will be typing the wrong commands without assistance and mess up my system. The files are called:

NVIDIA-Linux-x86-96.43.05-pkg1.run
nvidia-xconfig-1.0.tar

Do I need both? How do I update my video card driver? Thanks.

---

### Post by erginemr on 2008-02-04
> **rphil2008 said:**
> Hello, newbie here. Apologies to the original poster. I thought I'd just ask the question here since the titile of the thread is a help request for Nvidia driver update. 

I have downloaded updated NVidia Drivers from nvidia for linux pc. I want to use this to update my Ubuntu Linux 7.1 at my home pc having no internet connection. I have no command line experience at Linux and I am concerned I will be typing the wrong commands without assistance and mess up my system. The files are called:

NVIDIA-Linux-x86-96.43.05-pkg1.run
nvidia-xconfig-1.0.tar

Do I need both? How do I update my video card driver? Thanks.

Depending on the model of your NVidia card, the package in the repositories is "nvidia-glx" and its version is ver.96.39. You can either run your restricted-drivers-manager or find and install it from synaptic. On the other hand, the package you have downloaded is ver.96.43, so the one in the repositories is pretty new IMHO. Although you can still install the downloaded binary packages, I strongly suggest you to stick to the NVidia drivers in the repositories.

The installer also needs numerous X11 development packages to be able to compile the new NVidia driver into the kernel, which means you will need to download many more packages. As an added bonus, you will need to do the same with each major kernel upgrade, done by the update manager. Even if you do so, there is always a chance that you will run into compatibility problems later on and will not be able to boot into the desktop no matter what you do. I know it, because I have messed up my system twice and could not recover from it after a kernel update to a system with the NVidia-site installed drivers. 

To avoid this problem, you will need to take some extra precautions such as disabling the detection of "nvidia" module from some config files. Believe me; it is not worth the effort. If installing "nvidia-glx" works for you, you can avoid all this fuss. Plain and simple!

---

### Post by oldsoundguy on 2008-02-04
I personally used ENVY to install the nVidia drivers on three desktop machines and had NO problems .. but it requires an internet connection to work.

---

### Post by psycho5 on 2008-02-04
So many people have told me to stay CLEAR of ENVY auto installer, they say it messes up your system. Why's that? I haven't used it anyway to install my driver, I just followed the manual way.

---

### Post by obeztg on 2008-02-04
I have a newer system that I'm trying to intall Ubuntu to, but it hangs during the boot sequence. I believe it is due to my video card which is the nVidia GeForce 880 GT. I get a message that the card isn't recognized and that Ubuntu is going to boot into Safe graphics mode. It then get's "stuck" at the "running boot scripts" screen (where the screen flickers a number of times and then eventually just stops and sits there). I want to install this to my HDD but I need to know how to get into the interface in such a way that I can install it and get my video card running. Any suggestions?

Thank you

---

### Post by oldsoundguy on 2008-02-04
from what I have read, ENVY is only a problem if you are attempting to install drivers for ATI .. since the SOURCE drivers are really messed up. 
BUT, if you are doing a new install, just what do you have to lose other than some time?  If it works, fine, if it does NOT work .. REINSTALL Ubuntu and try the manual way with the restricted drivers.
The stuff is NOT going to re-write your BIOS or permanently burn itself into your hard drive!

---

### Post by rphil2008 on 2008-02-04
> **erginemr said:**
> Depending on the model of your NVidia card, the package in the repositories is "nvidia-glx" and its version is ver.96.39. You can either run your restricted-drivers-manager or find and install it from synaptic. On the other hand, the package you have downloaded is ver.96.43, so the one in the repositories is pretty new IMHO. Although you can still install the downloaded binary packages, I strongly suggest you to stick to the NVidia drivers in the repositories.

The installer also needs numerous X11 development packages to be able to compile the new NVidia driver into the kernel, which means you will need to download many more packages. As an added bonus, you will need to do the same with each major kernel upgrade, done by the update manager. Even if you do so, there is always a chance that you will run into compatibility problems later on and will not be able to boot into the desktop no matter what you do. I know it, because I have messed up my system twice and could not recover from it after a kernel update to a system with the NVidia-site installed drivers. 

To avoid this problem, you will need to take some extra precautions such as disabling the detection of "nvidia" module from some config files. Believe me; it is not worth the effort. If installing "nvidia-glx" works for you, you can avoid all this fuss. Plain and simple!

Thanks for all who replied. The above post directly relate to my problem. I never thought 7.1 had a new driver already in its repositories. I wil stick to it. Now can anyone please tell me "cook-book" steps on how to install the nvidia-glx? Thanks again. My card is NVidia GEForce 4 MX.

---

### Post by r4ik on 2008-02-04
Perhaps this helps,

[http://ubuntuguide.org/wiki/Ubuntu:Gutsy#NVidia_Driver](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#NVidia_Driver)

Good luck !

---

### Post by sputnik13 on 2008-02-04
> **erginemr said:**
> ...the package you have downloaded is ver.96.43, so the one in the repositories is pretty new IMHO....

Actually, looking at [NVIDIA's display driver archive]("http://www.nvidia.com/object/linux_amd64_display_archive.html") and the corresponding release dates, it would appear 96.43.05 is the latest version.  It baffles me what the rationale behind the version numbering is.

---

