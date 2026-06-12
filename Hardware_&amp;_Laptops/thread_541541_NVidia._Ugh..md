---
title: "NVidia. Ugh."
date: 2007-09-02
forum: Hardware &amp; Laptops
---

### Post by detroit/zero on 2007-09-02
Since this is a hardware issue, I suppose this is where it goes. If not, I trust someone will relocate it accordingly.

First, my basics:
HP Pavillion a1030n Desktop w/ Intel P4 3.0GHz dual processor and Intel 845G onboard graphics
NVidia GeForce FX 5500
Fresh install of Feisty Fawn

Before a system update somewhere around May or maybe June, I had Feisty running along quite nicely with the NVidia 9755 driver. Beryl ran like a champ. Compiz/Fusion ran even better. Some update came through (a kernel update, I think?) and everything broke. Driver re-installation attempts were unsuccessful. I abandoned my desktop for a while and used my laptop since it's NVidia free and much less of a hassle to work with.

Here I am now back on my desktop trying to get my NVidia card working again and I'm having a much harder time than I remember it being - [LIST]
[*]The 9755 no longer works (NVIDIA-Linux-x86-1.0-9755-pkg1.run or some such thing).
[*]The new NVidia Glx (nvidia-glx-new_1.0.9755+2.6.20.5-15.20_i386.deb) doesn't work either.
[*]The other driver from NVidia (100.14... something or another) doesn't work.
[*]Restricted Drivers Manager doesn't work.
[*]Envy doesn't work.[/LIST]I realize through trials and errors dating back to my initiation into Edgy Eft that the Intel onboard graphics have to be blacklisted in both */etc/modprobe.d* and in */etc/hotplug*. I seem to remember the "glx" module being commented out in *xorg.conf* and having to add the "nvidia" module to the module loader section. I think I had to add lines like "renderaccel = true" and "addargblxvisuals = true" (spelling may be off.. I'm just working out of memory here..), "pci = 0.0.2", and things like that.  

But even after all this is done, I still get error messages and X won't load. Sometimes it's an invalid GPU kernel message, sometimes it's an invalid module loader (glx is always the source of an error when present) message, sometimes this, sometimes that.. 

I'm afraid I don't have any current logs to show at the moment. I had to disable NVidia and reboot on the Intel Chipset.

Can anybody offer any advice/help/guidance?

I know I'm rambling, but it's late and I've been at this a while now. If there's info I need to provide, I'll gladly do so.

Thanks for any help...

---

### Post by jocko on 2007-09-03
To help troubleshooting, it may be necessary to find out exactly which errors you get.

First backup your current xorg.conf (working with the intel onboard gpu):
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.intel
```
Then reboot and disable the intel gpu in bios.

When X fails and you are kicked back to the command line, login and run the following to enable the nvidia in xorg.conf (you may want to print or write these commands on a piece of paper before you start):

```
sudo killall gdm
sudo dpkg-reconfigure xserver-xorg
```
(in the first screen select nvidia, accept the default options in the following screens unless you know they are wrong)
To attempt to start xorg without reboot:
```
sudo gdm
```
If it fails, reboot and see if it works. If you still get kicked back to command line, login and run his:

```
sudo killall gdm
cat /var/log/Xorg.0.log | grep EE >> errors.txt
sudo cp /etc/X11/xorg.conf.intel /etc/X11/xorg.conf
```

That will save any errors that occured in a file named errors.txt in your home directory and restore your xorg.conf to work with your intel gpu.
Reboot, re-enable the onboard gpu in bios and copy/paste the contents of ~/errors.txt here.

Hopefully the log file will indicate what the problem is and someone will help you to get it working.

---

