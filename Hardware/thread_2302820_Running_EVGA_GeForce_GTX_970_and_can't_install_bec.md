---
title: "Running EVGA GeForce GTX 970 and can't install because of no DVI output"
date: 2015-11-13
forum: Hardware
---

### Post by Duty_Herrmann on 2015-11-13
So, I am trying to install Ubuntu 15.10 as a standalone OS on my new comp with a dual boot set-up. I have installed and used it on my laptop in the past with no installation troubles. I also have no troubles running Ubuntu on my new comp within a VM. My graphics card is a GeForce 970 that only has HD outputs. I have two DVI connections and an HDMI connection. I have tried using a dvi to vga adapter to no avail. What happens is that when I boot from thumbdrive with my Ubuntu Iso image, the install screen comes up in greyscale for a few seconds before cutting out completely. 

Does anyone have any solutions as to how I can set Ubuntu to HD output even though I haven't yet been able to install (I don't think that's likely but maybe)? I have also thought that maybe I could install via VM but I have not been able to find any literature on how to install a standalone via VM (also wouldn't be surprised if that weren't possible)? 

If anyone has a solution or can provide some helpful literature, I would be quite thankful.

---

### Post by blm-ubunet on 2015-11-13
There's nothing special output HD outputs. The HDMI port is electrically equivalent to single link DVI with a non-locking connector & consumer price tag.

Your DVI ports may (DVI-I) or not (DVI-D) contain any VGA output.

AFAIK nVidia has not released the signed firmware for any of the 900 family.
When you first boot ubuntu (no proprietary driver) nouveau will try to load as best match but there is no firmware!
Why this does not just fail & fallback to vesa driver I do not know..

The work-around is to stop any KMS driver at boot & get VESA driver (max res. 1280x1024) loaded & then you install nvidia driver from ppa.

The **temporary** grub boot option is "nomodeset". This causes vesa fallback driver to load.

Your GPU /hw only needs nvidia-343 or later.
This is already in std distro repositories or you could add the graphics driver ppa
[https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)
and go all out..

---

### Post by Duty_Herrmann on 2015-11-13
Thank you.

How do I stop the KMS driver at boot? I've used Ubuntu before but haven't gotten too deep into the guts of it yet.

---

### Post by blm-ubunet on 2015-11-13
> The temporary grub boot option is "nomodeset". This causes vesa fallback driver to load.
You can do this by editing a setup file & updating grub or by interrupting boot & inserting that piece of text.

Getting too deep into the guts of it is fine if you have time & no pressing need for functioning PC..

---

### Post by oldfred on 2015-11-14
Some others with 970/980 cards.

 Asus z97-A with nVidia GTX 970 Ubuntu  15.04
[http://askubuntu.com/questions/615896/ubuntu-15-04-uefi-cannot-install-blank-screen-no-signal?noredirect=1#615896](http://askubuntu.com/questions/615896/ubuntu-15-04-uefi-cannot-install-blank-screen-no-signal?noredirect=1#615896)
      
 NVIDIA GeForce GTX 970/980: Windows vs. Ubuntu Linux Performance 2015 note versions ppas used to update
[http://www.phoronix.com/scan.php?page=article&item=nvidia_maxwell900_winlin&num=1](http://www.phoronix.com/scan.php?page=article&item=nvidia_maxwell900_winlin&num=1)
Install with Asrock Z97 & nVidia 970
[http://ubuntuforums.org/showthread.php?t=2257406](http://ubuntuforums.org/showthread.php?t=2257406)
[http://ubuntuforums.org/showthread.php?t=2259210](http://ubuntuforums.org/showthread.php?t=2259210)

The GTX 970/980 Maxwell GPUs Light Up With Nouveau On Linux 3.19
[http://www.phoronix.com/scan.php?page=news_item&px=MTg4NTg](http://www.phoronix.com/scan.php?page=news_item&px=MTg4NTg)

 Nouveau limited support for GTX 970/980 in kernel 3.19
[http://www.phoronix.com/scan.php?page=news_item&px=MTg1MjU](http://www.phoronix.com/scan.php?page=news_item&px=MTg1MjU)


I think the link above where it says Nouveau works, was changed.

>  The GeForce GTX 970/980 new Maxwell GPUs also couldn't be tested since there isn't any hardware acceleration support with Nouveau and that's currently blocked by NVIDIA providing their new signed firmware images. Or only nVidia will work.


You may need newest kernel and newest nVidia driver from ppa. Best to be using newest version of Ubuntu to have newer standard kernels & drivers.


 PPA for nVidia mamarley pps - depreciated Use this:
[https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)

 Ubuntu Launches Its "Fresh" Proprietary Driver PPA
[http://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-Fresh-Driver-PPA](http://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-Fresh-Driver-PPA)
[https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)
Instructions are newest driver for newest cards, must load legacy driver if old nVidia card.
[http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action](http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action)
Details on why and future incorporation to Ubuntu installer
[https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html](https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html)
sudo apt-add-repository ppa:graphics-drivers/ppa

---

### Post by Duty_Herrmann on 2015-11-20
Thanks for all the help on this. I've managed to sort out my problem.

---

### Post by Duty_Herrmann on 2015-11-20
How do I set this to solved?

---

### Post by QIII on 2015-11-20
Just above your first post, click "Thread tools".  In the dropdown, select "Mark this thread solved"

---

### Post by tinol on 2016-03-04
how did you finally resolve this? I've followed the thread but still having problem. I have an EVGA GTX 970 using Ubuntu 14.04. I have a newer version pf nvidia driver  ( I have 352.79) but when I install the new EVGA gtx 970 I get just a blank screen, basically no dvi to vga output. I switched back to teh old card in order to do more digging around and so far nothing seems to work when I switch to the gtx 970. Any help would be welcomed

---

### Post by Bucky Ball on 2016-03-04
> **Duty_Herrmann said:**
> Thanks for all the help on this. I've managed to sort out my problem.

Common courtesy here to share with the community and those who've been helping you what you did to sort out your issue. Please do. Thanks. :)

PS: I also have a 970 on a brand new rig and running monitors HDMI and DVI and no issues whatsoever. You DO NOT need a PPA for the driver. The recommended one in the 'Additional Drivers' works just fine. (352 from memory). 

This card works beautifully in 15.10. I am using it for video editing and it uses CUDA (you'll need the toolkit, but more of that later) and whizzes along. :)

Good luck.

---

