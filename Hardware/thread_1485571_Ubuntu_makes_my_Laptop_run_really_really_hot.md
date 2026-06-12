---
title: "Ubuntu makes my Laptop run really really hot"
date: 2010-05-17
forum: Hardware
---

### Post by callide777 on 2010-05-17
Hey Guys.

So I really want to tackle this issue with my Laptop running super hot under Ubuntu. Under Windows Vista, my laptop never gets hot. Despite that, Ubuntu is still better than Windows. My visual effects are set to "none" and I did not install nvidias proprietary video driver. This is a fresh install.

All the forums I've read related to this problem claim that it's an issue with the video card driver. I would really like some help in understanding what the problem could be and what steps I need to take to fix it. I would be willing to figure out how to write and configure a video driver if that's what I had to do. 

[_[IMG]http://chrisbaldelomar.com/ubuntu/ScreenshotSmall.png[/IMG]_]("http://chrisbaldelomar.com/ubuntu/Screenshot.png")




-Computer-
Processor        : 2x AMD Turion Dual-Core RM-75
Memory        : 2836MB (595MB used)
Operating System        : Ubuntu 10.04 LTS


-PCI Devices-
RAM memory        : nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a2)
ISA bridge        : nVidia Corporation Device 075e (rev a2)
SMBus        : nVidia Corporation MCP78S [GeForce 8200] SMBus (rev a1)
Co-processor        : nVidia Corporation MCP78S [GeForce 8200] Co-Processor (rev a2)
RAM memory        : nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a1)
USB Controller        : nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1) (prog-if 10)
USB Controller        : nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1) (prog-if 20)
USB Controller        : nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1) (prog-if 10)
USB Controller        : nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1) (prog-if 20)
IDE interface        : nVidia Corporation MCP78S [GeForce 8200] IDE (rev a1) (prog-if 8a [Master SecP PriP])
Audio device        : nVidia Corporation MCP72XE/MCP72P/MCP78U/MCP78S High Definition Audio (rev a1)
PCI bridge        : nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1) (prog-if 01)
IDE interface        : nVidia Corporation MCP78S [GeForce 8200] SATA Controller (non-AHCI mode) (rev a2) (prog-if 85 [Master SecO PriO])
Ethernet controller        : nVidia Corporation MCP77 Ethernet (rev a2)
PCI bridge        : nVidia Corporation MCP78S [GeForce 8200] PCI Express Bridge (rev a1)
PCI bridge        : nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
Host bridge        : Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] HyperTransport Configuration (rev 40)
Host bridge        : Advanced Micro Devices [AMD] Family 11h [Turion X2, Athlon X2, Sempron] Address Map
Host bridge        : Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] DRAM Controller
Host bridge        : Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] Miscellaneous Control
Host bridge        : Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] Link Control
VGA compatible controller        : nVidia Corporation C77 [GeForce 8200M G] (rev a2)
Ethernet controller        : Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)

---

### Post by soltanis on 2010-05-17
What happens if you install the nVidia binary drivers? If it's really the graphics card drivers, then the ones from nVidia themselves should operate the card at a cooler frequency. I do know nVidia has this "power mizer" thing which is basically GPU throttling, and it's quite possible the open source drivers (which IMHO suck) don't support that.

---

### Post by callide777 on 2010-05-17
Yeah, in all my previous installation of ubuntu, I installed the nvidia's video drivers. I had thought that the drivers themselves may have been the problem. But, I still seem to get the same result. In addition, nvidia's drivers for linux is a little buggy and it's always a challenge trying to set up 2 monitors to twinview.

Are you saying that nvidia's driver has a GPU throttle setting? What is that exactly? 

How could I look at the default video drivers for ubuntu? I know that would be an ambitious undertaking. I am interested though.

---

### Post by AlexZaim on 2010-05-17
```
sudo apt-get install lm-sensors


sudo sensors-detect

To load the manual modules, type

sudo /etc/init.d/module-init-tools start

Load the modules into kernel with

sudo sensors -s

And check the output

sudo sensors

How to control fan speed (lm-sensors)

Install and config lm-sensors first, see section above. Then run pwmconfig to test your fans.

sudo pwmconfig
```
pwmconfig is where you will set a new critical temperature ( you want to lower it) so that the cooler spins faster when it rises above.

you might as well want to read the man pages... ```
man pwmconfig
```

---

### Post by callide777 on 2010-05-17
Ok, i'll do that when I get home. I'll consider that a temporary fix though.

I still think there is a bug somewhere. And I want to fix it the right way. In windows, my fan hardly ever has to come on and the temp is still relatively low. Ubuntu shouldn't have to use the fan more so than windows. Any ideas?

---

### Post by Mike BFD on 2010-05-17
Gentlemen,

I noticed the same problem (laptop overheat) with Intel 965 Express video chip. Does anybody have any suggestion?

Also, to make sure my fans are not clogged I'd like to open the back cover... But have no idea how to do it with Presario A900 laptop! It has plenty of screws on the backside - but no visible cover... What are those screws holding?))

---

### Post by callide777 on 2010-05-17
it's probably not the fan. if you were running windows, this wouldn't be an issue. It has to be some bug with the dirver, or something else. Any ideas?

---

### Post by Mike BFD on 2010-05-20
Update:

I found this 
[http://ubuntuforums.org/showthread.php?t=1456703](http://ubuntuforums.org/showthread.php?t=1456703)
pretty useful, please read that it may help to cool down our laptops))

Workarounds offered there helped me a bit (my Compaq is still hotter than I'd like it to be but it doesn't shutdown on overheating anymore)

---

