---
title: "Need to boot via recovery mode after installing nvidia 750ti card"
date: 2016-12-05
forum: Hardware
---

### Post by james.b on 2016-12-05
I'm running 16.04 on an i5 based system and was doing ok with the on-board video out on my gigabyte motherboard but decided to upgrade to a GTX 750 Ti.

Since doing this I have to go through the following process at each boot:

1. Start the computer, this will either take me to the unencrypt drive screen (which I think I have now disabled) or a black screen. I can't enter text in either case and the resolution is all wrong at the unencrypt prompt.
2. Turn it off by holding down the power button. It then boots to the options screen where I select 'advanced options'
3. Select recovery mode and then select rebuild packages.
4. It runs through the rebuild packages process and then boots normally.

After this everything is seemingly fine, but it's an irritating process to have to go through each morning. 

I read that this is likely a driver issue. In the 'additional drivers' preferences I have tried selecting both  NVIDIA binary driver - version 367.57 from nvidia-367 and version 340.98  from nvidia-340 but get the same results each time.

Should I be looking at installing nvidia drivers manually? or is there a simple fix for this?

thanks!

---

### Post by oldfred on 2016-12-05
You almost always has issues if you try to install more than one nVidia driver. A new driver does not uninstall the old one. So you have to totally purge old driver before installing a new one.

       #What is installed
dpkg -l | grep -i nvidia
dkms status
lsmod | grep nvidia 

While there may be newer drivers, any of the older ones should work. Most of the changes for newer drivers are to support the newer cards.

 Updated driver search by nVidia model, do not download, just check correct driver version
[http://www.geforce.com/drivers](http://www.geforce.com/drivers) 

      
 If you have installed any version, you must purge first, old will conflict with new as new install does not overwrite old version.
sudo apt-get remove --purge nvidia-*
sudo apt-get purge nvidia* bumblebee primus bbswitch-dkms
This may not exist, so if error that would be ok
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup 
   sudo ubuntu-drivers devices
If you just want default version - recommended one
sudo ubuntu-drivers autoinstall
Or you manually choose any in list.
sudo apt-get install nvidia-XXX  

If you have a very new card like the 1050 or any in the 10 series, you can add the ppa, to get the most current driver released by nVidia. Do not download the .run file directly from nVidia.

      
 Ubuntu Launches Its "Fresh" Proprietary Driver PPA - August 2015
[http://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-Fresh-Driver-PPA](http://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-Fresh-Driver-PPA)
Instructions are newest driver for newest cards, must load legacy driver if old nVidia card.
[http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action](http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action)
Details on why and future incorporation to Ubuntu installer
[https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html](https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html)
[https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)
sudo apt-add-repository ppa:graphics-drivers/ppa

---

### Post by james.b on 2016-12-05
That seems to have fixed it, thanks!

---

