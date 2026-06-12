---
title: "Any reconfiguration of xorg.conf by nvidia-xconfig prevents desktop load"
date: 2018-05-16
forum: Hardware
---

### Post by Keith Myers on 2018-05-16
Ubuntu 18.04 LTS install.  No problem installing new OS with the default [***nouveau***]("https://www.google.com/search?q=nouveau&spell=1&sa=X&ved=0ahUKEwjA6Iuu1ovbAhUSeKwKHZafBCQQBQgmKAA")  drivers.  Desktop working fine.  Installing all my normal configuration and utilities.  Reboot system to add the graphics-drivers ppa.  No problem and select the latest Nvidia 396.24 driver which I am currently using in my other Linux systems.  Installs fine.  Add more utilities and further set up normal configurations.  Nvidia-settings added to the Dock.  Everything looks good.  Reboot system and nvidia drivers working fine.  Now to get the 3 GTX 1070 cards set up for compute.  Need to set cool-bits to get fan control and to set all cards up for compute.  This is where everything goes to he!!.  Run

nvidia-xconfig --enable-all-gpus
nvidia-xconfig --cool-bits=4

xorg.conf reconfigured and new xorg.conf.backup and xorg.conf.original-nvidia-configuration files created.  Look at xorg.conf and see that cool-bits-4 has been added to all screens like usual.  Everything looks normal and exactly what the xorg.conf looks like in my other Ubuntu 16.04 compute systems.  Reboot the system for the new xorg.conf to take effect and to have fan control available in nvidia-settings app.

System boots and I see the normal boot display because I always remove "quiet splash" since I want to see any errors and watch the normal loading of the system.  The boot gets to the end where the display manager blanks the screen and I get the normal purple screen.  But instead of getting the mouse cursor, the screen stays blank.   I finally move the mouse and the cursor is a big "cross" and that is it.  I either have to drop to tty with a alt-ctrl-F3 or push the computer reset button.  I can't restart the display manager with a gdm restart or systemctrl restart gdm.service does nothing.  I can't get to a login screen.

The only way I can get the system back is to boot grub recovery mode, drop to root, mount the drive and cp xorg.conf.backup to xorg.conf and the system boots again to the desktop.  I don't know why either of the normal nvidia-xconfig commands corrupt the xorg.conf or whatever and then prevents loading the desktop or display manager. I have tried both commands together and separately.  Either will make a new xorg.conf that won't boot the desktop. The file looks absolutely correct and I even compared it to my other 3 gpu Ubuntu 16.04 system.  The syntax and section structure is exactly the same.

I have never had any issues with Ubuntu 16.04 adding the use all gpus or fan control before.  I normally use cool-bits=28 on the 16.04 machines but I tried several settings of the cool-bits enable parameters to try and see if the more elaborate settings was causing issues.  cool-bits=4 is the minimum I need to get fan control setting available in nvidia-settings.  I normally just set the gpu fan for 100% fan speed that way since the gpus are run full stop 24/7 with compute loads. 

Can anyone offer a reason why nvidia-xconfig corrupts xorg.conf in Ubuntu 18.04 LTS while is no problem with Ubuntu 16.04?  Help please!!

---

### Post by dino99 on 2018-05-17
path: /etc/X11/xorg.conf.d/

