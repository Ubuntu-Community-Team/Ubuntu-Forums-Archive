---
title: "NVIDIA onboard GPU driver"
date: 2009-04-11
forum: Installation &amp; Upgrades
---

### Post by fixxxer50 on 2009-04-11
Hi I just installed 9.04 and after install I tried to install the graphics driver via system>admin>hardware drivers and shows me version 96 for my display hardware which is NVIDIA Geforce4 MX integrated GPU. After download and install when I restart the login display has some random red pattern on the top and the whole screen is blank. I can hear the startup tone though. Also I can see the mouse which is ok and can move around. 
I checked [ftp://download.nvidia.com/XFree86/Linux-x86/185.19/README/appendix-a.html](ftp://download.nvidia.com/XFree86/Linux-x86/185.19/README/appendix-a.html)
where it says I need 96.43.xx driver and so I downloaded Version: 96.43.11 . 
Which kinna looks like the same version I installed initially via system>admin>hardware drivers.

I have no idea how to manually install the driver and fix the kernel. Can someone help please. 

here is my xorg.conf after installing the driver from system>admin>hardware drivers

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
	Option	"AddARGBGLXVisuals"	"True"
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection

-------------------------------------------------------------------------
Can someone please help .

---

### Post by fixxxer50 on 2009-04-11
I saw a lot of updates nearly 350 MB worth so I thought I'll give it a try and downloaded it. I saw something mentioned about nvidia 96.xx.xx in the update in the terminal. So I was happy, but after the update, when I rebooted, instead of the log in screen there was a big NVIDIA logo and the comuter froze. This happened a couple of times finally I had to use the recovery mode and restore the default xorg file. 

How do I install a driver and configure it properly of NVIDIA Geforce4 MX Intergrated GPU. 
If you know please help me out.

---

### Post by cariboo on 2009-04-11
I would suggest you open up Sysnaptic Package Manager and remove all mention of nvidia, then restart X, either by using Ctrl=Alt-Backspace or rebooting, and then try to install the restricted drivers. Personally I always do the updates first on a new installation before enabling the restricted drivers.

Jim

---

### Post by fixxxer50 on 2009-04-11
> **cariboo907 said:**
> I would suggest you open up Sysnaptic Package Manager and remove all mention of nvidia, then restart X, either by using Ctrl=Alt-Backspace or rebooting, and then try to install the restricted drivers. Personally I always do the updates first on a new installation before enabling the restricted drivers.

Jim

Thanks Jim I just removed all the NVIDIA's from synaptic its wierd a lot of them I think 181 , 76 etc were selected except the 96 which is the one which supports my card.
when I removed them and went to system/admin/hardware drivers There was no listed driver (after reboot) so I went to synaptic and I am downloading 96 package right now. Will write a feed back asap.

---

### Post by fixxxer50 on 2009-04-11
Hi Jim I tried. I deleted every NVIDIA there was in synaptic, except for NVIDIA - common , NVIDIA all modaliases. and then rebooted, then detected the hardware driver, Installed 96 and rebooted again. I still get a blank screen at boot, some red pattern on the top,I can see the pointer move it around till log in sound, after that mouse doesnot move no Num Lock response, the system just hangs. 
Any Idea whats going on here. and what I need to do?

---

### Post by cariboo on 2009-04-11
I haven't had any experience with this problem, Nvidia has always just worked for me, even when I installed a new video card, it just plain worked.

I would suggest trying envy-gtk to install the drivers. You'll have to restart in recovery mode again and run xfix again, then once you are back at the desktop, use Synaptic to install envy-gtk, and use it to install the drivers. You will have to get rid of all mention of nvidia again, make sure you uninstall nvidia-common too.

Jim

---

### Post by fixxxer50 on 2009-04-12
> **cariboo907 said:**
> I haven't had any experience with this problem, Nvidia has always just worked for me, even when I installed a new video card, it just plain worked.

I would suggest trying envy-gtk to install the drivers. You'll have to restart in recovery mode again and run xfix again, then once you are back at the desktop, use Synaptic to install envy-gtk, and use it to install the drivers. You will have to get rid of all mention of nvidia again, make sure you uninstall nvidia-common too.

Jim
Yesterday Night I got fed up I reinstalled Ubuntu from the alt disc then I updated all the latest updates and then after reboot tried to install display driver from  admin/system/hardware drivers/ 
I am still getting the same problem. Still getting stuck at Log in screen. 
:(

---

### Post by overdrank on 2009-04-12
Please correct me if I am wrong  but I believe there was issue with intrepid and the legacy nvidia drivers with the new X. It may not be solved in Jaunty yet and you may look [here]("http://ubuntuforums.org/showthread.php?t=1107866&highlight=NVIDIA+Geforce4+MX")

---

### Post by fixxxer50 on 2009-04-12
> **overdrank said:**
> Please correct me if I am wrong  but I believe there was issue with intrepid and the legacy nvidia drivers with the new X. It may not be solved in Jaunty yet and you may look [here]("http://ubuntuforums.org/showthread.php?t=1107866&highlight=NVIDIA+Geforce4+MX")

Does that mean that if I install a version previous to 8.10 I will be able to install the display driver? 
If yes then Please tell me which version of Ubuntu should I install. 
Also I am going through the form you mentioned about right now. Do you think they will be able to fix the issue in 9.04 and if yes how will I or other users who have the same problem find out? Will I be able to get somekind of a notification?

---

### Post by jcoelho on 2009-04-24
Hello guys,

I'm having a very similar problem, Ubuntu 9.04 detects my graphic card (GeForce4 MX integrated GPU, in a Nforce 2 chipset). The OS suggest to install the Nvidia driver 96.43.10...i install it and at first sight everything seems to be ok, but after that my PC hangs randomly.

Do you know what's happening? I think the drivers for legacy Nvidia GPU are not totally supported yet.

---

### Post by jcoelho on 2009-04-26
Hello there,

     I think my problem with Ubuntu 9.04 was solved, I updated the BIOS on my motherboard and everything is working fine...at least for the moment.

     I have been testing my system for a few hours and everything seems to be OK.

---

### Post by fixxxer50 on 2009-09-06
> **jcoelho said:**
> Hello there,

     I think my problem with Ubuntu 9.04 was solved, I updated the BIOS on my motherboard and everything is working fine...at least for the moment.

     I have been testing my system for a few hours and everything seems to be OK.

Sorry for the late reply. I know its been a while. But I had kinna given up on the old computer. But recently my laptop with ubuntu just died on me so I thought I'll give it another try. So I installed ubuntu 9.04 from alt cd. it was giving me the same error initially. Then I started playing around with bios settings for the graphics card. I set everything to optimal, for the graphics Gpu settings. which made the memory of onboard gpu just 32 mb. but it worked. The system works very stable with the basic normal animation settings. I have not tried the full animation, because the shared memory is just 32 mb. when I try to make shared memory as 128 mb it starts crashing, my boxee and other programs start crashing, also the agp aperture size is fixed on 64 mb. 
Now I posted this incase someone else is facing the same problem, also does anyone know why am I not able to increase the shared memory on my gpu. Any help is appreciated. 
Thanks!

P.S. and yes I had made the chages to the bios before installing ubuntu, and when the installation was finished, I just selected 96 drivers from the hardware drivers and installed them directly, and it worked without a problem, right off the bat.

---

