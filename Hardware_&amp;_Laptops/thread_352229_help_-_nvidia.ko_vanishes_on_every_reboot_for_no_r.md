---
title: "help - nvidia.ko vanishes on every reboot for no reason?"
date: 2007-02-03
forum: Hardware &amp; Laptops
---

### Post by notasquirrel on 2007-02-03
Hi, another nvidia driver problem...

I've been using my laptop and not really doing anything to it, not installing any new software, not using the repositories or anything.  I did install some of the updates the system notified me about.  Now, all of a sudden, between one boot and the next, my nvidia driver kernel module vanishes on every reboot and GDM can't start, kicks me out to a text error screen.  :confused: 

It's normally located here:
/lib/modules/2.6.17-10-generic/volatile/nvidia.ko

Every reboot, it vanishes from that location and can only be found here:
/lib/modules/2.6.17-10-generic/kernel/drivers/video/nvidia.ko

My fix so far is to copy it from /lib/yadayada/drivers/video, to /lib/yadayada/volatile.  Then I can start GDM.  

Strangely enough, this coincides with a second problem that I would normally say is unrelated...  Whenever I start Compiz now, after copying the driver to get Gnome running, I get no window decorations.  Also it seems I used to be able to start gnome-window-decorations, but now that command doesn't exist any more.  At least the shell won't tab-complete to it and the 'locate' command doesn't find it.

Seems to me I need to find out where GDM / X / Gnome / whatever is looking for the nvidia drivers, and update whatever config file to point to where they now like to reside.  I have no clue where to start looking.

So...  [puppy eyes] Help? [/puppy eyes]


Kernel version is 2.6.17-10-generic
Nvidia is 9631, from the nvidia archives (NVIDIA-Linux-x86-1.0-9631-pkg1.run)
Xorg is 1:7.1.1ubuntu6.2
X11-common matches Xorg
gdm is 2.16.1-0ubuntu4.1
Compiz is 0.3.4.2-0gandalfn1
Laptop is an AlienWare Area-51m if that helps.
Video card is one of those mini-AGP laptop things, an FX-Go 5700

The compiz version kind of sounds higher somehow, and it has stopped bugging me to do a dist-upgrade to get the new version.  I can't imagine a compiz upgrade changing anything in regards to nvidia drivers though?  That should be completely abstracted from compiz.

---

### Post by notasquirrel on 2007-02-03
BTW I just noticed that after these steps:

boot computer
copy nvidia.ko
stop gdm
start gdm
run 'locate nvidia.ko'

The driver has moved again and is no longer in /lib/yadayada/volatile.  So it's happening either periodically, or on gdm start :confused:, or both on boot and on gdm start, or maybe on shutdown.

---

