---
title: "nForce 610i chipset not supported"
date: 2008-02-10
forum: Hardware &amp; Laptops
---

### Post by tianran.chen on 2008-02-10
Greetings,

I just bought MSI P6NGM(L) motherboard, which uses nForce 610i chipset (with GeForce 7050 integrated), but now the onboard video and audio are not working. When I do "lspci" I get a whole list of "Unknown device"s. NVidia has no linux driver for nForce 610i or GeForce 7050 neither. So now I don't know what to do. Any information on this will be appreciated.

(I guess I should have studied more about this before I buy, but... oh well)

---

### Post by Fechter on 2008-02-10
It will be a little bit sticky, but let's give it a try.

Audio  	

    * Intel High Definition Audio (Azalia)
    * Realtek ALC888 HD Audio CODEC
So the 610 chipset gives you very good capabilities. You will need to install the Realtek drivers from their site/ they have the alc888 hd driver for linux/unix/.
I am not sure if you will make the video work properly.. try from add/remove Nvida "new" driver.

---

### Post by Sam_Lowry on 2008-02-28
Damn, I just built a Linux system with a nForce 610i chipset, and I think I am having the same problem. Install stops half-way through. Boned.

---

### Post by Sam_Lowry on 2008-02-28
UPDATE: I just switched monitors and Linux loaded right up! I was using a very old CGA monitor (ask your grandpa what that is). 

----------------------------------------------------------------
Linux CD:
Ubuntu 7.10 "Gutsy Gibbon" 
(CD from PCTech101, not downloaded)

Motherboard: 
GIGABYTE GA-73VM-S2
Onboard Graphics Integrated in the nVIDIA® GeForce 7050 / nForce 610i chipset
Audio Realtek ALC662 codec 

CPU: 
Intel Pentium E2160 Dual-Core Processor Allendale 1.8GHz 1MB L2 Cache LGA 775 65W

1GB RAM
4 GB of disk space

---

### Post by Yellow Pasque on 2008-02-28
First, try this command to update your lspci list:
```
sudo update-pciids
```

Envy should allow you to install the nvidia driver version off their web site, which should support the video.

