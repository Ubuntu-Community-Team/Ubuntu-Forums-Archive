---
title: "Low resolution with unclaimed GeForce 6100 nForce 405"
date: 2015-11-06
forum: Hardware
---

### Post by bela83 on 2015-11-06
Hi !

I had a PC running 14.04 not working for quite a long time (over a year). I put it back in order yesterday, and did all the upgrades. Since then, it can't run in full graphics mode. I have to choose recovery mode in grub, then failsafeX to get to the desktop.

I am using the nouveau driver.

The hardware is :
> 
$ sudo lshw -C display

  *-display NON-RÉCLAMÉ   
       description: VGA compatible controller
       produit: C61 [GeForce 6100 nForce 405]
       fabriquant: NVIDIA Corporation
       identifiant matériel: d
       information bus: pci@0000:00:0d.0
       version: a2
       bits: 64 bits
       horloge: 66MHz
       fonctionnalités: pm msi vga_controller bus_master cap_list
       configuration: latency=0
       ressources: mémoire:fd000000-fdffffff mémoire:d0000000-dfffffff mémoire:fc000000-fcffffff mémoire:febc0000-febdffff


Please guide me to which command output I can give to help you.
Thanks in advance.

---

### Post by mörgæs on 2015-11-06
The 6xxx series from Nvidia is well-known in the forum.

Try a fresh install of Lubuntu 15.10 where you accept closed-source drivers during install.

---

### Post by bela83 on 2015-11-07
> **mörgæs said:**
> The 6xxx series from Nvidia is well-known in the forum.

Try a fresh install of Lubuntu 15.10 where you accept closed-source drivers during install.

Thanks mörgæs. So I will wait for 16.04 because LTS matters to me (I'm in no hurry).

You advise Lubuntu because Ubuntu would be too heavy ? How is Lubuntu these days ? Haven't tried it in a long time.

---

### Post by mörgæs on 2015-11-07
Light and very low on bugs. You can try it in a live boot.

---

### Post by bela83 on 2015-11-07
Thanks ! Do you have by any chance a link to a thread for Nvidia 6xxx series ?
And we could close the topic.

---

### Post by mörgæs on 2015-11-07
[http://ubuntuforums.org/showthread.php?t=2290250&page=2&p=13337015&viewfull=1#post13337015](http://ubuntuforums.org/showthread.php?t=2290250&page=2&p=13337015&viewfull=1#post13337015)

---

