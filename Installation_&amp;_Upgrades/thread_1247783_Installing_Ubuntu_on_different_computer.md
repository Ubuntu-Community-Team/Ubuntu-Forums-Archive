---
title: "Installing Ubuntu on different computer"
date: 2009-08-23
forum: Installation &amp; Upgrades
---

### Post by BarsMonster2 on 2009-08-23
Hi there.
I am buying a small server and would be placing it in a datacenter, which is in different city.

So I decided to pre-install Ubuntu 9.04 Server 64-bit on a HDD, tune everything, test it, and then just replace HDD when I would get a server.

Is it safe to assume that it would just work on a new hardware?
Hardware is pretty different:

My PC: Intel P45+C2D8400, 8Gb of RAM, 2 Marvell network adaptors. Ubuntu was not able to use eth0, so I had to disable it in bios, and do install with eth1. HDD in first SATA port.

Small Server: Atom 330+nVidia ION, 4Gb of RAM. Same HDD in the only SATA port.

---

### Post by raymondh on 2009-08-23
> **BarsMonster2 said:**
> 

So I decided to pre-install Ubuntu 9.04 Server 64-bit on a HDD, tune everything, test it, and then just replace HDD when I would get a server.

Is it safe to assume that it would just work on a new hardware?
Hardware is pretty different:


You'll have to tune it to your hardware.

---

### Post by BarsMonster2 on 2009-08-23
> **raymondhenson said:**
> You'll have to tune it to your hardware.
What needs to be tuned for different hardware?
From the software point, setting should be the same (MySQL options, nginx, e.t.c - I am setting everything keeping in mind that I have 4 Gb)

---

### Post by raymondh on 2009-08-23
> **BarsMonster2 said:**
> What needs to be tuned for different hardware?
From the software point, setting should be the same (MySQL options, nginx, e.t.c - I am setting everything keeping in mind that I have 4 Gb)

You are right ... settings should be the same.

I was thinking more of the necessary drivers needed for the new machine.

---

### Post by BarsMonster2 on 2009-08-23
> **raymondhenson said:**
> You are right ... settings should be the same.
 
I was thinking more of the necessary drivers needed for the new machine.
 
So that is my qestion, is Ubuntu usually able to pick up all necessary drivers automatically, or not. If not, what actions are needed to have it work with new hardware? (for example, if network drivers would not work, I will have to install drivers now in advance.).

---

### Post by raymondh on 2009-08-23
> **BarsMonster2 said:**
> So that is my qestion, is Ubuntu usually able to pick up all necessary drivers automatically, or not. If not, what actions are needed to have it work with new hardware? (for example, if network drivers would not work, I will have to install drivers now in advance.).

Just re-read your first post.  have you considered the LTS versions?

you're on the right track.... researching :)

Usually, Ubuntu will pick up drivers.  Browse the manufacturer's website and check if the have linux-based drivers for your hardware.  If so, chances are Ubuntu will pick it up as they could've been included already in the reps.  If not, you can manually install them prior to final deployment of your final configuration.  If no drivers, you may have to search open-source.

Whilst in a different center, you still (hopefully, you will) have access to the server remotely.  Manipulation/maintenance ought to be within your admin priveledges.

Good luck.

---

### Post by BarsMonster2 on 2009-08-23
> **raymondhenson said:**
> Just re-read your first post. have you considered the LTS versions?
 
Whilst in a different center, you still (hopefully, you will) have access to the server remotely. Manipulation/maintenance ought to be within your admin priveledges.
 
Well, this is personal server, so I would prefer to be closer to the bleeding edge :-)
 
Yes, remote access is possible, but it's around 10$/hour.
 
Thanks for the answers.

---

