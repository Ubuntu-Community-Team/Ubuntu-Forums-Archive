---
title: "Ubuntu 12.04 and Nvidia Geforce Gt 520Mx"
date: 2014-07-02
forum: Hardware
---

### Post by ckrles on 2014-07-02
Hi I'm going to install Ubuntu 12.04 Lts on a laptop having:  Intel i7 4Gb Ram nvidia Gefore Gt 520MX  I have a doubt with the graphics card. I've tried the live session and it displays correctly but not at full resolution. I only getr 1324 X 768 ( I can't remember the exact figures). the fact is that I know that there exist Nvidia drivers (this script NVIDIA-Linux-x86-295.59.run) which I haven't intalled yet, because I've read about a problem of overheating because of the combined use of both Intel's graphics card on i7 and Nvidia's card. I read something about Bumblebee driver which I don't know what exactly it does. I also read someting about some "optimus feature" not available in linux in Nvidia's card.    Anyone could recommend me a driver to install and get 3D and all the feature of the graphics card. I would really appreciate if you could tell which driver (file or command line for terminal) to install before messing up with the drivers.  I've also read something about changing some options in the BIOS, but I guess that would affect the dual boot with Windows, so it wouldn't be an option.  Thank you for your help.

---

### Post by oldfred on 2014-07-02
The 295 driver is now older. Best to install the newest in Ubuntu's repository.

Does your system only use nVidia or does it boot with Intel video? Can you set that in UEFI/BIOS or does it only auto-switch?

nomodeset works with nVidia but not usually with Intel and then other options may be required.
 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)

Newer nVidia drivers work better, but usually best not to install the very newest directly from nVidia unless you have to have the newest features to support a very new card/chip. Ubuntu repository is much better at having recent versions.

      
 Bumblebee:
[https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)
[http://www.webupd8.org/2013/04/set-up-bumblebee-with-bumblebee.html](http://www.webupd8.org/2013/04/set-up-bumblebee-with-bumblebee.html)
[http://askubuntu.com/questions/348614/bumblebee-on-ubuntu-13-04-with-geforce-750m-and-driver-319](http://askubuntu.com/questions/348614/bumblebee-on-ubuntu-13-04-with-geforce-750m-and-driver-319)

If a new UEFI based system 14.04 may work a lot better. Many improvements to grub, kernel, and other support software for new systems. Only a few have had issues and 12.04 then may be better.


 Testing NVIDIA Optimus / DRI PRIME On Ubuntu 14.04
[http://www.phoronix.com/scan.php?page=article&item=nvidia_prime_ubuntu1404&num=1](http://www.phoronix.com/scan.php?page=article&item=nvidia_prime_ubuntu1404&num=1)

---

### Post by ckrles on 2014-07-02
The point is that it is not my pc. It's my father's. On my advice he agreed to move away from Windows 7 (after several reinstalls and updates which got me fed up), so I want to make it easy for him and he liked Zorin 6  based on Ubuntu 12.04 Lts (Zorin 9 based on Ubuntu 14.04 Lts is not ready on its final version yet). I tried Zorin 6 live Cd and it works fine I get 1324x 768 resolution and I can play 13Gb mkv files. I guess the i7 GPU works fine. He's not play heavy games or perform highly demanding task, just some web browsing and online video watching. I can use the HDMI to plu to a 40" led TV and it works fine, although if I get the desktop on the two screens at the same time the laptop screen gets resized and the tv screen is fine.   I was asking for a simple way to get 1920 x 1080 resolution and perhaps easily cloning both screen with no resizing on the laptop screen. So I don't mind if the driver for 12.04 is a bit old. I'm not looking for top performance and extreme optimization, I'd simply like it to work. It's an Asus A53S.   I also want to avoid overheating and extra power consumption on the battery, so I thought Bumblebee could be a good replacement for Nvidia Optimus function.  Should I go for Bumblebee?  Thank you.   I forgot to mention it. I don't know what card I'm using to boot. I guess it's Intel's, because in the details section it recognises the CPU but in the GPU section it says unkown.

---

### Post by grahammechanical on 2014-07-02
If the machine has Nvidia Optimus technology then you are better off using the latest Ubuntu with the latest Nvidia driver or the latest version of Bumblebee. Nvidia was very slow to bring out a driver that worked with Optimus. So, the latest is the best but I do not think that it will come close to what the Nvidia Windows drivers do with Nvidia hybrid graphics. Otherwise, you will end up with a system that will be running the Nvidia card, hence the overheating or the on-board (Intel?) adapter and not be able to switch between the two. So, what is the point of having the nvidia card.

Note the time-line in these links and notice that Nvidia development begins long after Ubuntu 12.04 was released. 

[http://www.webupd8.org/2013/04/nvidia-releases-linux-graphics-drivers.html](http://www.webupd8.org/2013/04/nvidia-releases-linux-graphics-drivers.html)


[http://www.webupd8.org/2013/08/using-nvidia-graphics-drivers-with.html](http://www.webupd8.org/2013/08/using-nvidia-graphics-drivers-with.html)

[http://www.webupd8.org/2013/12/more-work-to-support-nvidia-optimus.html](http://www.webupd8.org/2013/12/more-work-to-support-nvidia-optimus.html)

For many months Bumblebee was the best that was on offer to Linux users of machines with Nvidia hybrid technology.

[http://bumblebee-project.org/](http://bumblebee-project.org/)

Regards.

---

### Post by ckrles on 2014-07-02
English is not my native language and I'm not too proficient at it. Right now, I THINK (I don't know how to be sure) the only video tht's working on my system is Intel's. So, what would you recommend me to do?  1. Leave it as it is (just Intel's driver and no Nvidia) 2. Force Nvidia driver and uninstall/deactivate Intel's (I wouldn't know how). 3. Install Bumblebee. I still don't know if it imitates Optimus. But I wouldn't want overheat problems. (I live in very warm place). 4. Any other options  According to what you're telling me, I guess you would select installing Bumblebee, but I'm still unsure about whether it'll cause overheat. Does it cause overheating?  Would you please tell me how to do the option you select?  Thank you.

---

