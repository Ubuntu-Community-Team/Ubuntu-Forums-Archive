---
title: "Wireless and double clock speed issues for compaq presario V2000 series"
date: 2006-02-17
forum: Installation &amp; Upgrades
---

### Post by marisy2k on 2006-02-17
I would like to first thank all the people who helped me either directly or
indirectly to get my ubuntu set up just like I wanted :) 

Anyone who is using the same pc as me compaq presario V2405CA should be able
to get their wireless network up as well be able to correct that weird clock speed
problem one might have.

For the wireless all I do once I install Ubuntu:

1. Install ndiswrapper-utils using Synaptic Package Manager in System->Administration.

2. Next get the windows drivers for the wireless(bcmwl5.inf, bcmwl5.sys and
    layout.bin) in my case. You should be able to get hold of it in your drivers cd
    that came with your laptop or be able to download them somewhere online.

3. Open up a terminal and go to the folder containing the driver files. Now type
  - sudo ndiswrapper -i bcmwl5.inf
  - sudo modprobe ndiswrapper
  - sudo ndiswrapper -m
:Note that after you type the modprobe line your light should go up.

4. Now open up Networking in System->Administration. wlan0 should be displayed
    there. Select it and click Properties. Enable it and set connection as dhcp and
    specify your essid and click ok.

5. Now activate wlan0 if it's not already activated and select wlan0 as your default
    gateway device and then end it by clicking OK.

That should get your wireless up and running.

Note that at the time of this post ipv6 did not do well so I disabled it which improved
my internet connection speed significantly. Search for "disable ipv6" in the
forum.

For the clock speed problem:

I actually performed a "linux noapic nolapic" when I installed Ubuntu from the
CD so that set the kernel parameter needed to correct the clock speed problem.

If you already have Ubuntu installed:

- First reboot and press escape to get to the grub menu.
- Press e and type noapic and nolapic to the end of the line and press enter.
- Now press b and see if that fixed the clock speed problem for you.

To make the change permanantly edit /boot/grub/menu.lst and add "noapic nolapic" to the end of the kernel line. It should look something like this:

title		Ubuntu, kernel 2.6.12-9-386 
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hda1 ro noapic nolapic quiet splash
initrd		/boot/initrd.img-2.6.12-9-386
savedefault
boot

...<some other lines>...

Hope that helps.

---

