---
title: "I'm a little slow"
date: 2005-09-02
forum: Hardware &amp; Laptops
---

### Post by reidmt on 2005-09-02
I am a new Linux user.  Completely.  I've been trying to install Ubuntu on my old laptop because it doesn't do anything well with Windows.  

After a couple of install hitches, I've got it running.  I don't know why, but it is absurdedly slow.  Really, really slow.  The trackpad can't control the pointer, which just jumps around.  The machine is slow to the point of being unusable.

It's an Acer TravelMate 602TER running a PIII 650Mhz processor on a 3.5Gb partition with a 600Mb swap area.  

Any help would be appreciated.

Thanks, in advance.

---

### Post by MdaG on 2005-09-02
[QUOTE=reidmt]I am a new Linux user.  Completely.  I've been trying to install Ubuntu on my old laptop because it doesn't do anything well with Windows.  

After a couple of install hitches, I've got it running.  I don't know why, but it is absurdedly slow.  Really, really slow.  The trackpad can't control the pointer, which just jumps around.  The machine is slow to the point of being unusable.

It's an Acer TravelMate 602TER running a PIII 650Mhz processor on a 3.5Gb partition with a 600Mb swap area.  

Any help would be appreciated.

Thanks, in advance.[/QUOTE]


Hmm your system specs seem a little low for a Ubuntu system... Maybe that's why?

---

### Post by s_p_a_r_k_y on 2005-09-02
how much memory do you have?

---

### Post by reidmt on 2005-09-03
128Mb ram.  The odd thing is that it sometimes starts up smoothly and with no problems, but suddenly moves at a snail's pace when asked to do something.  

RKK

---

### Post by PaganHippie on 2005-09-03
How much physical RAM do you have installed?

---

### Post by PaganHippie on 2005-09-03
[QUOTE=reidmt]128Mb ram.  The odd thing is that it sometimes starts up smoothly and with no problems, but suddenly moves at a snail's pace when asked to do something.  

RKK[/QUOTE]
 Do you notice *a lot* of HDD activity when you ask it to do something?  That would indicate that the OS is hurting for memory.  More RAM never hurts....  ;)

---

### Post by drummer on 2005-09-03
[QUOTE=reidmt]128Mb ram.  The odd thing is that it sometimes starts up smoothly and with no problems, but suddenly moves at a snail's pace when asked to do something.  

RKK[/QUOTE]
 128meg of RAM is about the absolute minimum for running Gnome, I use 100 or so just on a fresh boot, and am using 160meg at the moment (firefox uses quite a lot). I'd look into installing XFCE4 as your desktop manager, search for the xfce4 package in synaptic (not xfce though, have to have the 4) or in a terminal:```
sudo apt-get install xfce4
```. Or get some more ram if you want to run Gnome at an acceptable speed.

---

### Post by reidmt on 2005-09-03
When running well, the HD sounds like a regular computer.  When not running well, which is 9x out of 10, it runs in fits and spurts.  

RKK

---

### Post by reidmt on 2005-09-03
[QUOTE=drummer]128meg of RAM is about the absolute minimum for running Gnome, I use 100 or so just on a fresh boot, and am using 160meg at the moment (firefox uses quite a lot). I'd look into installing XFCE4 as your desktop manager, search for the xfce4 package in synaptic (not xfce though, have to have the 4) or in a terminal:```
sudo apt-get install xfce4
```. Or get some more ram if you want to run Gnome at an acceptable speed.[/QUOTE]

I may be in the market for more ram or a distribution that can be a better fit for my system.  The install CD says that it requires a minimum of 32 Mb ram, and, while it ships with no warranties, either express or implied, without even the implied warranty of merchantibility or fitness for a particular purpose, I don't think they'd underestimate the requirements that much.  

Other threads indicate that it can run on some pretty small-scale machines.  

Re: research

Paraphrasing Donald Rumsfeld, you install linux on the machine that you have, not the machine that you wish you have.  I had an Acer laptop and looked around for a distro I thought I could handle.  I'd still like to get it to work and have heard generally positive reviews about its compatibility with most hardware systems.  Acer in generally seems to have some compatibility problems with linux, and I chose something I thought would work.  (I also heard that the partitioner was fairly easy to work with, and I did it with no prior experience.)

Off to wine tasting in the Dalles, 

RKK

---

### Post by drummer on 2005-09-03
The requirement of 32mb is the minimum for the text-based installer to run properly. Once Ubuntu, or any Linux distro is booted, the required amount of ram depends heavily on the desktop environment you use (Gnome, KDE, XFCE, Fluxbox, IceWM, etc, etc.) and the programs you run. Before trying another distro, give xfce a go. 

The results will be the same if you use another distro and still use Gnome or KDE as your DE, they are both quite bloated and need at LEAST 128mb of ram just to start up, otherwise your computer will be using the swap partition constantly as 'virtual memory' which is, as you've seen, very slow. I can also suggest you use Abiword instead of Open Office for word processing, which is much lighter than OO.

---

### Post by mlord on 2005-09-04
Your notebook does not have enough RAM for Gnome or KDE desktops.

Install XFCE instead, and Unbuntu should run just fine.

---

