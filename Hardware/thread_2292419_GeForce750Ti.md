---
title: "GeForce750Ti"
date: 2015-08-27
forum: Hardware
---

### Post by Robert_McGeeney on 2015-08-27
Can anyone tell me which proprietary drivers works with the geforce GTX 750ti? I read a ubuntu dev report that it's still being worked on. Any tips welcome.
Currently running using nouveau driver.

Machine Specs:
Gigabyte GA-Z97mx5 Gaming board
Intel i3 3.50Ghz processor
16 GB RAM
GeForce GTX 750Ti Graphics
Ubuntu-Gnome 15.04 Vivid

---

### Post by oldfred on 2015-08-27
Generally best to use a ppa and install the newest driver from nVidia. But do not download directly from nVidia. Several ppas are available, Ubuntu now has one of its own.
If you have installed the incorrect one, you must purge all traces before installing another or you will have major issues.

It is not just video driver, but kernel & support software. Best to use newest version of Ubuntu.

       Ubuntu Launches Its "Fresh" Proprietary Driver PPA
[http://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-Fresh-Driver-PPA](http://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-Fresh-Driver-PPA)
[https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)
Instructions are newest driver for newest cards, must load legacy driver is old nVidia card.
[http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action](http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action)
Details on why and future incorporation to Ubuntu installer
[https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html](https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html)
sudo apt-add-repository ppa:graphics-drivers/ppa.

I think the 750 was the first Maxwell, but they all need latest.

 The GTX 970/980 Maxwell GPUs Light Up With Nouveau On Linux 3.19
[http://www.phoronix.com/scan.php?page=news_item&px=MTg4NTg](http://www.phoronix.com/scan.php?page=news_item&px=MTg4NTg)

 NVIDIA GeForce GTX 970/980: Windows vs. Ubuntu Linux Performance 2015 note versions ppas used to update
[http://www.phoronix.com/scan.php?page=article&item=nvidia_maxwell900_winlin&num=1](http://www.phoronix.com/scan.php?page=article&item=nvidia_maxwell900_winlin&num=1)
Install with Asrock Z97 & nVidia 970
[http://ubuntuforums.org/showthread.php?t=2257406](http://ubuntuforums.org/showthread.php?t=2257406)
[http://ubuntuforums.org/showthread.php?t=2259210](http://ubuntuforums.org/showthread.php?t=2259210)

---

### Post by efflandt on 2015-08-28
I know that when I first installed 14.04.1 in January 2015, nouveau or nvidia-current in 14.04 did NOT support my GTX 750 Ti (even though nvidia-current in 12.04 worked). But **nvidia-331-updates** worked (which is now apparently a 340 version) and I am currently running **nvidia-352** from xorg-edgers ppa (they now also have nvidia-355). I was not aware of ppa:graphics-drivers/ppa. I am still using an older kernel (3.13.0-62-generic), but since I am not using nouveau that is not an issue.

Not sure which nvidia driver versions are in 15.04 repos, but whatever newest version there should certainly work. But I don't know if Software Center would show you different driver versions, so if **Additional Drivers** does not recognize your card and offer nvidia drivers, and you do not know how to use apt-get to do that, I would install **synaptic** from Software Center and use that to find nvidia drivers. But since no graphics drivers worked after I first installed 14.04.1 (even though graphics worked in live/install iso) I had to do that using apt-get from recovery mode, using root console with networking enabled.

---

### Post by SeijiSensei on 2015-08-28
I have that card and am using the nvidia-352 driver from the xorg-edgers PPA.  To add the repository:
```

sudo add-apt-repository ppa:xorg-edgers/ppa
sudo apt-get update

```
Now run the "Additional Drivers" or "Driver Manager" application, and it should install the correct version for you.

---

### Post by Yellow Pasque on 2015-08-28
^I would definitely not recommend using the xorg-edgers PPA if the user just wants the latest nvidia driver. That's like using a hammer to kill a fly...

[https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)
This PPA is a far safer choice, and hopefully, Ubuntu will approve of adding it to the "Additional Drivers" GUI.

---

### Post by MartyBuntu on 2015-08-28
> **Temüjin said:**
> ^I would definitely not recommend using the xorg-edgers PPA if the user just wants the latest nvidia driver. That's like using a hammer to kill a fly...



I somewhat agree. The edgers PPA get's thrown out quite a bit as a "cure-all".

---

