---
title: "How do I install the NVIDIA drivers I downloaded? (it's not in additional drivers)"
date: 2015-03-06
forum: Hardware
---

### Post by gammies on 2015-03-06
So I downloaded the latest NVIDIA drivers from the NVIDIA website.  When I go to Software and Updates it doesn't show the latest update but gives me a few options.  None of them display quite right.  When I try gaming I get extreme FPS drop and lag.  Also, sometimes when I view youtube videos it looks choppy.  Anyways, it's pretty clear that the drivers on the software and updates don't work quite right.  

How do I install them manually?  All the tutorials I found seem to automatically fetch drivers that are in my additional drivers section.  I can barely play counter-strike 1.6 in the low graphics setting, forget about TF2.  Obviously something is wrong here and I want to try using the latest NVIDIA drivers before giving up trying to game on Ubuntu.  I am on the latest version of UBUNTU in 64bit and using a GTX 570 in case it matters.

---

### Post by oldfred on 2015-03-06
Generally better not to install from nVidia directly. You have to in effect reinstall on every kernel update.
The one's from Ubuntu repository are a bit older and usually work with bit older cards.
If you have to have the newest best to use a ppa, there are several but be sure to use one that you know is a good reliable source.  And often you need not just nVidia driver, but support software and maybe a newer kernel to be able to use all that new software. 

If you have installed nVidia and want to change to a different source, be sure to totally purge old install or you get conflicts and even more issues.

       sudo mv /etc/X11/xorg.conf /etc/X11/xorg/conf.old
Shows any file with nvidia in name, lots of files.
sudo find / -name "nvidia*"
Shows versions in repository:
sudo apt-cache search nvidia-sett*
Lists installed version, in/with your kernel:
dkms status
# Houseclean out all old versions to avoid issues
sudo apt-get remove --purge < nvidiadriverpackagename>
# [ using the correct names] for each driver, before running:
sudo apt-get purge nvidia*


 Install Nvidia 340.24 from ppa:xorg-edgers/ppa
[http://www.sysads.co.uk/2014/07/install-nvidia-340-24-driver-ubuntu-14-04/](http://www.sysads.co.uk/2014/07/install-nvidia-340-24-driver-ubuntu-14-04/)
14.04 drivers for Nvidia GeForce GT 730 desktop board - 
[http://ubuntuforums.org/showthread.php?t=2240702](http://ubuntuforums.org/showthread.php?t=2240702)
PPA for nVidia mamarley pps
[http://ubuntuforums.org/showthread.php?t=2256437&p=13185945#post13185945](http://ubuntuforums.org/showthread.php?t=2256437&p=13185945#post13185945)
[https://launchpad.net/~mamarley/+archive/ubuntu/nvidia](https://launchpad.net/~mamarley/+archive/ubuntu/nvidia)
All the current drivers xorg-edgers PPA
[https://launchpad.net/~xorg-edgers/+archive/ubuntu/ppa/+packages](https://launchpad.net/~xorg-edgers/+archive/ubuntu/ppa/+packages)
Oibaf PPA discusion
 [http://www.phoronix.com/scan.php?page=article&item=ubuntu_1310_oibaf&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_1310_oibaf&num=1)

---

### Post by efflandt on 2015-03-07
Your video card has been on the market for a number of years, so it is NOT a card that needs the latest cutting edge drivers. I have never used the run script directly from Nvidia to install Linux drivers, so not sure how to cleanly remove them. But if you can figure that out or fresh install Ubuntu this should give you most recent drivers from the regular repos:```
sudo apt-get update
sudo apt-get install nvidia-331-updates
```That worked even with my GTX 750 Ti that has a new Maxwell chip. The only reason I installed a newer version (nvidia-346) from xorg-edgers ppa was to play around with video overclocking. But without overclocking it runs no different nor faster than nvidia-331-updates package from the normal Ubuntu repositories.

---

### Post by gammies on 2015-03-07
Ok, so this probably isn't going to solve my issue but here is the answer to my question.

[http://www.binarytides.com/install-nvidia-drivers-ubuntu-14-04/](http://www.binarytides.com/install-nvidia-drivers-ubuntu-14-04/)

I'll let you know how this new driver works out for me.

EDIT: This turned out to be a hardware issue and switching to UBUNTU was a coincidence.  My fan was loose and I needed to clean out my video card.

---

