---
title: "[SOLVED] NVidia restricted drivers or official drivers?"
date: 2008-07-22
forum: General Help
---

### Post by Darkade on 2008-07-22
Hello I'm planning in buying an NVidia 9600 GT graphics card but due to all the problems about NVidia cards and it's drivers I must ask: Are this problems caused by the restricted drivers that you can install via synaptic? Will they be solved if I would install NVidia official drivers for linux? Do you know if NVidia 9600 GT is supported by the ubuntu provided drivers?

Of course I would love to use free/Open Source Drivers but if they won't make the most out of my graphics card should I install the official drivers? I'm really lost here, and I don't want to invest in something I will not be able to use in Ubuntu

Thanks :D

---

### Post by YaroMan86 on 2008-07-22
The proprietary drivers are actually pretty good. Its the open source nvidia driver you want to avoid.

---

### Post by jombeewoof on 2008-07-22
> **YaroMan86 said:**
> The proprietary drivers are actually pretty good. Its the open source nvidia driver you want to avoid.

I have the exact opposite suggestion. 
drivers straight from Nvidia don't work for me. 
The "new" driver from synaptic works like a champ though.

Nvidia GeForce 6800 GT

---

### Post by Darkade on 2008-07-22
So if I install the proprietary drivers I shouldn't problems?
Which are the drives that **Envy** installs, the open source or the propertary?

---

### Post by Sef on 2008-07-23
> So if I install the proprietary drivers I shouldn't problems?

Likely not, but no 100% guarantees.


> Which are the drives that Envy installs, the open source or the propertary?

The proprietary ones.  Open source drivers don't need a script.

---

### Post by aman.agx on 2008-07-23
What I did was this.
1. Downloaded NVIDIA-Linux-x86_64-173.14.09-pkg2 from Nvidia site.
2. downloaded libc-dev package
3. log out
4. CTRL-ALT-F1
5. log in as root
   or sudo the commands
6. killall gdm
7. sh NVIDIA-Linux-x86_64-173.14.09-pkg2.run
8. gdm
9. log in and added the following line to  /etc/default/linux-restricted-modules-common
DISABLED_MODULES="nv"

Reboot and it works fine

---

### Post by YaroMan86 on 2008-07-24
> **jombeewoof said:**
> I have the exact opposite suggestion. 
drivers straight from Nvidia don't work for me. 
The "new" driver from synaptic works like a champ though.

Nvidia GeForce 6800 GT

Ummmm... last I checked, nvidia-glx-new *is* the proprietary driver. And I've noticed installing from the nVidia website or from EnvyNG only managed to screw up my X config and I'd have to rebuild it.

But yeah, trust me, nvidia-glx-new is the proprietary driver for "new" cards. I believe there are two other proprietary drivers in the repository for older cards, but since my 6150SE chipset falls under nVidia's "new" category, I know little about them. That driver is maintained by nVidia. Hard to get more official than that.

The only open source driver out there I know of is the "nv" driver, which doesn't do 3D. Essentially a "get by" driver for nVidia chipsets. You can't use things like Compiz Fusion with it. Its one of the reasons why I'm not one of those "YOU MUST USE ONLY OPEN SOURCE OR LOSE YOUR SOUL" FOSSies. The open source "nv" driver is a joke, simply put. That and also use Flash, since Gnash simply isn't that good.

---

