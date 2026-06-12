---
title: "Laptop with two GPU Intel and NVidia"
date: 2013-09-30
forum: Hardware
---

### Post by priestnot on 2013-09-30
First of all hello. And thanks in advance for any help you can give me.

I am about to buy a new laptop and I have a few questions because I want to install Ubuntu 64Bit 14.04 on it.

The laptop in question has the following hardware:

Screen: 13.3" 1920 x 1080 Full High-Definition
CPU: 4rd Generation Intel® Core&#8482; i7 4700MQ ( 2.4GHz/3.4GHz, 4 Cores, 8 Threads, 6M Cache) 
RAM: 16GB DDR3 1600MHz Dual-Channel (2x 8GB, Unbuffered, 1.5V, CL11) 
GPU: NVIDIA GTX 765M 2GB GDDR5 (with optimus technology).
Wifi: INTEL N-6235 802.11B/G/N Wireless LAN + Bluetooth&#8482; V4.0 + HS 
3 Hard drives (2 that can be on raid0)
1 HDMI output Port 
1 VGA output Port 
3 USB 3.0 Ports 
1 USB 2.0 Ports 
1 RJ-45 LAN (10/100/1000Mbps) 

The questions that I have are many on drivers and power efficiency using the GPU.

The board has optimus technology does Ubuntu have support to it? Can I turn of the NVidia GPU and use the intel one on the go? I found Bumblebee [https://wiki.debian.org/Bumblebee](https://wiki.debian.org/Bumblebee) but does it work with the GTX 765M?
If not is there a way to make linux use the intel GPU instead of the NVidia?

Does Ubuntu support the wifi board? Is it capable of using the bluetoooth 4.0?
Can I use the drives in raid0?
Can I use both VGA and HDMI outputs to connect to 2 displays at the same time?

Hope some one can answer this questions.
Thank you...

---

### Post by Linuxisfast on 2013-09-30
If you wish to turn off GPU and use the Intel one you need to install Bumblebee, otherwise if you install Ubuntu 12.04.3 it will use the Nvidia and the integrated one would not be used for rendering.

---

### Post by priestnot on 2013-09-30
Thank you for your input.

Ok but did some one tried Bumblebee witha NVIDIA GTX 765M? were can I confir if it does work?

But if bumblebee does not work is there a way to turn off permanently the NVIDIA graphics card?

---

### Post by oldfred on 2013-09-30
Some systems have UEFI/BIOS settings to control video, others are automatic.

       New Intel driver installer (only with 13.04)
[http://www.phoronix.com/scan.php?page=news_item&px=MTQyNTQ](http://www.phoronix.com/scan.php?page=news_item&px=MTQyNTQ)
Intel "Haswell" System 76 Iris Pro Linux Graphics Yield Some Wins Against Windows
[http://www.phoronix.com/scan.php?page=article&item=intel_irispro_linwin&num=1](http://www.phoronix.com/scan.php?page=article&item=intel_irispro_linwin&num=1)
NVIDIA's Linux Driver On Ubuntu Is Very Competitive With Windows 8
[http://www.phoronix.com/scan.php?page=article&item=nvidia_windows8_geforce&num=1](http://www.phoronix.com/scan.php?page=article&item=nvidia_windows8_geforce&num=1)

      
 Newest nVidia Prime with 13.10 testing may run hot, but option to bumblebee
[http://www.webupd8.org/2013/08/using-nvidia-graphics-drivers-with.html](http://www.webupd8.org/2013/08/using-nvidia-graphics-drivers-with.html)
nVidia Optimus and Ubuntu explained 
[http://ubuntuforums.org/showthread.php?t=1657660](http://ubuntuforums.org/showthread.php?t=1657660)

Not too many with new Haswell have posted. A couple.

 Toshiba Satellite P50 model number: P50-A-01E Haswell processor
[http://ubuntuforums.org/showthread.php?t=2163854](http://ubuntuforums.org/showthread.php?t=2163854)
Turned NIC (Integrated Network Interface Controller) off and then booted off of USB. Was NOT an issue with any Linux distro just a quirk of the laptop.
 Am now running 13.10 daily and everything works. Also had to stick with EFI boot ON, Secure Boot disabled. Wouldn't boot off of any media or HDD when mode set to CSM.
Toshiba Satellite P75 intel hd 4600 needed acpi_osi=Linux acpi_backlight=vendor
[http://ubuntuforums.org/showthread.php?t=2161204](http://ubuntuforums.org/showthread.php?t=2161204)

---

### Post by grahammechanical on 2013-09-30
Ubuntu gives us the option to download an ISO image, burn it to disk and then run a live session to test out the OS on the hardware we are using. That is what you need to do. Whether you buy this machine or not is your choice but there is something that you should know about Linux and Nvidia's Optimus technology. The video drivers are at best described as experimental. Nvidia was very slow to develop a driver and it has been equally slow in bringing the driver to completion.

[http://www.webupd8.org/2013/08/using-nvidia-graphics-drivers-with.html](http://www.webupd8.org/2013/08/using-nvidia-graphics-drivers-with.html)

So, the best alternative is an open source driver that is also still very much under development.

[http://www.webupd8.org/2013/04/set-up-bumblebee-with-bumblebee.html](http://www.webupd8.org/2013/04/set-up-bumblebee-with-bumblebee.html)

Then there is the question of the OS that comes pre-installed on this machine. Windows 8? Then it will most certainly be secure boot enabled. That is not the issue as Ubuntu 12.10, 13.04 and 12.04.3 have kernels that comply with the secure boot requirements. You will need to turn Fast Boot off and you will need to understand a little about installing under UEFI/EFI as compared to legacy booting.

Some people do not have problems installing on machines with Windows 8 but many do have problems. Do not expect an easy ride.

Regards.

---

### Post by priestnot on 2013-10-02
thanks for your help...

---

