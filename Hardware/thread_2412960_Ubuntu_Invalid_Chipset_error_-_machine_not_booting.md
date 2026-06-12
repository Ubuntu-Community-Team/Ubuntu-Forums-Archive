---
title: "Ubuntu Invalid Chipset error - machine not booting"
date: 2019-02-19
forum: Hardware
---

### Post by chiefsanders on 2019-02-19
Hi guys, hoping someone can point me in the direction of what's wrong here. 

I've got a client with a Linux machine running Ubuntu 18.04.2. I never set the machine up, but agreed to take a look at it despite not being a Linux expert. I'm not sure if its graphics card related or CPU related. The machine is a custom build which the client built themselves

AMD Threadripper 1900x 8 core CPU
32GB RAM
NVIDIA GeForce RTX 2080ti

To my knowledge, the client didn't do any homework beforehand in terms of checking what is compatible and such. He's reported that he has had to re-install the graphics drivers every 3 weeks or so because they keep "breaking" and disappearing then needing to be re-installed. He swears he has done nothing other than "shutting it down one evening, and the next day it started doing this." 

I finally managed to get the machine booting......but it only boots with an intervention, pressing shift to get the GRUB menu and then selecting the OS......it appears to boot fine. The graphics drivers near as I can see are not installed, and the machine is constantly refusing to install them saying it can't find the package for the drivers......despite me downloading them directly onto the machine! I tried rolling back the kernel to a previous version, but nada the machine still won't boot on its own as normal. 

I have attached  a screenshot to show some of the error messages being received. 

Can anyone offer any pointers? I'm on the verge of sadly handing it back to him and saying "You're on your own!" 

Thanks guys, 
Donald

---

### Post by chiefsanders on 2019-02-19
Note: I got the drivers installed, I think, using the following: 
sudo apt-get update
sudo apt-get upgrade
sudo ubuntu-drivers devices

Then I used sudo apt-get install nvidia-xxx to install the drivers. 

It has stopped throwing up the chipset error now......but its still refusing to boot in to Ubuntu. I don't know what else I can do to be frank.

---

### Post by deadflowr on 2019-02-19
*Thread moved to **Hardware***

Hopefully someone can give you a better understanding of what you need to get it to work.

To start what was the nvidia driver version it installed?
You might need the updated/experimental/testing gpu-driver ppa version:
[https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa]("https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa")

Ubuntu's default driver selection can lag for some new hardware...

---

### Post by Autodave on 2019-02-19
That should be using at least the 410.93 driver.

---

### Post by CatKiller on 2019-02-19
> **Autodave said:**
> That should be using at least the 410.93 driver.

Specifically, 410 is the series that first included Turing support. Nothing earlier than that will work. Which means that the OP **must** use the PPA.

The "just breaking" suggests that the OP's client didn't have DKMS configured properly, perhaps because they'd used the .run file initially. Don't use the .run file.

---

