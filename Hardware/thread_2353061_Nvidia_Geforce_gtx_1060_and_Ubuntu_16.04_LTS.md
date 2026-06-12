---
title: "Nvidia Geforce gtx 1060 and Ubuntu 16.04 LTS"
date: 2017-02-18
forum: Hardware
---

### Post by agielchinsky on 2017-02-18
Hello, I recently installed Ubuntu, and then tried to install a Nvidia Geforce gtx 1060 6GB GPU. I've tried a few methods for installing the drivers that I found online, but none worked. Each time I would get stuck in a login loop which required Ctrl+alt+ F1 and sudo apt-get purge nvidia* to fix. What is the proper/correct way to install this card? 

This machine was originally Win10 only, then semi working dual boot, then working Ubuntu only. I was previously using the onboard card. I'm hoping to train neural networks with this card.

Thanks for your help!

---

### Post by agielchinsky on 2017-02-18
I restarted and went into went into bios to turn off secure bootup (i wasn't able to do it through mokutil). When I turned the computer back on the resolution was back to normal, and I was able to install the driver through Software and Updates/ Additional Drivers using PPA.

Is is safe/normal to leave secure bootup turned off?

Thanks

---

### Post by oldfred on 2017-02-18
Do do need to purge to fully uninstall any other versisons.
And then use ppa to install newest nVidia driver.

 Ubuntu 16.04 LTS installation problem with GA-Z170X-UD5 TH & GTX 1080
Go to the BIOS, Peripherals > "Initial Display Output": set it to IGFX (basically, this tells your computer to use your motherboard to display graphics)
[http://ubuntuforums.org/showthread.php?t=2327648](http://ubuntuforums.org/showthread.php?t=2327648) 

      
 #To see available versions:
dpkg -l | grep -i nvidia*
#see details for version installed
sudo apt-cache policy nvidia*
dkms status 

 
sudo apt-get purge nvidia*
# this may not exist
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup 

 Details on why and future incorporation to Ubuntu installer
[https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html](https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html)
[https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)
sudo apt-add-repository ppa:graphics-drivers/ppa 
   # should show newest versions available in addition
ubuntu-drivers devices 

Then install newest in list of versions.

---

### Post by jeff666 on 2017-02-18
nivida has their own driver which works great you might want to try (i havn't tried with ubuntu just debain but should be the same) 
1.download from the website [http://us.download.nvidia.com/XFree86/Linux-x86_64/375.39/NVIDIA-Linux-x86_64-375.39.run](http://us.download.nvidia.com/XFree86/Linux-x86_64/375.39/NVIDIA-Linux-x86_64-375.39.run)
2.shut off display services
3.run installation script
4.restart display services
5.enjoy
 it could be the same driver just different installation (i'm not going to check, just posting this becuase it work flawless for me). 

"Note that many Linux distributions provide their own packages of the  NVIDIA Linux Graphics Driver in the distribution's native package  management format. This may interact better with the rest of your  distribution's framework, and you may want to use this rather than  NVIDIA's official package.
Also note that SuSE users should read the SuSE NVIDIA Installer   [ HOWTO]("http://users.suse.com/%7Esndirsch/nvidia-installer-HOWTO.html") before downloading the driver.
Installation instructions: Once you have downloaded the driver, change  to the directory containing the driver package and install the driver  by running, as root, sh ./NVIDIA-Linux-x86_64-375.39.run
One of  the last installation steps will offer to update your X configuration  file. Either accept that offer, edit your X configuration file manually  so that the NVIDIA X driver will be used, or run nvidia-xconfig
Note that the list of supported GPU products is provided to indicate  which GPUs are supported by a particular driver version. Some designs  incorporating supported GPUs may not be compatible with the NVIDIA Linux  driver: in particular, notebook and all-in-one desktop designs with  switchable (hybrid) or Optimus graphics will not work if means to  disable the integrated graphics in hardware are not available. Hardware  designs will vary from manufacturer to manufacturer, so please consult  with a system's manufacturer to determine whether that particular system  is compatible.
See the [README]("http://us.download.nvidia.com/XFree86/Linux-x86_64/375.39/README/index.html") for more detailed instructions.
For further information please visit our forum, [https://devtalk.nvidia.com/default/board/98/linux/](https://devtalk.nvidia.com/default/board/98/linux/) .                                                   " -- nivida.com

secure boot should be on to the best of my limited knowledge without it any app can write to any memory (which makes sense why it would need to be off for certain drivers gtx 1060 has some settings onboard (at least my model)) check and see if your bios has a legacy/efi mode (mine boots efi first so be aware of that for dual boot) you can  reinstall as csm only.

nerual network training --dam you must be smart, good luck with your project.

---

