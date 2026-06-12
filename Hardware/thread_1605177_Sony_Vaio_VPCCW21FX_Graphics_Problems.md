---
title: "Sony Vaio VPCCW21FX Graphics Problems"
date: 2010-10-25
forum: Hardware
---

### Post by Fait on 2010-10-25
I recently became a convert to ubuntu from the tyrant known as winblows. However, my laptop has a few problems * Black Screen on startup, even with latest graphics driver from nvidia, with or without the nomodeset option. (I have to select the failsafe graphics option with nomodeset) * Brightness keys do not work * HDMI doesn't work (I suspect because the graphics driver isn't working. I had it working with video only at one point when the graphics driver was working, but had to reinstall because of an unrelated problem and now I can't get anything to work. * Even when the Nvidia driver was working I had screen tearing when watching video. * Wireless card drops almost all of its packets almost all the time (But I plan on just replacing it anyway, its only 25$) 

Any and all help would be greatly appreciated. I have started to convert my friends and family to Ubuntu with great success. 

Sony Vaio CW series Intel Core I3 330-M Processor, Nvidia GeForce GT 310m graphics.

Ubuntu 10.10 Maverick Meerkat

---

### Post by jjchm on 2010-11-05
Hi, recently i installed Ubuntu 10.10 64 bits in my laptop Sony VPCCW21FX, the procedure for complete that mission are:

1) Download ISO "Alternate Mode", the normal ISO don't boot, blank screen.
2) When the cd is ready, put in your cd-drive, when the initial screen appear, activate the option "nomodeset" (F6 for view the options).
3) Continue with the process.
4) When the S.O. is ready, update your system.
5) Download the nvidia driver in the official site ([www.nvidia.com]("http://www.nvidia.com/")), the ultimate driver is the .260, but in some others threads in this forum recommends use the .256 driver. I use that version .256.
6) The procedure for install the nvidia driver is very easy:

- Ctrl+F1, use your username and password
- execute sudo /etc/init.d/gdm stop. 
- chmod +x drivernvidia.run
- ./drivernvidia.run
- Choose "YES" when the installer ask you for create de xorg.conf.

7) reboot your system, before of the initial screen for enter your user and pass, you should see the nvidia logo screen.

That's all for use ubuntu 10.10 64bits in VPCCW21FX. 

The wireless network don't work very well, packet loss (30% - 40% aproximately).
The wire network work perfect. 0% Packet Loss.

Best Regards.
 		                   		  		  		  		  		  	   	 		 [IMG]http://ubuntuforums.org/images/statusicon/user_online.gif[/IMG]  		 		 		[[IMG]http://ubuntuforums.org/images/buttons/report.gif[/IMG]]("http://ubuntuforums.org/report.php?p=10071200") 		 		  	 	 	 	 		  		 			[IMG]http://ubuntuforums.org/images/misc/progress.gif[/IMG] 			[[IMG]http://ubuntuforums.org/images/buttons/edit.gif[/IMG]]("http://ubuntuforums.org/editpost.php?do=editpost&p=10071200")

---

