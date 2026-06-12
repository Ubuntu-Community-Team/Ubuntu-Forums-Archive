---
title: "eGalaxTouch driver help"
date: 2010-01-23
forum: Hardware
---

### Post by mikesir87 on 2010-01-23
Hi!  First time thread post here!  :-)  Ok... I've got an HP Pavilion tx1220us, and I've installed the eGalaxTouch drivers.  I ran through the configuration and gotten calibration to work.  But, something kinda weird happens.  When I touch the screen, initially nothing happens.  It's not until I put my finger on the trackpad that the "click" from the screen occurs.  I can hit the screen, remove the stylus, and then tap the trackpad, and it goes directly to where I clicked.  Any ideas on how to get the screen to register the click on its own?  Thanks in advance!

Also, I'm running 9.10 with Kernel 2.6.31-17.

---

### Post by mikesir87 on 2010-01-28
Sorry to bump this, but it's been several days so far.  Does anyone have any ideas?

---

### Post by Eredeath on 2010-01-28
I've have the same problem with my HP tx1000. I suspect that the x configuration file needs to be edited, though i am unsure how. Sorry i can't be more help.

---

### Post by championswimmer on 2010-05-06
**[COLOR=red]Installing UBUNTU 9.04 on HP TX1000 laptop (touchscreen+fingerprint)[/COLOR]**
  [COLOR=red]1.       [/COLOR][COLOR=red]Install Ubuntu 9.04 Jaunty[/COLOR]
  [COLOR=red]2.       [/COLOR][COLOR=red]Connect to Internet and open SYSTEM>ADMINISTRATION>HARDWARE DRIVERS [/COLOR]
  [COLOR=red]3.       [/COLOR][COLOR=red]Install NVIDIA current version[/COLOR]
  [COLOR=red]4.       [/COLOR][COLOR=red]Install Broadcomm B43 driver[/COLOR]
  [COLOR=red]5.       [/COLOR][COLOR=red]Install software modem driver[/COLOR]
  [COLOR=red]6.       [/COLOR][COLOR=red]Download eGalaxDriver from website [/COLOR][COLOR=#76923C][[COLOR=#76923C]http://home.eeti.com.tw/web20/eGalaxTouchDriver/linuxDriver.htm[/COLOR]]("http://home.eeti.com.tw/web20/eGalaxTouchDriver/linuxDriver.htm")[/COLOR][COLOR=red][/COLOR]
  [COLOR=red](download for kernel 2.6.xx)[/COLOR]
  [COLOR=red]7.       [/COLOR][COLOR=red]Extract tarball and run setup.sh from terminal with sudo[/COLOR]
  [COLOR=red]8.       [/COLOR][COLOR=red]Restart Computer and run (with Alt+F2) “eGalaxTouch” (without quotes and linux is case sensitive)[/COLOR]
  [COLOR=red]9.       [/COLOR][COLOR=red]Configure your touchscreen[/COLOR]
  [COLOR=red]10.   [/COLOR][COLOR=red]Open xorg.conf with following command[/COLOR]
  [COLOR=red][FONT=&quot]sudo gedit /etc/X11/xorg.conf[/FONT][/COLOR]
  [COLOR=red]11.   [/COLOR][COLOR=red]Under Section “Device” add the following line[/COLOR]
  [COLOR=red][FONT=&quot]Option  “RandRRotation”        “True”[/FONT][/COLOR]
  [COLOR=red] [/COLOR]
  [COLOR=red]12.   [/COLOR][COLOR=red]Create two launchers on your gnome panel with following commands:-[/COLOR]
  [COLOR=red] [/COLOR]
  [COLOR=red]xrandr –o 1                (for tablet mode) P.S. u can set it “3” as well if u want opposite rotation)[/COLOR]
  [COLOR=red]xrandr –o 0                        (for Laptop mode)[/COLOR]
  [COLOR=red] [/COLOR]
  [COLOR=red]13.   [/COLOR][COLOR=red]Install Cellwriter from synaptic[/COLOR]
  [COLOR=red]14.   [/COLOR][COLOR=red]Install xournal from synaptic[/COLOR]
  [COLOR=red]15.   [/COLOR][COLOR=red]Install the following for finger print recognition[/COLOR]
  [COLOR=red]lib-fprint[/COLOR]
  [COLOR=red]libpam-fprint[/COLOR]
  [COLOR=red]fprint-demo[/COLOR]
  [COLOR=red]16.   [/COLOR][COLOR=red]Open file common-auth[/COLOR]
  [COLOR=red][FONT=&quot]sudo gedit /etc/pam.d/common-auth[/FONT][/COLOR]
  [COLOR=red](delete all lines in the file and paste these lines)[/COLOR]
  [COLOR=red] [/COLOR]
  [COLOR=red][FONT=&quot]Auth    sufficient          pam_fprint.so[/FONT][/COLOR]
  [COLOR=red][FONT=&quot]Auth    sufficient          pam_fprint.so[/FONT][/COLOR]
  [COLOR=red][FONT=&quot]Auth    required           pam_unix.so   nullok_secure[/FONT][/COLOR]
  [COLOR=red][FONT=&quot] [/FONT][/COLOR]
  [COLOR=red](the first line can be copied 3-4 times if u want to allow more than 1 chance to register fingerprint)[/COLOR]
  [COLOR=red]17.   [/COLOR][COLOR=red]Create keyboard shortcuts for screen rotation (here is an example)[/COLOR]
  [COLOR=red]Key                                                                                        Command[/COLOR]
  [COLOR=red]Ctrl+Alt+UP                                                                       xrandr –o 0[/COLOR]
  [COLOR=red]Ctrl+Alt+LEFT                                                                    xrandr –o 1[/COLOR]
  [COLOR=red]Etc[/COLOR]
  [COLOR=red]Etc[/COLOR]
  [COLOR=red](Notes: This Guide will work for any UBUNTU installation upto Karmic (9.10). Unfortunately in Lucid, the developers have tried to provide native support for Touchsdcreen and Nvidia but it has turned out to be sloppy. And there is no xorg file as well. So viable options are to uninstall nv and nouveau drivers and install Nvidia and the run sudo nvidia-xconfig from command line. After that follow steps 4 to 17)[/COLOR]

---

### Post by mikesir87 on 2010-05-06
Thanks for the reply!

Quick question... I installed the eGalaxTouch driver, and something interesting happens.  Whenever I tap the screen, I've noticed that on the "tapDown", the cursor jumps to the top-left corner of the screen (which is where I have my gnome menu).  The click is registered then.  When I left up the tap, the cursor moves to where I actually tapped.

I changed the click mode to "Click on Touch", and it does work how I would think it should.  But, the mouse cursor continues to hang in the top-right corner.  Any thoughts?

---

### Post by naugtur on 2010-05-07
The problem might be related to another mouse driver or another mouse.

How did You change the mode to "Click on Touch"? I have the same unwanted behaviour and I can't change the mode. There is "current mode: normal" in the misc tab of the configuration, but the change button is inactive.

---

### Post by championswimmer on 2010-05-10
sorry buddy no suggestions on that... i told  na it works only upto karmic... u using lucid i gues... it happens.... mytongue in cheek suggestion is to downgrade xorg to 6 from 7

---

### Post by naugtur on 2010-05-11
I was using ubuntu 8.04. eGalax drivers didn't want to install properly on 9.x.

But evdev on Lucid got it for me ;) It works much better than eGalax drivers. 

see my solution here: [http://ubuntuforums.org/showthread.php?p=9254202](http://ubuntuforums.org/showthread.php?p=9254202)

---

