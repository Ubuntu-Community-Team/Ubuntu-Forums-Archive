---
title: "Need help to compile NIC driver"
date: 2007-05-05
forum: Hardware &amp; Laptops
---

### Post by jodoj80 on 2007-05-05
Hi. I'm a newbie in Linux and I need help how to compile the driver source files for the ethernet port of my motherboard PC Chips M851 V1.3A. I've allready download the driver's and untar it, but there is something in the installation that I don't understand. It said:              
```
    4) Compile the driver source files and it will generate rhinefet.o, and
       copy it to correct driver installation path (The installation directory
       is different in different kernel versions. In 2.4.x kernel, the path is 
       /lib/modules/KERNEL_VERSION/kernel/drivers/net/, and in 2.2.x kernel,
       the path is /lib/modules/KERNEL_VERSION/net/, the KERNEL_VERSION (see
       above) means the kernel version of your Linux distribution. If you don't
       know your kernel version , please run 'uname -r' command in command 
       line. The kernel version will look like '2.2.16', '2.4.2-2smp' etc.) :
        make install
```I decided to attach the installation file, so maybe you can understand thing that I don't. the first time that I try Ubuntu was with the same motherboard and I never have to install drivers for it. Now, after 3 month's without using my computer I decide to reinstall Ubuntu again and the NIC is not working.

---

### Post by chili555 on 2007-05-05
This driver is an oldie! Built in 2004 for a 2.2.x or 2.4.x kernel, which we haven't used since Chili had no grey hair! The module format .o is incorrect for modern 2.6.x kernels which use the module format .ko.

I believe the reason no newer driver can be downloaded and compiled is because it's built-in to your kernel. Please try:```
sudo modprobe via-rhine
ifconfig
```Did your ethernet interface appear? If so, please try:```
sudo dhclient eth0
```Are you connected?

Post back and let us know.

---

### Post by jodoj80 on 2007-05-05
@chili555. Thanks for the answer.

Sorry for the delay. But, I think a picture talk by itself.

I  appreciate your help on this.

---

### Post by chili555 on 2007-05-05
Hey, we're half-way there. We have eth0 working without compiling a questionable, moldie-oldie .tar.gz. Do you have this connected to a router or DSL modem or cable modem or what? Any PPPoE?

---

### Post by jodoj80 on 2007-05-05
@chili555. I've DSL without any kind of AAA configuration (*NO PPOoE or anything similar*)

I'm going to describe my WAN/LAN:
[LIST=1]
[*]The DLS is connected the switch
[*]I've an 8 Port Switch where all my computer and network equipment is connected. Including my old WRT54G v4 with DD-WRT Firmware, that I use just for wireless access. :guitar: 
[/LIST]chili555 the computer is connected to the switch. If you need more information to help me, I'll provide it to you. And thanks again for help in this.

---

### Post by jodoj80 on 2007-05-13
Thanks chili555,

But I've already resolve my problem.

Thanks,

---

