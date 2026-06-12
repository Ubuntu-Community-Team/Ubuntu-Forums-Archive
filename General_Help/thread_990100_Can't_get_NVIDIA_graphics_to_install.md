---
title: "Can't get NVIDIA graphics to install"
date: 2008-11-22
forum: General Help
---

### Post by JonathanConway on 2008-11-22
I just installed Ubuntu (Intrepid Ibex).

I'm trying to install the NVIDIA graphics drivers through the "Hardware Drivers" screen, but it doesn't seem to work.

I click "NVIDIA accelerated graphics driver (version 173)" and click the "Activate" button. The first time I did this, it asked for the Admin password, which I entered. I checked the box to "remember", so now it doesn't prompt me for the password. At any rate, when I click the button, a window pops up that says "Downloading and installing driver" for a split second. Then it dissapears and nothing else happens.

I've tried this heaps of times and also tried rebooting, but nothing seems to help.

Any ideas?

---

### Post by Bucky Ball on 2008-11-22
So in System->Administration->Hardware Drivers there is no green button or tick to indicate the driver is in use? You could perhaps paste in a terminal:

sudo apt-get update

... and try again. In the top right on the top toolbar, have you got an arrow icon pointing downwards? If so, click that and it will download all updates, then it should work for you. Unless you have done that already, then back to square one.

---

### Post by Moezzie on 2008-11-22
I dont really trust the Restricted drivers and envy, they usually dont work for me.
The way i always do it is:
[LIST=1]
[*]Download the drivers form nvidias own site
[*]Shut down gdm
[*]Unpack and install the drivers manually
[*]Reboot
[/LIST]
Try it out.

---

### Post by Bucky Ball on 2008-11-23
> **Moezzie said:**
> I dont really trust the Restricted drivers and envy, they usually dont work for me.
The way i always do it is:
[LIST=1]
[*]Download the drivers form nvidias own site
[*]Shut down gdm
[*]Unpack and install the drivers manually
[*]Reboot
[/LIST]
Try it out.

? No different. You're just doing it manually.

---

### Post by coop925 on 2008-11-25
I'm in a similar position and I'm having zero luck on getting it straightened out... or finding anything on here about it. 

I've got an Acer (crap) Aspire 5520. It's got Nvidia 7000M video and an Atheros wifi card. Surprisingly, the wireless works out of the box this time, but the video is NOT working - best I can get is 800x600. I've attempted both versions of the install described above, but when I try the 'download, "sudo killall gdm", ./NVIDIA...' it has an issue with the kernel - specifically looking for an *older* version than is installed. *grumble*

Xorg.conf edits didn't fix it either. I'm at a loss.

---

### Post by Glitchd on 2008-12-26
I too am having the same problems with nvidia.
I have nvidia 7000m in my acer 5520-5156 laptop.
I just cannot get the graphics to be right(everything is huge)
I am kind of a noob.
Nothing I do will get the driver to display correctly.
any help would be much appreciated.
p.s.-is there a way to just reinstall 8.04 while keeping everything thats in my home folder?
I really dont want to go through the process of copying all
of my home folder jus to paste it back in after the fresh install.
again any and all help would be much appreciated.
_GLiTcHD:confused:

---

### Post by jonkulp on 2009-02-19
Can anybody post a complete working xorg.conf file for this laptop? Acer Aspire 5520 with Nvidia Geforce 7000m graphics card, running 8.04. 

I'm trying to sort out the same problem as everyone else on this thing for one of my students with no luck.  It's a 1280x800 native-resolution screen and the best I can get is 1024x768.  The Nvidia driver, no matter how I install it (envy, hardware drivers, or downloading/installing from Nvidia's site), gets no better than 800x600.  We had it working properly once, with compiz rocking and everything, but after he ran updates one day the graphics got borked.  I can't remember how I finally got it working the first time, but I think it was with a an older kernel, and either the kernel update or the xserver update jacked it up.  Tried booting with older kernel and it doesn't make a difference.  Tried adding lines to the xorg.conf file manually without success.  Sigh.  Please, if you have this laptop running at 1280x800 would you be so kind as to post your xorg.conf file so I can try it?  Many thanks...

---

### Post by bixejo on 2009-02-19
My desktop computer is also equipped with a NVIDIA graphics card. When I tried to upgrade to Ubuntu 8.10 (I'm currently running 8.04) I got a warning pop-up window saying that there is no NVIDIA controller working properly in 8.10, and gave me the chance of canceling the upgrade process, and of course that's what I did.

 I don't know further details, but I would suggest you to install Ubuntu 8.04 LTS instead of 8.10.

Good luck,

---

### Post by jonkulp on 2009-02-19
Yes, the laptop in question is already running 8.04.  Seems like that ought to help the problem but I can't fix it so far. :(

---

