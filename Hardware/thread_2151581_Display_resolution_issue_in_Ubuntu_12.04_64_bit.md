---
title: "Display resolution issue in Ubuntu 12.04 64 bit"
date: 2013-06-05
forum: Hardware
---

### Post by Philip Gray on 2013-06-05
Good morning
 
I recently purchased a new PC. It has the following hardware:
Gigabyte B75M-D3H Ivy Bridge Motherboard
Memory 16GB DDR3 1333
Two Samsung SATA DVD Writers
INTEL CI3 3220 3.3GHZ 3M LGA11 CPU
GeForce GT630 2GB 128BIT graphics card
2TB SATA Western Digital Green hard drive
1TB SATA Seagate hard drive

I have installed Windows 7 Ultimate and Ubuntu 12.04 64 BIT. I have removed the GeForce 
graphics card because my current monitor does not work with it graphics card and I have 
been unable to find a monitor with a resolution greater than 1366x768. So I have been 
forced to use the motherboard's onboard graphics which is a AMD CrossFireX.

My issue is that I cannot get a resolution higher than 1024x768 with this onboard graphics 
card. The Display option under System settings only has two resolutions:- 1024x768 and 
800x600. In Windows 7 with the same graphics card I have resolutions of 1920x1440 and 
higher. In Windows 7 I am using a resolution of 1280x1024 which I would like to also have 
in 12.04. I also had a look under the drivers tab to see if there are any proprietary 
graphics drivers. None are shown. On my other PC where I have Ubuntu 12.04 32BIT installed 
it shows NVidia drivers for my GeForce 8400GS graphics card.

How can I get a higher resolution in 12.04 64BIT. Are there proprietary drivers available 
for the AMD CrossFireX graphics card? I have looked in Google but have not found anything 
helpful.

Regards
Philip

---

### Post by vadimkolchev on 2013-06-05
What does ```
xrandr
``` give you? Please paste the output here.

---

### Post by Yellow Pasque on 2013-06-05
> So I have been forced to use the motherboard's onboard graphics which is a AMD CrossFireX.
The integrated graphics is the intel HD2500 (built into the CPU). The motherboard spec supports a Crossfire configuration, but that doesn't mean you have one (and Crossfire doesn't work on Linux anyway).

> My issue is that I cannot get a resolution higher than 1024x768 with this onboard graphics card. 
Most likely, you forgot to remove the proprietary nvidia driver.

---

### Post by Philip Gray on 2013-06-06
Hi [**[COLOR=#000000]vadimkolchev[/COLOR]**]("http://ubuntuforums.org/member.php?u=1658396")

Thank you for yr prompt response. Here is the output you requested:

Screen 0: minimum 320 x 200, current 1024 x 768, maximum 8192 x 8192
VGA1 connected 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       60.0* 
   800x600        60.3     56.2  
   848x480        60.0  
   640x480        59.9  
HDMI1 disconnected (normal left inverted right x axis y axis)
DP1 disconnected (normal left inverted right x axis y axis)
HDMI2 disconnected (normal left inverted right x axis y axis)
DP2 disconnected (normal left inverted right x axis y axis)

Regards
Philip

---

### Post by Philip Gray on 2013-06-06
Hi [**[COLOR=#000000]Temüjin[/COLOR]**]("http://ubuntuforums.org/member.php?u=327594")

Tks for yr reply you really helped me. I never got to install anything because my monitor just stayed blank and powered down. After I read yr post I stuck in the CD that came with my motherboard and it installed a load of intel drivers in Win 7. I checked in Win 7 but, as true to form, it did not tell me what GPU the motherboard was using. It installed a bucket load of resolutions, most you would never use. I use 1280x1024.

Thanks to yr very valuable input I did a search on Google and I found out a few things. Intel has an installer available called:
Intel(R) Linux* Graphics Installer version 1.0.1 for Ubuntu* 13.04 (64-bit) 
intel-linux-graphics-installer_1.0.1_amd64.deb

I am not sure whether I safe install this as the web page says it is for 13.04. The wup8d website, where I got the link to this, is not very clear, it just mentions that this update fixed some issues.

Another web site mentioned that I need this package: sudo apt-get install xserver-xorg-video-intel
I tried to install it from synaptic but I got these dependencies issues:
xorg-video-intel 
xorg-video-abi-11 
xserver-xorg-core (>=2:1.10.99.901) 

I could not find these files in  synaptic. What should I do now? With all the hassle I am having I am a little vary of trying to find, download and install the deb files for this. I do not want to create a bigger problem for myself.

Regards
Philip
P.S. Sorry for the long response

---

### Post by Yellow Pasque on 2013-06-06
Ubuntu comes with the intel drivers pre-installed. You need to remove the proprietay nvidia driver, and make sure you delete any /etc/X11/xorg.conf file  you have.

---

### Post by vadimkolchev on 2013-06-06
According to xrandr, the maximum you can have currently is 1024x768, unfortunately.

---

### Post by Yellow Pasque on 2013-06-06
> **vadimkolchev said:**
> According to xrandr, the maximum you can have currently is 1024x768, unfortunately.

That's probably because the generic VESA driver is being used. Need to see /var/log/Xorg.0.log to know for sure.

---

### Post by Philip Gray on 2013-06-07
Hi [**[COLOR=#000000]Temüjin[/COLOR]**]("http://ubuntuforums.org/member.php?u=327594")

I did not install any NVidia drivers. When I had the NVidia card in my PC I could not see the BIOS screen so I could see the ubuntu live cd. When I took the card out and connected to the onboard card I could see the BIOS and the ubuntu live cd. I installed 12.04 with the NVidia card not in my PC. I had a look in synaptic and found an entry nvidia-common. When I selected it for removal, synaptic advised that it would also remove the ubuntu-desktop package. I have attached the Xorg.0.log file and some screenshots.

I noticed in synaptic that there are a number of xserver-xorg-core-lts-quantal package entries enabled. I do not know where these 12.10 entries came from. I saw that the latest installer on intel's linux website is xserver-xorg-core-lts-quantal_1.13.0-0ubuntu6.1~precise3_amd64.deb. I also saw that the xserver-org-core 2:1.7.6-2ubuntu7.12 package is installed.

Regards
Philip

---