related xorg.conf discussion (scrolldown a bit)  [https://noobminer.xyz/overclocking-multiple-nvidia-graphics-card-linux/](https://noobminer.xyz/overclocking-multiple-nvidia-graphics-card-linux/)

---

### Post by Keith Myers on 2018-05-17
Thanks for the reply.  Nothing relevant in the post though.  I am not mining. I already know how to overclock and enable gpus. Been doing it successfully for years on Ubuntu 16.04.  Something has changed in the way that Ubuntu 18.04 works compared to 16.04 with how nvidia-xconfig and xorg.conf work. 18.04 doesn't have a /etc/X11/xorg.conf.d directory.  Neither do my 16.04 machines.  I will make the directory and the 20-nvidia.conf file and see if that does anything.

---

### Post by Keith Myers on 2018-05-17
Problem solved.  Any further time that nvidia-xconfig was invoked, it created a false xorg.conf file.  The monitor horizontal and vertical sync frequencies were put to nonsense values not matching the original xorg.conf file.

Secondly the Device0 and Device1 names and BusID numbers were switched.  This was likely the main reason the desktop would not load.

The first time I fixed and created the modified xorg.conf file with the fan and overclock settings enabled, it only set the Device0.  I ran the nvidia-xconfig parameters again and fixed the file once more and the next reboot got all cards enabled with fan and overclock settings enabled.

So have no idea why the nvidia-xconfig application is corrupting the file and can't seem to identify the correct Device and monitor frequencies.  This probably should be investigated by the developers.

---

### Post by Keith Myers on 2018-08-10
I have run into this issue on multiple computers of friends that I have been helping install Ubuntu 18.04.  Every time I use nvidia-xconfig to add in thermal control and all gpus enabled, it has swapped PCIe Bus ID's of the cards in the top and bottom slots of the motherboards.  Everytime.  PCIe BusId #5 is re-enumerated to PCIe BusID#10 and vice versa.  So upon the next reboot the system won't display any screen because Ubuntu is looking for the monitor on the wrong graphics card.  I now know that once you have reconfigured xorg.conf for thermal control and enable all gpus, you must go back into the file and edit the file to move the Bus ID numbers back to their original enumeration before rebooting.

This is a definite flaw in nvidia-xconfig.  But at least now I know to expect this and preemptively make the necessary changes to xorg.conf to avoid the boot grief.

---

### Post by #&amp;thj^% on 2018-08-10
FWIW I just copy my xorg.conf to "**/etcX11/Xsession.d/**" and rename it to "**20-nvidia.conf**"

---

### Post by Keith Myers on 2018-08-10
But then you don't get any of the changes you made to xorg.conf for thermal and fan control or all gpus enabled.

---

### Post by #&amp;thj^% on 2018-08-10
Yes I do. ;)

---

### Post by Keith Myers on 2018-08-21
But do you get the swapped BusID's in the first place?  No point in copying a corrupted xorg.conf to 20-nvidia.conf.  You still won't have a monitor output.

---

### Post by dustar1986 on 2019-05-09
> **Keith Myers said:**
> But do you get the swapped BusID's in the first place? 

Yes, I get swapped BusIDs on Ubuntu 19.04 with Nvidia 418.56. My TITAN RTX in slot2 (further to CPU) got a lower BusID (A1:00) order while my GT1030 in slot1 (closer to CPU) got a higher order (C1:00). My only monitor is on the GT1030. With everything default, I have no problem with display on every boot.

I clicked in here because I was searching for which exact file I should save X settings on Ubuntu 19.04, as I want to change coolbit as well. So my question is: Shall I edit the "20-nvidia.conf" under "/etc/X11/Xsession.d" ?

---

### Post by hgkrug1 on 2019-05-23
I have seen many people battling with the same issue.  The solution discussed above seems the most promising form all the proposed solutions I have seen and tried (unsuccessful).  However, I apologise to ask, would you be so kind to provide the solution a bit more with details?  I don't have the technical knowledge you guys seem to have!

---

### Post by hgkrug1 on 2019-05-23
I have the same issue on Ubuntu 19.04 with a NVIDIA Corporation GP107 [GeForce GTX 1050] card.  According to the Nvidia website, the nvidia-driver-430 should work. I attempted solution above by 

copy xorg.conf to "**/etc/X11/Xsession.d/**" and rename it to "**20-nvidia.conf**" 				after I have installed the driver.

Same problem after reboot.

---

### Post by hgkrug1 on 2019-05-23
The above solution did not work for me.  I found a solution for this Nvidia driver issue (on ubuntu 18 and 19). See instructions at the top at [https://ubuntuforums.org/showthread....nvidia+drivers]("https://ubuntuforums.org/showthread.php?t=2419319&highlight=nvidia+drivers"), it worked for me!

---

### Post by hgkrug1 on 2019-05-23
I found a solution for this Nvidia driver issue (on ubuntu 18 and 19). See instructions at the top at [https://ubuntuforums.org/showthread....nvidia+drivers]("https://ubuntuforums.org/showthread.php?t=2419319&highlight=nvidia+drivers"), it worked for me!

Unfortunately, I could not reproduce the installation on a freshly installed system.

However, I found a suitable fix at entry #19 of [https://bugs.launchpad.net/gdm/+bug/1798790](https://bugs.launchpad.net/gdm/+bug/1798790)

Try this as a workaround: edit /etc/gdm3/custom.conf 
and uncomment the line: 
#WaylandEnable=false

---

### Post by unterdenlinden2 on 2019-06-20
I was able to make my Xorg.conf work by running:
```

nvidia-xconfig --enable-all-gpus
nvidia-xconfig --cool-bits=4

```

Then open nvidia-settings and your Xorg.conf and remap the deviceX and corresponding BusIDs in the Xorg.conf file to what is shown under each GPU X in nvidia-settings. For some reason  nvidia-xconfig switches these around, as has been mentioned. Then my desktop would load and fan control was allowed across all GPUs.

---

