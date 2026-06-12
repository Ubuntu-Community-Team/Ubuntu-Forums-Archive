---
title: "Nvidia Quadro K620 installation: blinking cursor"
date: 2019-04-04
forum: Hardware
---

### Post by the-chemist19 on 2019-04-04
Dear all,

I am trying to update the graphics driver for a HP desktop with a K620 graphics card. Previously, I have used the Nvidia run files (directly from Nvidia homepage) to install the driver.

However, now I have issues (probably after a ubuntu update?): PC boots up and shows a flashing screen with /dev/sda, followed by blinking cursor. I am aware that the /dev message is normal. However, the booting process just stops here.

Here is what I have done so far:

I was using Ubuntu 16.04 LTS. After trying a few suggestions found on several posts, I upgraded to 18.04 LTS via do-release-upgrade. Now I get a log-in window but with low resolution. Looking into Software -> Additional drivers shows me that the nouveau drivers were used. 

I have tried several ways to install the Nvidia driver:

- via GUI, by selecting a prop driver [https://www.linuxbabe.com/ubuntu/install-nvidia-driver-ubuntu-18-04](https://www.linuxbabe.com/ubuntu/install-nvidia-driver-ubuntu-18-04)
- via command line ubuntu-drivers devices, as described here [https://linuxconfig.org/how-to-install-the-nvidia-drivers-on-ubuntu-18-04-bionic-beaver-linux](https://linuxconfig.org/how-to-install-the-nvidia-drivers-on-ubuntu-18-04-bionic-beaver-linux)
- via command line by adding the ppa as described here later: [https://linuxconfig.org/how-to-install-the-nvidia-drivers-on-ubuntu-18-04-bionic-beaver-linux](https://linuxconfig.org/how-to-install-the-nvidia-drivers-on-ubuntu-18-04-bionic-beaver-linux) or here [https://ttdtrang.tk/2017/12/ubuntu-16-04-frozen-graphical-interface/](https://ttdtrang.tk/2017/12/ubuntu-16-04-frozen-graphical-interface/)
- via run file, following all instructions described here (also blacklisting noveau driver) [https://gist.github.com/wangruohui/df039f0dc434d6486f5d4d098aa52d07](https://gist.github.com/wangruohui/df039f0dc434d6486f5d4d098aa52d07)

Before installing a driver, I purge with apt-get purge nvidia-*
After installation of a driver, I check with nvidia-smi that it is there.

I have tried several driver versions (both open and prop), so far no success

Secure boot is switched off, as described here: [https://www.pugetsystems.com/labs/hpc/The-Best-Way-To-Install-Ubuntu-16-04-with-NVIDIA-Drivers-and-CUDA-1097/](https://www.pugetsystems.com/labs/hpc/The-Best-Way-To-Install-Ubuntu-16-04-with-NVIDIA-Drivers-and-CUDA-1097/)

Once the blinking cursor appears, I am no longer able to use alt-ctrl-f1 to change to command line.
I use ssh to remotely connect and kill the X server with "sudo telinit 3"

Interestingly, when I reboot with a USB bootable stick to test ubuntu, I get a nice looking screen with high resolution. Its the nouveau driver, but of course I cannot change the driver here

Please, do not close this thread. I am aware that there are many posts on this. 

However, I must be missing something - please comment if you know another suggestion to tackle this!

Thanks a lot! 

The_chemist19

---

