---
title: "Nvidia restricted driver wont install Ubuntu 8.10"
date: 2008-10-23
forum: Hardware
---

### Post by apreichner on 2008-10-23
I recently installed Ubuntu 8.10, after hearing it was pretty stable, and I figured only a few days to the release, it should be. Well installation went smoothly and I boot in and check for updates, there are none. So I then proceed to try to install the Nvidia restricted driver (driver v 177). It asked for my password; I entered it. It then came up with a quick download box but then the box vanished and the red dot for the driver not being in use stayed there. Each time I try installing the driver it does this, whether I restart or not. Sorry if this is the wrong forum to post this in, I'm a bit of a noob here.

---

### Post by phidia on 2008-10-23
What specific model nvidia card are you trying to get working?

Trying to jump the release date obviously doesn't work. There is a reason there is a date set for the final release and part of that is resolving bugs.

There are [46 bugs reported]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-177/+bugs") about nvidia driver issues at launchpad against intrepid ibex.

---

### Post by apreichner on 2008-10-23
I'm trying to install it for Nvidia 7600 gs.

EDIT-

I don't see my issue on any of the bugs reported. Is there a way to manually install the drivers through the terminal, that might give me a better understanding of what the error is if there is one.

---

### Post by apreichner on 2008-10-23
SOLVED-

I went on the Intrepid IRC. Apparently it was not finding the driver in the sources list, although the restricted source was in there. I needed to do a apt-get update. After I did that, the driver installed flawlessly and works great!

---

### Post by phidia on 2008-10-23
> **apreichner said:**
> SOLVED-

I went on the Intrepid IRC. Apparently it was not finding the driver in the sources list, although the restricted source was in there. I needed to do a apt-get update. After I did that, the driver installed flawlessly and works great!

Great to hear and this will help others too.

You can mark the thread solved by editing the title box With the word (Solved) in front of your desription.

---

### Post by xtaski on 2008-10-30
Thanks apreichner - this helped me too. It's surprising to see this bug also made it into the actual 8.10 release.

---

### Post by TheBananaBeast on 2008-10-30
no good here.  Ran apt-get update, sat around for a while.  when I try to install the driver now the window just hangs at 0% "Downloading and Installing Driver".  Suggestions?

---

### Post by jacob21 on 2008-10-30
I just installed ibex, ran an update, and installed the restricted driver.  After I restarted my computer, it booted into the command line, and I can't start x.  Could someone tell me how to install the driver from the command line.  Any help would be greatly appreciated.

---

### Post by gnom on 2008-10-30
> **TheBananaBeast said:**
> no good here.  Ran apt-get update, sat around for a while.  when I try to install the driver now the window just hangs at 0% "Downloading and Installing Driver".  Suggestions?
Same for me -  although I didn't have to do apt-get update... I have GF8400 on HP dv6750ew laptop.

---

### Post by Endolith on 2008-10-30
I have the same problem.  Hanging at "downloading and installing driver".  Tried updating apt-get, install -f, etc.

Either that or it finished and then the little circle remains at "not activated"

---

### Post by TheBananaBeast on 2008-10-30
ha ha, got it.  the hanging at zero issue just stopped happening.  Not really helpful, I know.  My guess would be server traffic issues?

---

### Post by Endolith on 2008-10-30
> **TheBananaBeast said:**
> ha ha, got it.  the hanging at zero issue just stopped happening.  Not really helpful, I know.  My guess would be server traffic issues?

That happened to me but it still wouldn't say "Activated".  Then I rebooted and it won't go into GDM anymore.  :mad:

How do I make my computer usable again?  This is exactly the kind of neverending driver problems that made me use Ubuntu in the first place, and now I'm stuck with them again.

---

### Post by sirchmeister on 2008-11-01
Try this for removing them and getting back to where you were:

After logging in at the terminal do:

sudo nano /etc/X11/xorg.conf

