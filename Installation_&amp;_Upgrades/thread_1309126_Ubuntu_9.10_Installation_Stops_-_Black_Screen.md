---
title: "Ubuntu 9.10 Installation Stops - Black Screen"
date: 2009-11-01
forum: Installation &amp; Upgrades
---

### Post by Ubuntokyo on 2009-11-01
Hi everyone,

I have been looking for a solution to my issue the whole day on forums with no luck.
I wonder if one of you could overcome this.

I am using a Japanese desktop (Fujitsu FMV Theo50x), originally delivered with Vista. My screen is my TV, using HDMI input (max res. 1920x1200).
I could successfully install Ubuntu 8.10 in the past but with a major issue: the installer stops and leaves me with a black screen...
The Problem came from my the ATI Radeon Xpress 1250 video card.
At that time I could solve the issue by applying the following lines in the console (CTRL+ALT+F1) during the install and once on the installed system:

sudo apt-get update
sudo apt-get install xorg-driver-fglrx
sudo depmod -a
cd /etc
mkdir x11
sudo aticonfig --initial
sudo aticonfig -overlay-type=Xv
sudo killall gdm
sudo gdm

If I understand well, I basically installed the ATI proprietary driver that was compatible with the version of XOrg used in 8.10.

Now I have exactly the same&#12288;problem in 9.10, but the same solution does not work. I actually tried several things as suggested in the following links:

[https://help.ubuntu.com/community/BinaryDriverHowto](https://help.ubuntu.com/community/BinaryDriverHowto)

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

After reading several sites, I understand that the ATI proprietary driver is not compatible with Xorg 1.6 used in Ubuntu 9.10. Also it seems that the Open source driver does not install.

I would appreciate any feedback on this issue, in particular on the following points:
 - Is there a way to install Ubuntu 9.10 in text mode or low graphic so that I never face a black screen? I downloaded the alternate CD but am a little lost between all the options.
 - Is there a way to use a standard driver that outputs VGA or anything that I could see to at least finish the install?
 - Is there a way to make the installer go until the end with my video card and the standard install CD?
 - Would a new 9.10 installation swipe away my working 8.10 or would it by default install it next to it in dual boot (I do not know if we are asked to choose a partition, I can't see a thing).

I have seen a lot of posts with similar issues on ATI cards, with no relevant solution as in my case, I cannot install Ubuntu so usually cannot proceed to the steps described.
In advance, thanks for your help.

Ubuntokyo

---

### Post by turboxs on 2009-11-01
I don't know if its of any help, but I have an Nvidia 9600GT card and both the live cd and alternative text install result in a black screen for me.

---

### Post by DustofDust on 2009-11-01
[http://ubuntuforums.org/showpost.php?p=8201026&postcount=23](http://ubuntuforums.org/showpost.php?p=8201026&postcount=23)

at boot press esc and boot with the restricted kernel and do something like in my other post at the link.

---

### Post by pobjones on 2009-11-01
I upgraded from 9.04 to 9.1 and my system was trashed not able to get anything but black screen. Had to format and re-install 9.04.
It's a shame as I like ubuntu and don't get why an upgrade can be worse than previous versions.
It's something to do with nvidia video cards but let's be honest it's hardly as though it's an uncommon card. I hear ATI cards have similar problems.....another common card.
I think ubuntu have released this to early and may finish up shooting themselves in the foot.

---

