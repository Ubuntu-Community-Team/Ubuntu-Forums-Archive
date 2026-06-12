---
title: "[HOWTO] Ubuntu 7.10 and ASUS F3Sv"
date: 2007-10-19
forum: Hardware &amp; Laptops
---

### Post by Fittersman on 2007-10-19
alright, after a few trial and error sessions im running the new ubuntu 7.10 on my ASUS F3Sv.

What works and what doesnt:

**Works**
--Wireless
--direct rendering
--memory card reader
--touchpad
--some of the Fn keys
**Doesnt**
--fingerprint reader
--some of the Fn keys
**Untested**
--webcam
--TV tuner
--anything i didnt list (unless i missed it)

First, you will need the alternate x64 install CD, you can get that here:
[http://www.ubuntu.com/getubuntu](http://www.ubuntu.com/getubuntu)

it should install without any problems but dont forget to make a backup of your important data incase something does go wrong.

[SIZE="7"][COLOR="Blue"]To get X working[/COLOR][/SIZE]

if at all possible get the Nvidia driver before somehow and place it somewhere where you will not forget, such as a usb stick, or an SD card in the memory card reader (yes, it works :D)

after the install process is complete, remove the CD from the drive and reboot INTO RECOVERY MODE (the normal mode will NOT work yet)

you will come to a command line, type:
```
startx
```

when X starts, it will give you a warning that you are running as root, click on continue. You also may get a user agent switcher failure warning, click on dont reload.

at the top of your screen, click System --> Administration --> Synaptic Package Manager. Search for libc. Mark both libc-dev and libc6-dev for installation. Click Apply. You will need to reinsert the CD to install these packages.

go to [http://www.nvidia.com/object/linux_display_amd64_100.14.19.html](http://www.nvidia.com/object/linux_display_amd64_100.14.19.html) and download the video driver, remember where this is downloaded to (most likely the desktop)

In the top right corner click the shutdown button (it will appear to be frozen for about a minute, just wait) then select log-out.

you should be back at the command line, so type:
```
telinit 3
```

now you can login with the account you created during the install process.

at the top of your screen, click System --> Administration --> Services. Scroll down until you come across "Graphical login manager (gdm)". Now UNcheck the box beside it. You should be back at the command line again.

once again, type: 
```
telinit 3
```

this brought me to some weird stuff (will file a bug report tomorrow), so i had to force reboot, i just didnt want to leave it out incase it actually did something although i doubt it (hold down the power button to force reboot)

when you restart, restart into recovery mode again and type:
```
telinit 3
```

it will go really fast, then one process will seem to take forever, just press enter and it will finish.

login using your account.

now, cd to the directory you saved the Nvidia driver to earlier and type:
```
sudo sh NVIDIA-Linux-x86_64-100.14.11-pkg2.run
```

there is no precompiled thing for this kernel, so say no that you dont want to search the internet for one (if you say yes you will end up in the same place anyway)

go through it normally, until you get to a prompt that asks you if you want to install the 32-bit openGL drivers. SAY NO

after the installation it will ask if you want the nvidia-xconfig utility to configure the xorg.conf file for you, say yes.

after the driver is installed, you will be back at the command line, now type:
```
sudo shutdown -r now
```

this time when you reboot, you can reboot into the normal ubuntu kernel! (it will shut off the LCD screen, so press Fn + F8 to see the loading bar if you want, i dont know why this is so if anyone knows how to fix that please share :))

one last problem, the windows have no frame... to fix this go to System --> Preferences --> Appearance. Now click on the 'visual effects' tab and select none.

should work now!


/----------------------------------------------------------------------------------------------------------------------------------------/

i will test some more things tomorrow.... but for now its late im going to bed, if there was any problems or something i missed, please tell me as i only had jot-notes of what i did to go off of while writing this.

---

### Post by ricperry1 on 2008-03-26
Using this method, there is no window borders.  Since the visual effects are OpenGL composited, maybe by installing the 32-bit OpenGL stuff you will get the window borders back.  Maybe not though.

---

