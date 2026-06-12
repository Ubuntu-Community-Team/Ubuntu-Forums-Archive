---
title: "nvidia geforce 8400 GS"
date: 2007-07-30
forum: Hardware &amp; Laptops
---

### Post by hamburglar6 on 2007-07-30
today i installed a nvidia geforce 8400 GS in my machine (biostar tforce4 sli motherboard, 1 GB RAM, amd 64 3800+ x2).  when i boot my machine up, as the kernel is loading i get the following message:

> PCI: Failed to allocate mem resource #3:2000000@fe000000 for 0000:05:00.0 

when i use the open source 'nv' drivers, everything works fine.  when i use the 'nvidia' drivers my monitor blanks and doesn't come back until i boot into a terminal and change the drivers back to 'nv'.  I also have a gentoo partition and it's the same deal there.  

before this card i had a geforce 7300 LE which i was able to install the 'nvidia' drivers and get direct rendering to work.

thanks!
kevin

---

### Post by fcigoi on 2007-07-31
Exact same problem here, except that my new laptop came with that board and since then I have been unable to start XServer.
My question is: how do you switch to "nv" drivers ? I came to the conclusion that the Nvidia drivers built in Ubuntu 7.04 are not compatible with that board but while the new ones are introduced I'd love to use my laptop so I'll downgrade to nv if someone points me in the right direction

---

### Post by n8bounds on 2007-07-31
I have the same card in my dv6500--post here if you get a fix

oh and run sudo dpkg-reconfigure xserver-xorg, fcigoi, either from a TTY if you can boot normally and get to one, or from single user mode and then reboot

---

### Post by hamburglar6 on 2007-08-01
after poking around a little bit i've found that some people who had this problem had it resolved by updating their bios- it didn't work for me, but you might want to take a whack at it if you know what kind of motherboard you have.

fcigoi- just to add to what n8bounds said, ubuntu doesn't ship with the 'nvidia' drivers installed.  right now you are probably using either 'nv' or 'vesa'.  when your xserver crashes, you should be at a terminal (if you're not try alt + ctrl + f1) and type this

```
sudo nano -w /etc/X11/xorg.conf
```

go down to the 'device' section and see what is next to see which driver you are using.  you can just try both 'nv' and 'vesa' in those spots and reboot (or type startx at the command line- alt + ctrl + backspace will kill x and bring you back to the command line).  If that doesn't work the command that n8bounds gave will generate a new x configuration file for you.  if you want it to choose recommended defaults for most options (all except driver and resolution i think) add the -phigh option:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

if either of those drivers get x to work for you, you might want to try installing the 'nvida' drivers using Envy which can be found at [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

### Post by Scotty562 on 2007-08-03
Are you using Feisty or gutsy? If you're using Feisty try using envy to install the drivers. I had the same probelem when installing the nvidia drivers in gutsy.

---

### Post by hamburglar6 on 2007-08-04
I am using feisty and i did use envy.  After that didn't work I also used the nvidia installer and that produced the same results.

---

### Post by mooseboy on 2007-08-04
I also had a similar experience with my HP DV6500t. I was able to get the very latest nvidia beta drivers (off their website) running on gutsy gibbon for about 10 seconds. Compiz ran fine, but when I launched glxgears ,the machine locked up. I'm stuck with nv for now until proper ubuntu packages updated for nvidia are released.

---

### Post by hamburglar6 on 2007-08-04
You should file a bug report with nvidia if you want it to get fixed.  Just run 
```
nvidia-bug-report.sh
```
and it will generate a bug report log that you just have to attach it in an email to an address it gives you.  I did it last night and got a reply back within a couple of hours.

---

### Post by gamitor on 2007-08-09
I just order the Hp dv 2500t which has nvidia geforce 8400 GS and I have no experience with Ubuntu Linux. Will this laptop be able to install and run Ubuntu with Desctop effects ?

Thank You in Advance

---

### Post by dabl on 2007-08-09
The PCI bus error message goes WAY back:

[http://www.linuxforums.org/forum/redhat-fedora-linux-help/32870-pci-failed-allocate-mem-resource-error-pcie-fc3-64bit.html](http://www.linuxforums.org/forum/redhat-fedora-linux-help/32870-pci-failed-allocate-mem-resource-error-pcie-fc3-64bit.html)

I've been seeing it on every boot for almost a year.  AFAIK, it is not relevant to performance (or problems) on your system.   :)

---

### Post by hamburglar6 on 2007-08-10
dabl- thanks for the response.  i was wondering if that had much to do with my problem or not.  i've looked around the web a bit more for some stuff about my card and now i'm thinking the 12V rail on my power supply doesn't have enough current to run the card...although it seems a bit weird it would work with the 'nv' drivers if that were the case.  

i should be getting a new PSU in the mail monday- if that fixes it i'll post back then for anybody else who might check this thread out.

gamitor- the 8400 GS isn't really a top of the line card, but it should have no problem at all running desktop effects/beryl/compiz-fusion.  if you plan on using any really graphics intensive applications/games then you may want to disable the effects, but even that might be alright.  if you want to test how your graphics is performing after you install the nvidia drivers just type into a terminal

```
glxgears
```

with both the effects turned on and turned off.  compare the rendering capabilities of both and see how much the effects are draining your resources.

if you're unfamiliar with installing the nvidia drivers, a very useful tool is Envy which can be found here: [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by Kubunteando on 2007-08-10
By the way, just talked with HP.
If you install a different Operating System that Windows, your warranty is void.

They have good laptops but this is worring...

---

### Post by Draylorre on 2007-08-14
> **Kubunteando said:**
> By the way, just talked with HP.
If you install a different Operating System that Windows, your warranty is void.

They have good laptops but this is worring...

Just so you know, most places will recognize the warranty again if you install what was on there before is something happens. My friend bought a Vista laptop, installed XP, had some problems and reinstalled Vista and they gladly took back his laptop's warranty.

---

### Post by hamburglar6 on 2007-08-14
I got the new PSU today, and nothing was accomplished except for I'm $50 poorer.  That pretty much narrows it down to a problem with the linux kernel or the nvidia drivers (which is the one that seems more likely to me).

---

### Post by dansen926 on 2007-08-16
The most temporary fix I found was using the vesa drivers to get around until I could get the envy script to install all that nvidia goodness for me ;)

I'd also try to update the drivers manually. Envy is just nice because it automates everything for you.

---

### Post by ivantheviking on 2008-03-20
I have a similar problemo. Same graphics card. I used Envy to install the Nvidia drivers when I first installed the card and got no problems; everything worked great on this POS monitor (the reason I say POS its a 15 inch dell hand me down while i save up for an LCD). A couple weeks later I attempted to update ubuntu using the update manager, yet when I clicked install updates a window popped up as if it were loading but then it would go back to showing me which updates were available for download. So I installed the updates manually in terminal. after reboot I got a message saying my restricted drivers aren't working. so now I'm stuck with the nv drivers which wont let this tv go past 640x480 resolution.

I tried uninstalling and reinstalling the nvidia drivers in Envy and same thing. any suggestions?:-k

---

### Post by scottyrabbit on 2008-04-25
[http://aldeby.org/blog/?page_id=87#installing](http://aldeby.org/blog/?page_id=87#installing) 
this helped me out with a lot of things. 

i have an hp pavilion dv6500t with the maxed out hardware by the way

---

