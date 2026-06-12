---
title: "Problems with Jaunty installing Nvidia driver"
date: 2009-08-20
forum: Installation &amp; Upgrades
---

### Post by Ubuntization on 2009-08-20
Hi all

I'm currently running Hardy. I can't install Jaunty cause after installing Jaunty, I have problems installing my video card driver. Somehow Hardy is easily able to download and install it automatically but not Jaunty. 

Jaunty usually downloads it but the installation process fails.My video card is a **nVidia GeForce 7350 LE**. That's why the 2 times I tried installing Jaunty, I had to go back and reinstall Hardy again. 

I had this same problem with Intrepid Ibex, and also with Hardy when they both first came out but later the problem was solved by itself. 


Help me Ubuntu lovers you are my only hope :)

---

### Post by running_rabbit07 on 2009-08-20
Try this [thread]("http://ubuntuforums.org/showthread.php?t=1243822"). It have have what you need for a happy Ubuntu.

---

### Post by Ubuntization on 2009-08-20
hi Ronnie

Thanks for your quick reply. Infact that is exactly the way i was trying to get the driver by going to System > Administration > Hardware Drivers
but unfortunately it didn't work

---

### Post by running_rabbit07 on 2009-08-20
> **Ubuntization said:**
> hi Ronnie

Thanks for your quick reply. Infact that is exactly the way i was trying to get the driver by going to System > Administration > Hardware Drivers
but unfortunately it didn't work

You tried installing the driver via Synaptic, too? Those are the only methods I know of.

---

### Post by nathanpc on 2009-08-20
In Synaptic you can find it, the only thing that you have to do is install all the things that you can found about Nvidia(For you kernel, obvious) and if this didn't work you can get the drivers from here: [http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)

Hope it helps,
 Nathan Paulino Campos

---

### Post by vikjon0 on 2009-08-20
Or use a driver from 3rd party PPA to get the latest version:

sudo nano /etc/apt/sources.list
add
deb [http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu](http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu) jaunty main
 
Add key
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com CEC06767

sudo apt-get update
sudo apt-get install linux-headers-generic nvidia-glx-185
*Version 180 is the version supplied by ubuntu(?) you can also try 190

sudo nvidia-xconfig -s --no-logo --force-generate

---

### Post by presence1960 on 2009-08-20
install envyng it will find your driver, download it and install it too. open a terminal and run ```
sudo apt-get install envyng-core
```and ```
sudo apt-get install envyng-qt
```.
After finished installing run from terminal ```
envng -t
```
Follow the prompts in terminal.
Or go Applications > System Tools > Envyng for a gui version.

---

### Post by running_rabbit07 on 2009-08-20
Hey precence1960, that "Lost Windows" thread disappeared fast didn't it?

I reported it, I can't stand piracy.

---

### Post by presence1960 on 2009-08-20
> **running_rabbit07 said:**
> Hey precence1960, that "Lost Windows" thread disappeared fast didn't it?

I reported it, I can't stand piracy.

I hate it also. That makes no sense to me, that guy has Ubuntu which is fast & free, and has the need to use pirated software. His best bet is to stay with windows and  keep quiet about it. But that doesn't absolve him of what he did. As much as I dislike Microsoft they have a right to charge for their product and have their patent & copyright honored. They are a corporate entity who is in business to make a profit.

I think I will stick with open source for my personal use. I have a windows 7 partition because I do repair work on the side and most of my clients use windows. So I need to stay up to date.

---

### Post by running_rabbit07 on 2009-08-20
> **presence1960 said:**
> I hate it also. That makes no sense to me, that guy has Ubuntu which is fast & free, and has the need to use pirated software. His best bet is to stay with windows and  keep quiet about it. But that doesn't absolve him of what he did. As much as I dislike Microsoft they have a right to charge for their product and have their patent & copyright honored. They are a corporate entity who is in business to make a profit.

I agree all the way. he won't be happy when a fed is knocking on his door.

> **presence1960 said:**
> I think I will stick with open source for my personal use. I have a windows 7 partition because I do repair work on the side and most of my clients use windows. So I need to stay up to date.

I hope to get a copy this semester from the college. Students usually get a good rate if signed up for IT classes.

I apologize for taking the thread off track.

---

### Post by Ubuntization on 2009-08-21
Hey guys 

Thanks a lot for you help, you guys a re awesome.I'll try all these suggestions and let you know the results :)

---

