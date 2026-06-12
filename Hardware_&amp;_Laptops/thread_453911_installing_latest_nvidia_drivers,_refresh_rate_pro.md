---
title: "installing latest nvidia drivers, refresh rate prob"
date: 2007-05-24
forum: Hardware &amp; Laptops
---

### Post by bishop9226 on 2007-05-24
i have an onboard nvidia 6100. i sold my ati x1950pro because its junk and i want to use linux with my nice beryl and wobbly windows:).  so now that i am using onboard i am happy but i can only get my refresh rate to 52hz stable @ 1024x768.  when i change it to 80 it refreshes the monitor then nothing respond anymore except the mouse and i have to reboot

im using the nvidia restricted driver that came with feisty and i assume i need to update this driver correct?  

i went here [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html) to get the latest driver for amd64 x2, i wasnt sure which one to get so i got the latest one - NVIDIA-Linux-x86_64-1.0-9755-pkg2.run

im not sure how to install it, as in the instructions it says to go to type

sh NVIDIA-Linux-x86_64-1.0-9755-pkg2

so i do that in terminal and it says it cant run it.

any help on getting me going would be appreciated:)

---

### Post by JSThePatriot on 2007-05-24
"It says it can't run it." Isn't very descriptive. I went through, and installed the drivers from NVidia, as you are wanting to. I also did it on AMD64. If you could tell me exactly what it is that "it cannot run" and/or "why" then I would be more than happy to offer further assistance.

Thanks, and I hope I can help,
JS

---

### Post by useResa on 2007-05-25
The procedure to install the downloaded Nvidia driver is basically as follows:
1. Press <CTRL><ALT><F1> to get into terminal session
2. Give the command ```
sudo /etc/init.d/gdm stop
``` to halt the Gnome display manager
3. Give the command ```
sudo  sh ./NVIDIA-Linux-x86_64-1.0-9755-pkg2.run
``` to run the installer.
4. ACCEPT the agreement and for the rest basically give the default answers **EXCEPT** to the question whether a precompiled kernel should be download. Answer NO (instead of the default YES).
5. Accept the "offer" to configure your xorg file.
6. I mostly conclude with a complete restart (although this is not specifically required) by issuing the command ```
sudo shutdown -r now
```

I hope this help you further along.

---

### Post by bishop9226 on 2007-05-25
thanks, i tried doing it this way - [http://doc.gwos.org/index.php/Latest_nvidia_feisty](http://doc.gwos.org/index.php/Latest_nvidia_feisty)

method 1.  and i didnt get any errors or anything so i think it worked? how do i check?  

my restricted driver manager says, "NVIDIA Accelerated Graphics Driver" but i dont remember if it said that before.  


also what can i do about adding more refresh rates?  mine maxes at 80 but 80 gives me a bunch of horizontal lines so i have to use "79".

also, when i do ctrl+alt+f1, i exit x server and go into terminal but none of the commands work at all. like ls doesnt list anything, and i cant navigate to my desktop folder like i can do in shell. whats up with that?

---

### Post by useResa on 2007-05-25
> **bishop9226 said:**
> thanks, i tried doing it this way - [http://doc.gwos.org/index.php/Latest_nvidia_feisty](http://doc.gwos.org/index.php/Latest_nvidia_feisty)

method 1.  and i didnt get any errors or anything so i think it worked? how do i check?  

my restricted driver manager says, "NVIDIA Accelerated Graphics Driver" but i dont remember if it said that before.  
 You can check what driver is indicated in your xorg.conf file.
Open a terminal (Applications -->  Accessories --> Terminal) and issue the command
```
gksudo gedit /etc/X11/xorg.conf
```Scroll down until you come across the text
> Section "Device"
    Identifier     "nVidia Corporation G72M [Quadro NVS 110M/GeForce Go 7300]"
    Driver         "nvidia"
EndSectionNaturally your identifier might be slightly different since you have a different video card.
Important is that the Driver indicates **nvida**

> **bishop9226 said:**
>  also what can i do about adding more refresh rates?  mine maxes at 80 but 80 gives me a bunch of horizontal lines so i have to use "79".
Sorry, can not help you here.
Maybe someone else can.

> **bishop9226 said:**
>  also, when i do ctrl+alt+f1, i exit x server and go into terminal but none of the commands work at all. like ls doesnt list anything, and i cant navigate to my desktop folder like i can do in shell. whats up with that?Basically you are already in a terminal so you don't have to go into a terminal.
However all commands should work. So -- after you login -- you should be able to go to your desktop folder by issuing the command
```
cd Desktop
```
Could you otherwise be more specific which command you tried and what the result was?

---

### Post by dabl on 2007-05-25
In a console window, if you type ```
nvidia-settings
``` it should bring up the Nvidia control panel.  Near the top is a menu item that is approximately "XServer Display Configuration".  Click that and a panel will open that has the current monitor resolution and refresh rate.  You can click on the refresh rate and it MIGHT offer you some other rates (no guarantee). If it does, you can pick the highest rate available and it should work at that rate. On my Kubuntu 32-bit, I can do that, but in Ubuntu 64-bit, it says "Auto" and that's all I get, on the same hardware.

To use the "Save to X configuration file" button at the lower right of this panel, you have to be running as Super User, i.e. you would have to to run it as ```
sudo nvidia-settings
```  But I've had it bork up xorg.conf by doing that, so don't try it before you've made a backup of your current xorg.conf.

HTH

---

### Post by bishop9226 on 2007-05-25
got it to 85 in the control panel;), im happy with that. thanks

---