Find the section which lists the Nvidia device and change the entry from "nvidia" to "nv".

Then hit CTRL+X and Y to save and then ENTER.

Then:

sudo apt-get remove dkms
sudo apt-get install dkms

---

### Post by Epistaxis on 2008-11-01
> **sirchmeister said:**
> Try this for removing them and getting back to where you were:

After logging in at the terminal do:

sudo nano /etc/X11/xorg.conf

Find the section which lists the Nvidia device and change the entry from "nvidia" to "nv".

Then hit CTRL+X and Y to save and then ENTER.

Then:

sudo apt-get remove dkms
sudo apt-get install dkms

I'm having the same problem and this didn't solve it. If I use the "default" drivers, I can get a full-resolution desktop but I can't enable desktop effects. If I try to install the NVIDIA 177 drivers, the installation finishes normally and says I have to reboot, but when I do, GDM fails. I've tried apt-get update and reinstalling dkms and nvidia-glx-177. I have a fairly new card (GeForce 8800 GTS) so it shouldn't be a legacy issue.

Has anyone gotten 8.10 to work with Nvidia restricted drivers, or are they simply incompatible with Intrepid?

---

### Post by phidia on 2008-11-01
> **Epistaxis said:**
> I'm having the same problem and this didn't solve it. If I use the "default" drivers, I can get a full-resolution desktop but I can't enable desktop effects. If I try to install the NVIDIA 177 drivers, the installation finishes normally and says I have to reboot, but when I do, GDM fails. I've tried apt-get update and reinstalling dkms and nvidia-glx-177. I have a fairly new card (GeForce 8800 GTS) so it shouldn't be a legacy issue.

Has anyone gotten 8.10 to work with Nvidia restricted drivers, or are they simply incompatible with Intrepid?

Some 8 & 9 series cards have been not recognized it seems.

You could try booting in recovery mode and typing "xfix" That's suppose to correct x problems now. If you can download the latest driver from the nvidia site you could try installing the driver "by hand".
See the wiki [here]("https://help.ubuntu.com/community/BuildYourOwnNvidiaGlx") and the links therein.
That wiki mentions issues specific to your card.

---

### Post by Epistaxis on 2008-11-02
I solved my own problem. I hadn't let the 8.04->8.10 upgrade modify my /boot/grub/menu.lst because I have a dual-boot on a RAID 0 and it's very fragile. So, GRUB was still loading the old kernel. Once I finally realized this, I changed all instances of "2.6.24-16" to "2.6.27-7" in /boot/grub/menu.lst (and "8.04" to "8.10" while I was at it), and as soon as I rebooted, the Nvidia drivers were already working.

Sorry if it doesn't help anyone else, but make sure you don't overlook this possibility.

---

### Post by mikeeve on 2008-11-20
> **TheBananaBeast said:**
> no good here.  Ran apt-get update, sat around for a while.  when I try to install the driver now the window just hangs at 0% "Downloading and Installing Driver".  Suggestions?

I'm having the same problem with "Downloading" stopping at 0%. I can't even force the download window to close. After all these years of Ubuntu/Linux developement, still these inane problems.:confused:

(I'm actually working with ATI drivers, not nVidia.)

---

### Post by Argeroth on 2008-11-20
> **mikeeve said:**
> I'm having the same problem with "Downloading" stopping at 0%. I can't even force the download window to close. After all these years of Ubuntu/Linux developement, still these inane problems.:confused:

(I'm actually working with ATI drivers, not nVidia.)

Have you tried selecting a 'preferred server' in the package manager settings?  It runs about 200 tests to determine the 'best' server for downloading.  Try it if you haven't and see if it makes any difference.

---

### Post by Endolith on 2008-11-20
I got my Nvidia driver installed using envy instead of jockey.

[https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/298584](https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/298584)

---

### Post by birddog165 on 2009-01-28
Thanks, I had the same problem and all I needed was to run apt-get update
Weird how that stuff works

---

