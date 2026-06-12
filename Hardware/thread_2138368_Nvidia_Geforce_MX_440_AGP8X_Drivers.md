---
title: "Nvidia Geforce MX 440 AGP8X Drivers"
date: 2013-04-23
forum: Hardware
---

### Post by Nordico on 2013-04-23
I installed xubuntu (11.10) about a year or so ago, and I remember having troubles with my graph drivers. I don't recall exactly what I did, but it involved some manually typing info in the xorg.config file; eventually, I ended up with an acceptable and functional graphic interface so I kept that configuration (though I wasn't sure it was the optimal).

Recently, I needed to compile some CUDA codes, so I installed the cuda.toolkit and gave it a try. The last error I got was for the lack of a library called libcuda.so, which aparently didn't come in the toolkit but should come with the drivers instead. I guessed that I didn't have the lib because of my precarious graph configuration, so I went to the nvidia page, downloaded and installed the apropriate drivers (the installation changed the xorg.config). The lib was not there either, and moreover the graph quality of my image got worse. I opened synaptic and downloaded all 96-related packages and rebooted. After doing that, the screen hanged when loading the login menu. I used safe mode: the libcuda.so was still not there and the xorg.config had not changed. I had a backup from the one I originally had (previous to the driver installation) so I used those and could login again (but the graphs still look bad). I did this change once again and confirmed that with the new xorg.config the system always hanged. Another syntom of my problems: I seem to have the "Nvidia Xserver Settings" thrice in the application menu: twice under System and once under settings.

In conclussion: my graphic configurations is a total mess right now and I really need some help resetting all this (or at least cleaning it a bit) and finding the apropriate drivers and configuration.

---

### Post by mörgæs on 2013-04-24
This is an old card. First, if you have the option you should swap it for something better.

Second, it seems the poor system has been through so many modifications that there's not much left. I would do a fresh install of Xubuntu 12.04.2. Remember to take a back-up of all xorg.conf-files first and don't install closed-source drivers from the start.

---

### Post by Yellow Pasque on 2013-04-24
[http://en.wikipedia.org/wiki/CUDA#Supported_GPUs](http://en.wikipedia.org/wiki/CUDA#Supported_GPUs)

---

### Post by Nordico on 2013-04-25
Ok, today I will try to fresh install the system. After that I am going to need assistance, because I'm going to be in the same situation I was the first time I did this.

Thanks for the data on the graph card, I wasn't sure if it supported CUDA. The machine is also a bit old, so there is no point in changing the card. I usually have no problem with the machine being old because I only wanted it to code and try that code. Moreover, I've been told that I didn't even need a graph card at all in order to be able to compile the CUDA code (it would obviously crash if I try to send it to the card to compute, but supposedly this program can also be run interactively). Is this wrong?

---

### Post by Nordico on 2013-04-25
Fresh Install done. I updated all the software, and I haven't enabled third party drivers yet. How do I get my optimal graph configuration? Right now the screen display is acceptable, the only issue is that when starting up the screen suddenly turns to energy saving and then comes back almost immediately (this used to happen the first time I installed the system, before configuration of the graphs, and then it stopped).

Also, a comment: I have xubuntu 11.10, not 12.04. This all started with ubuntu 12.04, but the system was eating a lot of resources and I found on the internet it had to do with the graphcard (and I think that also had to do with the nvidia96 drivers or something like that) and a problem that aparently didn't appear in 11.10. When I changed to xubuntu for xfce, I assumed that it would be probably best to keep the 11.10 version. At this time, 12.04 was the latest version, and people used to say that there would probably be a fix in 12.10, but I lost track of this issue after that and I never heard if they did fix it or not, so I kept to the 11.10 version instead.

Also, if someone knows if my previous information is correct (I can compile cuda even if I don't have the hardware to run those parts of the code) and how to get the cudalib.so files, it would be of great help.

---

### Post by Nordico on 2013-04-27
Please; I can ask about the drivers needed to compile the cuda code in nvidia forums, but I really would like help with the appropriate way to set up my graphics configuration, because apparently the way I did it last time was not correct.

---

### Post by Nordico on 2013-04-29
Mmm, is the dynamic of these forums usually a little slow or does this mean I won't get any response?...

---

### Post by mörgæs on 2013-04-29
Most people here don't compile (I have used Buntu since 5.10 and have only done it once, for example).
Most people don't use such old graphics cards. 
Your card is not on the list in post #3.

Combined this gives a low probability that anybody can help you, but feel free to try the other forum.

---

### Post by Nordico on 2013-04-29
Yes, I said I could ask about the compiling part in another forum, but first I want to have the appropriate graph configuration; that is what I am asking about now.

---

