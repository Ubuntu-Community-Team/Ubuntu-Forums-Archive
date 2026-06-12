---
title: "how do i determine my video card?"
date: 2008-10-15
forum: Hardware
---

### Post by DetroitLibertyPenguin on 2008-10-15
So I am attempting to play a game called Regnum Online, an open source RPG similar to World of Warcraft, except free in both the beer and speach sense. 

However after installation, I start the program and login using my user name and password and I get an erro rthat says ```
 ERROR
Unsupported video card! 
There are three possible causes for this error:
1. Your video card is too old
2. You haven't installed the latest available drivers
3. You haven't installed the latest DirectX version
```

Granted, my machine is pretty old, an HP pavilion that originally was loaded with Windows 98. I have no idea what video card I have but Regnum Online posted some information on supported video cards on their website [http://www.regnumonlinegame.com/index.php?l=1&sec=20&subsec=41](http://www.regnumonlinegame.com/index.php?l=1&sec=20&subsec=41)

So my real question is, just as the forum thread says, how do i determine what video card I am using, preferably threw the GUI or the shell (consolue) as opposed to opening up my mahcine and hoping that the card says a brand name on it.

---

### Post by cariboo on 2008-10-15
In a terminal type:

```
sudo lshw -C video
```

It should give you an output something like this:

```
sudo lshw -C video
[sudo] password for jim: 
  *-display               
       description: VGA compatible controller
       product: C51PV [GeForce 6150]
       vendor: nVidia Corporation
       physical id: 5
       bus info: pci@0000:00:05.0
       version: a2
       width: 64 bits
       clock: 66MHz
       capabilities: pm msi bus_master cap_list
       configuration: driver=nvidia latency=0 module=nvidia
```

Your results will be different of course.

Jim

---

### Post by DetroitLibertyPenguin on 2008-11-12
When I run that I get 

 *-display               
       description: VGA compatible controller
       product: 82810 (CGC) Chipset Graphics Controller
       vendor: Intel Corporation
       physical id: 1
       bus info: pci@0000:00:01.0
       version: 02
       width: 32 bits
       clock: 66MHz
       capabilities: pm vga_controller bus_master cap_list
       configuration: driver=i810_smbus latency=0 module=i2c_i810
so what does that mean to me?

---

### Post by Naveedch on 2013-02-17
This is a very late response but better late than never, seems like you have an on-board graphics card. Gaming an on-board video is not recommended even for low res games such as mine-craft. Google the product: 82810 (CGC) Chipset Graphics Controller and you will find more information about your video adapter.

---

### Post by Old_Grey_Wolf on 2013-02-17
Please do not post in a thread that is more than a year old. The OP has not logged  in in over a year. Thread closed.

---