As for audio, try this script to upgrade to the latest version of ALSA:
[http://ubuntuforums.org/showpost.php?p=4298894&postcount=24](http://ubuntuforums.org/showpost.php?p=4298894&postcount=24)

If that doesn't work, use OSS4, which I know supports the latest nvidia mcp audio.

---

### Post by djopino on 2008-03-01
> **Sam_Lowry said:**
> UPDATE: I just switched monitors and Linux loaded right up! I was using a very old CGA monitor (ask your grandpa what that is). 

----------------------------------------------------------------
Linux CD:
Ubuntu 7.10 "Gutsy Gibbon" 
(CD from PCTech101, not downloaded)

Motherboard: 
GIGABYTE GA-73VM-S2
Onboard Graphics Integrated in the nVIDIA® GeForce 7050 / nForce 610i chipset
Audio Realtek ALC662 codec 

CPU: 
Intel Pentium E2160 Dual-Core Processor Allendale 1.8GHz 1MB L2 Cache LGA 775 65W

1GB RAM
4 GB of disk space
I got the same motherboard, GA-73VM-S2 but the nforce 610i chipset does not work with the downloaded cd of ubuntu 7.10 AMD64. I want to know if you did anything to make onboard sound and graphics work for GA-73VM-S2.

I have Pentium dual core E2180 with GA-73VM-S2.

---

### Post by djopino on 2008-03-01
**This post could be related to an Ubuntu bug filed at**: [https://answers.launchpad.net/ubuntu/+question/22924](https://answers.launchpad.net/ubuntu/+question/22924) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Ok, my previous post was not really precise so here's some info

My hardware :

Motherboard : GA-73VM-S2, integrated GeForce 7050/ nForce 610i chipset
onboard graphic : GeForce 7050
onboard audio : Realtek ALC662 codec, High Definition Audio
onboard ethernet : RTL 8201N chip (10/100 Mbit)
for the specs page : [http://www.gigabyte.com.tw/Products/Motherboard/Products_Spec.aspx?ClassValue=Motherboard&ProductID=2714&ProductName=GA-73VM-S2](http://www.gigabyte.com.tw/Products/Motherboard/Products_Spec.aspx?ClassValue=Motherboard&ProductID=2714&ProductName=GA-73VM-S2)

Processor : Pentium Dual Core E2180 @ 2.0 gHz

Hard Drive : Western Digital SATA2 500gb


What works :

First, with the fresh install of download ubuntu 7.10, the audio did not work. I made all the updates of ubuntu, I did the code proposed by Temüjin :
```
sudo update-pciids
```
I also ran the scripts proposed by Temüjin:
[http://ubuntuforums.org/showpost.php?p=4298894&postcount=24](http://ubuntuforums.org/showpost.php?p=4298894&postcount=24)
I'm not sure what of these did fix my audio but know it works!

The graphic works only with vesa driver. Ubuntu detects that a nVidia chip is inside but when I enable the proprietary driver the display manager will not work properly. It's says that the display manager will work with reduced resolution. With the vesa driver, I cannot use my native 1440x900 resolution. When I select this resolution, it's like if gdm stays in 1024x768 cause my monitor info says so and a lot of pixel are off screen. I will try to search for this issue and give you news.

I checked on the nVidia site and the nForce 610i chipset is not supported for linux, 32bits and 64bits neither. I will write nVidia to know when they expect to release and linux driver for nForce 610i chipset.

The network did work with fresh install without any updates.

I tried to install ubuntu 8.04 alpha 5 but the installer crashes when installing the bootloader. I could boot anyway by editing menu.lst of grub that was already installed by ubuntu 7.10. The network does not work on 8.04, neither the audio.

I will try to install the latest graphic driver from nVidia site. If you go to [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html) , it says that nForce drivers are supposed to be supported with open source drivers included in the linux kernel... but I think it's only for nForce-1 to nForce-4.

Ok I just searched and if you go to this site : [http://pci-ids.ucw.cz/iii/?i=10de](http://pci-ids.ucw.cz/iii/?i=10de) , and search on the page for nForce 610i, you will see that the pciids of nForce 610i have not been accepted. We can hope this will come soon...

Here's the output of lspci :
00:00.0 Host bridge: nVidia Corporation Unknown device 07c3 (rev a2)
00:00.1 RAM memory: nVidia Corporation Unknown device 07cb (rev a2)
00:01.0 RAM memory: nVidia Corporation Unknown device 07cd (rev a1)
00:01.1 RAM memory: nVidia Corporation Unknown device 07ce (rev a1)
00:01.2 RAM memory: nVidia Corporation Unknown device 07cf (rev a1)
00:01.3 RAM memory: nVidia Corporation Unknown device 07d0 (rev a1)
00:01.4 RAM memory: nVidia Corporation Unknown device 07d1 (rev a1)
00:01.5 RAM memory: nVidia Corporation Unknown device 07d2 (rev a1)
00:01.6 RAM memory: nVidia Corporation Unknown device 07d3 (rev a1)
00:02.0 RAM memory: nVidia Corporation Unknown device 07d6 (rev a1)
00:03.0 ISA bridge: nVidia Corporation Unknown device 07d7 (rev a2)
00:03.1 SMBus: nVidia Corporation Unknown device 07d8 (rev a1)
00:03.2 RAM memory: nVidia Corporation Unknown device 07d9 (rev a1)
00:03.4 RAM memory: nVidia Corporation Unknown device 07c8 (rev a1)
00:04.0 USB Controller: nVidia Corporation Unknown device 07fe (rev a1)
00:04.1 USB Controller: nVidia Corporation Unknown device 056a (rev a1)
00:08.0 IDE interface: nVidia Corporation Unknown device 056c (rev a1)
00:09.0 Audio device: nVidia Corporation Unknown device 07fc (rev a1)
00:0a.0 PCI bridge: nVidia Corporation Unknown device 056d (rev a1)
00:0b.0 PCI bridge: nVidia Corporation Unknown device 056e (rev a1)
00:0c.0 PCI bridge: nVidia Corporation Unknown device 056f (rev a1)
00:0d.0 PCI bridge: nVidia Corporation Unknown device 056f (rev a1)
00:0e.0 IDE interface: nVidia Corporation Unknown device 07f0 (rev a2)
00:0f.0 Ethernet controller: nVidia Corporation Unknown device 07dc (rev a2)
00:10.0 VGA compatible controller: nVidia Corporation Unknown device 07e3 (rev a2)

Hope this will help!

Djo

---

### Post by djopino on 2008-03-01
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/195139](https://bugs.launchpad.net/ubuntu/+bug/195139) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
Euréka!

Here's and HOW-TO make work audio, video proprietary drivers for the motherboard GA-73VM-S2 that has nforce 610i chipet with GeForce 7050 graphic card. Maybe this will work for other motherboards that has nforce 610i.

**AUDIO**

First, with the fresh install of download ubuntu 7.10, the audio did not work. I made all the updates of ubuntu over internet and after I did the code proposed by Temüjin :
```
sudo update-pciids
```

I also ran the scripts proposed by Temüjin:
[http://ubuntuforums.org/showpost.php?p=4298894&postcount=24](http://ubuntuforums.org/showpost.php?p=4298894&postcount=24)
I'm not sure what of these did fix my audio but know it works!

**GRAPHICS**

After that, I had a problem to set the native resolution. I have a wide screen monitor that runs with 1440x900 but with the vesa graphic driver, when I tried to set to 1440x900, it did not work. When I tried to install the restricted driver with the graphical utility in System/Administration/Restricted Drivers Manager the display manager did not work. So here's how to make nVidia drivers work :

First uninstall the nVidia drivers provided by the Restricted Drivers Manager.

After go to [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html). Select Linux IA32 latest version if you have 32bits distribution or AMD64 if you have ubuntu AMD64. Download and save it on your desktop.

Go where you saved the file and right click on it, select propreties. Go into permissions and mark the box "Allow executing file as a program".

Now you have to close your display manager. Close all you programs, log out and press ctrl+alt+F1. You will enter in a console that is not on the display manager. Log with your normal user and password. 

First close your display manager. Type :
```
killall gdm
```
replace gdm by kdm for KDE display manager.

Go to the directory where you saved the nVidia driver for linux. Type :
```
cd Desktop
```
and then
```
sudo sh NVIDIA-Linux-x86_64-169.12-pkg2.run
```
verify the version that is written. If the version is different, change it on the command above. To see the files you have in the directory you are, type "dir".

Now follow the step by step installer. At the end it is asked if you want to configure your xorg.conf. Say yes, this will select the nvidia driver. Now nVidia driver is installed!

When you return to the console type:
```
sudo gdm
```

You should see the nVidia logo before the login screen.

Enjoy!


NOTE: the new nVidia drivers from their web site were uploaded by nVidia on the February 26, 2008.

---

### Post by Sam_Lowry on 2008-03-07
Thank you, djopino. I am about to tackle this and I think you saved my a lot of hair pulling. Thanks man!

---

### Post by ceefour on 2008-03-22
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/nvidia-kernel-common/+bug/195139](https://bugs.launchpad.net/ubuntu/+source/nvidia-kernel-common/+bug/195139) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				> **djopino said:**
> **This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/195139](https://bugs.launchpad.net/ubuntu/+bug/195139) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
Euréka!

Here's and HOW-TO make work audio, video proprietary drivers for the motherboard GA-73VM-S2 that has nforce 610i chipet with GeForce 7050 graphic card. Maybe this will work for other motherboards that has nforce 610i.


Thank you so much, djopino. Yes, confirmed to work with Zotac N73V-AC7V:

[https://bugs.launchpad.net/ubuntu/+source/nvidia-kernel-common/+bug/195139](https://bugs.launchpad.net/ubuntu/+source/nvidia-kernel-common/+bug/195139)

---

### Post by Dileeshvar on 2008-07-23
> **djopino said:**
> **This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/195139](https://bugs.launchpad.net/ubuntu/+bug/195139) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
Euréka!

Here's and HOW-TO make work audio, video proprietary drivers for the motherboard GA-73VM-S2 that has nforce 610i chipet with GeForce 7050 graphic card. Maybe this will work for other motherboards that has nforce 610i.

**AUDIO**

First, with the fresh install of download ubuntu 7.10, the audio did not work. I made all the updates of ubuntu over internet and after I did the code proposed by Temüjin :
```
sudo update-pciids
```

I also ran the scripts proposed by Temüjin:
[http://ubuntuforums.org/showpost.php?p=4298894&postcount=24](http://ubuntuforums.org/showpost.php?p=4298894&postcount=24)
I'm not sure what of these did fix my audio but know it works!

**GRAPHICS**

After that, I had a problem to set the native resolution. I have a wide screen monitor that runs with 1440x900 but with the vesa graphic driver, when I tried to set to 1440x900, it did not work. When I tried to install the restricted driver with the graphical utility in System/Administration/Restricted Drivers Manager the display manager did not work. So here's how to make nVidia drivers work :

First uninstall the nVidia drivers provided by the Restricted Drivers Manager.

After go to [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html). Select Linux IA32 latest version if you have 32bits distribution or AMD64 if you have ubuntu AMD64. Download and save it on your desktop.

Go where you saved the file and right click on it, select propreties. Go into permissions and mark the box "Allow executing file as a program".

Now you have to close your display manager. Close all you programs, log out and press ctrl+alt+F1. You will enter in a console that is not on the display manager. Log with your normal user and password. 

First close your display manager. Type :
```
killall gdm
```
replace gdm by kdm for KDE display manager.

Go to the directory where you saved the nVidia driver for linux. Type :
```
cd Desktop
```
and then
```
sudo sh NVIDIA-Linux-x86_64-169.12-pkg2.run
```
verify the version that is written. If the version is different, change it on the command above. To see the files you have in the directory you are, type "dir".

Now follow the step by step installer. At the end it is asked if you want to configure your xorg.conf. Say yes, this will select the nvidia driver. Now nVidia driver is installed!

When you return to the console type:
```
sudo gdm
```

You should see the nVidia logo before the login screen.

Enjoy!


NOTE: the new nVidia drivers from their web site were uploaded by nVidia on the February 26, 2008.

Hey thanks but the installer is showing that libc for the driver is not installed I did try this command but it din work out !!
```
 apt-get install build-essential

```
what shall I do some one help me !!!

---

### Post by Dileeshvar on 2008-07-23
> **djopino said:**
> **This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/195139](https://bugs.launchpad.net/ubuntu/+bug/195139) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
Euréka!

Here's and HOW-TO make work audio, video proprietary drivers for the motherboard GA-73VM-S2 that has nforce 610i chipet with GeForce 7050 graphic card. Maybe this will work for other motherboards that has nforce 610i.

**AUDIO**

First, with the fresh install of download ubuntu 7.10, the audio did not work. I made all the updates of ubuntu over internet and after I did the code proposed by Temüjin :
```
sudo update-pciids
```

I also ran the scripts proposed by Temüjin:
[http://ubuntuforums.org/showpost.php?p=4298894&postcount=24](http://ubuntuforums.org/showpost.php?p=4298894&postcount=24)
I'm not sure what of these did fix my audio but know it works!

**GRAPHICS**

After that, I had a problem to set the native resolution. I have a wide screen monitor that runs with 1440x900 but with the vesa graphic driver, when I tried to set to 1440x900, it did not work. When I tried to install the restricted driver with the graphical utility in System/Administration/Restricted Drivers Manager the display manager did not work. So here's how to make nVidia drivers work :

First uninstall the nVidia drivers provided by the Restricted Drivers Manager.

After go to [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html). Select Linux IA32 latest version if you have 32bits distribution or AMD64 if you have ubuntu AMD64. Download and save it on your desktop.

Go where you saved the file and right click on it, select propreties. Go into permissions and mark the box "Allow executing file as a program".

Now you have to close your display manager. Close all you programs, log out and press ctrl+alt+F1. You will enter in a console that is not on the display manager. Log with your normal user and password. 

First close your display manager. Type :
```
killall gdm
```
replace gdm by kdm for KDE display manager.

Go to the directory where you saved the nVidia driver for linux. Type :
```
cd Desktop
```
and then
```
sudo sh NVIDIA-Linux-x86_64-169.12-pkg2.run
```
verify the version that is written. If the version is different, change it on the command above. To see the files you have in the directory you are, type "dir".

Now follow the step by step installer. At the end it is asked if you want to configure your xorg.conf. Say yes, this will select the nvidia driver. Now nVidia driver is installed!

When you return to the console type:
```
sudo gdm
```

You should see the nVidia logo before the login screen.

Enjoy!


NOTE: the new nVidia drivers from their web site were uploaded by nVidia on the February 26, 2008.

Hey thanks but the installer is showing that libc for the driver is not installed I did try this command but it din work out !!
```
 apt-get install build-essential

```
and it say some kernel package for the drive is not installed

what shall I do some one help me !!!

---

### Post by Yellow Pasque on 2008-07-23
Perhaps:
```
sudo apt-get install libc6-dev linux-libc-dev linux-headers-generic
```

---

### Post by Dileeshvar on 2008-07-23
hey guys,
Ya i did sort it out but now,
I am also facing the same with my nForce 610i and
I did try all the commands and procedure listed 
but still not getting it done !!
 help me out !!:confused::confused:

---

