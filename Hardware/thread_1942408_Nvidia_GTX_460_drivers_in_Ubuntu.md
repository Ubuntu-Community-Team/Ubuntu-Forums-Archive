---
title: "Nvidia GTX 460 drivers in Ubuntu"
date: 2012-03-17
forum: Hardware
---

### Post by alextop30 on 2012-03-17
Well here is a quick story. Until recently I was unable to install ubuntu on my setup because I have 3 different drives designated for different things. I came to the forums and got some great help and was able to successfully complete the installation. After the installation however I encountered a different problem and that the proprietary drivers included in Ubuntu 11.10 are not very fitting for my video card. I have 2 monitors connected to my EVGA Nvidia GeForce GTX 460. I tried downloading the drivers from Nvidia website going into ubuntu, press ctrl alt and f1 to enter shell and log in. After that I used the command 

sudo service lightdm stop

After which I navigate to where the .run package from Nvidia is and run it with the sudo command. The package installs (note this is the 64 bit ) drivers because I have a 64 bit ubuntu as well. Well when I restart my system lightdm service encounteres an error and the graphical interface does not start. The only way I have found to fix it is by reinstalling ubuntu over. 

The major problem is that when fresh ubuntu is installed on my computer the driver for my video card identifies only one of the monitors connected and marks it as unknown.

Can you guys help me out with fixing this and maybe give me detailed steps which I can follow because I am not very savy with code. 



Any help is really appreciated.


Thanks 

Alex

---

### Post by alextop30 on 2012-03-18
No one has any idea how to fix the video with this graphics card?

---

### Post by alextop30 on 2012-03-19
Ok after 10 hours of searching for a resolution I have found one that works very nicely. This is for people that need the help like I did.

if you add the repository using the following code it should update the nvidia drivers to the most current ones and they should work properly.

sudo apt-add-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get install nvidia-current

I found this soulution on [http://www.noobslab.com/2011/09/nvidia-drivers-for-ubuntu-1110-oneiric.html](http://www.noobslab.com/2011/09/nvidia-drivers-for-ubuntu-1110-oneiric.html) just to give credit where credit is due.

---

### Post by devxdev on 2012-03-19
Is it recognizing the display now or does it still say unknown? I had this same issue with a GTS 3xxM the way I did it was waaay longer than that.
But this makes me happy because I'm still using the half-broken one that came with Ubuntu, because like you I had issues and had to re-install :/

---

### Post by alextop30 on 2012-03-19
It helped last night until I noticed that my partitions were not configured correctly so I had to get mbr back on windows and reconfigure grub. When that happened it switched back to proprietery driver and it started sucking again. So if you are not with an extremly weird set up like mine it should run just fine.



12.04 is not any better with these drivers, I can tell you it is still the same problems. It seems that ubuntu is just not up to par yet.

---

### Post by alextop30 on 2012-03-19
Ok I think I have it this time. After the repository and the driver is installed everything must be configured in the nvidia manager. if you open the ubuntu dash and type nvidia the x server settings manager you will be able to modify the x server file so that it will give you signal on both displays. I just did that with 12.04, there however are a bunch of things that seem to be crashing and I don't know if I will be using this distribution for that long, I may end up just going back to 11.10 and doing all of my stuff all over again.

---

