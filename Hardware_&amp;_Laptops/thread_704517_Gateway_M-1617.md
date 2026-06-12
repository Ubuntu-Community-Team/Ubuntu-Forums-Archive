---
title: "Gateway M-1617"
date: 2008-02-22
forum: Hardware &amp; Laptops
---

### Post by stickybeatz on 2008-02-22
I picked up a Gateway M-1617 recently from Best Buy and wanted to install Ubuntu on it. First thing I'm noticing by doing some Googling is that I'm going to have wireless issues and sound issues. Has anyone out there gotten everything to work properly on an M-1617? And if so, any tips or advice?

---

### Post by johnl on 2008-03-07
This may be a little late, but I have the same model laptop running Ubuntu and I can offer you some advice:

1.  Install Ubuntu 32-bit edition.  I installed the 64-bit edition first, and couldn't even find working 64-bit windows drivers to use with ndiswrapper.

2.  I had to use ndiswrapper to install the windows driver, and then force ndiswrapper to associated with the wireless card: [This Post](http://ubuntuforums.org/showthread.php?t=575785) can give you the specifics.

3. To get sound playback working, all I had to do was install the linux-backports-modules-generic package.

I haven't experimented too much with getting sleep/suspend working, so I can't offer too much advice there.

Hope this helps!

---

### Post by silver_mx on 2008-03-14
**This post could be related to an Ubuntu bug filed at**: [http://ubuntuforums.org/showthread.php?t=575785](http://ubuntuforums.org/showthread.php?t=575785) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Hello, I know this problem is solved now here : [http://ubuntuforums.org/showthread.php?t=575785](http://ubuntuforums.org/showthread.php?t=575785) (It helped me alot) , but I would like to add some steps that were missing in my case. I have a Gateway-M1617 but I believe it can work for other models.

1.-Download the wireless card network driver (marvell topdog 802.11n Wireless) from this link [http://kbserver.netgear.com/release_notes/d103154.asp](http://kbserver.netgear.com/release_notes/d103154.asp). The driver is for this device WN311T - RangeMax&#8482; Next Wireless PCI Adapter, however works. The file's name is wn311t_setup_4_1.exe.

2.-Execute the file in any WINDOWS XP (It is necessary because only using windows XP the installer will create the drivers that I comment in this post, if you use Vista, the installer will create just the drivers for Vista), even if the computer doesnt have that device connected. The setup will try to install it, but tThe idea is only decompress the executable file and take 2 files: NetMW14x.inf and netmw145.sys. They are installed in c:\Program Files\Netgear\WN311T. Take the both files and copy to any directory in ubuntu, for example: /home/user/Desktop

3.-Open a console, go to the directory where you copied the both files (NetMW14x.inf and netmw145.sys) and type "sudo ndiswrapper -i NetMW14x.inf" . Ndiswrapper needs the both files to install the driver. If you dont have installed ndiswrapper, use synaptic to install it. Ndiswrapper comes with the CD so you dont need to have internet to install them.

4.-Type "sudo ndiswrapper -a 11ab:2a08 netmw14x". Where 11ab:2a08 is the wireless network card id (lspci -nn will show device ids).

5.-Im not sure if it is needed but just in case type this  "sudo ndiswrapper -m". It will  write configuration for modprobe.

6.-Type "sudo ndiswrapper -l" will now say the device is present and it can be configured normally.

7.-Edit the file /etc/modules. "sudo gedit /etc/modules". And add a new line at the end. Type "ndiswrapper". 
This line will execute ndiswrapper when linux starts. In my case I nedded this last step to make work my card.


That's it. It is working now. I hope this will help to others.

---

### Post by animatt on 2008-03-31
I am attaching the files you will need it is in a zip folder.  I followed directions above and worked fine.  I am attaching the files in a zip to eliminate the need for a windows computer, or the need to install WINE.

---

### Post by johnl on 2008-05-05
Update -- I managed to get the built in mic working, so now everything seems to be good!

I believe the only thing that needs to be done (besides selecting it for recording in alsamixer / gnome-alsamixer) is to change the model for alsa.

Open /etc/modprobe.d/alsa-base and add the line:

options snd-hda-intel model=gateway

And restart.

Hopefully recording should now work!

---

