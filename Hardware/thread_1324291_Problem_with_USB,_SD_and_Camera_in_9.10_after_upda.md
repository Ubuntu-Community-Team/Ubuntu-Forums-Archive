---
title: "Problem with USB, SD and Camera in 9.10 after update."
date: 2009-11-12
forum: Hardware
---

### Post by lodravah on 2009-11-12
Hello.

After doing an update today or yesterday, my MSI Wind does no longer mount USB-pendrives, external HDD, USB mouse/keyboard (works when I boot with the mouse and keyboard plugged-in, though USB-pendrives do not) or SD-card. Though my SD-card reader haven't worked since I installed 9.10.. 

lsusb and fdisk does not show the devices at all, manual mount does not work. 

Pretty much screwed here...

---

### Post by canadianwriterman on 2009-11-13
Same problem here. I upgraded my MSI Wind U100 to 9.10 UNR and now have no USB. I read some posts about interference from "uvcvideo," uninstalled it and also blacklisted it, but no love.

Right now my MSI is a doorstop because I can't even install another distro on it!

---

### Post by lodravah on 2009-11-13
> **canadianwriterman said:**
> Same problem here. I upgraded my MSI Wind U100 to 9.10 UNR and now have no USB. I read some posts about interference from "uvcvideo," uninstalled it and also blacklisted it, but no love.

Right now my MSI is a doorstop because I can't even install another distro on it!

yay. I'm not alone :P To be honest, I'm not expecting a fix to this issue except for a new kernel, which might pop up some time soon, or not.. I guess it is too specific to warrant some attention from devs.. 

Sux, though. Feel crippled without my USB and SD card. I guess the issue lie in either lacking of drivers or the new devkit.

---

### Post by lodravah on 2009-11-14
Update: Did an update yesterday, and now everything seems to be working again. Not sure which update it was, or if it was what did it. Today USB, bluetooth, and SD card works fine :)

---

### Post by lodravah on 2009-11-16
> **lodravah said:**
> Update: Did an update yesterday, and now everything seems to be working again. Not sure which update it was, or if it was what did it. Today USB, bluetooth, and SD card works fine :)

Well, everything stopped working at some point too yesterday. No USB of nothing. Fiddled around and found that the USB-support is broken by the initialization of my Bison webcam. 

[http://www.ubuntu.com/getubuntu/releasenotes/910#Brightness%20flickering%20on%20MSI%20Wind%20netbooks%20with%20KMS](http://www.ubuntu.com/getubuntu/releasenotes/910#Brightness%20flickering%20on%20MSI%20Wind%20netbooks%20with%20KMS)

Releasenotes regarding the webcam and disabling it. It worked for me, hope it works for you too..

---

### Post by montevjl on 2009-12-13
MEDION - BISON WEBCAM:(:(
It's been now a month I checked all foru,s, helps, dos & undos to fix my "bison" webcam  on a Medio ... Akoya.
The sys log shows the device as initialized, it's on dev0, but... it conflicts or the device cannot be accessed whatever I do.
I have all updated, kernel, karmic, uvnc, even tried to use a program called easycam 2 or something like, never managed to get the proper files to install, the product seems on a shelf waiting for a better season.
The ref. site say that Bison-Medion works fine, the another log says that it doesn't work (can remember).
One thing is sure ... the driver loads. But ?
I forgot... the cam shows in Skype but doesn't work.

---

### Post by no2498 on 2010-01-17
[montevjl]("http://ubuntuforums.org/member.php?u=721427")

do you have cheese or wxcam installed 
open the terminal type gstreamer-properties
click video try v4l1 or v4l2

if you look in the cheese help faq you find this


    * 6.1.&#8194;The video is sluggish/has a slow response. What can I do?
    * 6.2.&#8194;I have a Mac with iSight and a ATI graphics card, and the colors are weird.
    * 6.3.&#8194;My webcam works with gstreamer, but does not work with Cheese. What's wrong?
    * 6.4.&#8194;My webcam works with other programs such as Ekiga, Camorama, but not with Cheese. What's wrong?
    * 6.5.&#8194;Where does Cheese store my photos and videos?
    * 6.6.&#8194;My Quickcam Express doesn't work with Cheese...
    * 6.7.&#8194;"No Camera Found" Error Message
    * 6.8.&#8194;Which cameras are supported?

6.1.&#8195;The video is sluggish/has a slow response. What can I do?


      You may have set "ximagesink" (X Window System (No Xv)) as video-output.
      This means that your CPU is doing all the work. Change it to "xvimagesink"
      (X Window System (X11/XShm/Xv)) in order to let your graphics card do the work.
    


      To change this setting, run the gstreamer-properties
      command, click the Video tab
      and change the appropriate setting.

---

### Post by eggplant37 on 2010-01-17
I'll confirm this. I'm running 2.6.31-18-generic #55-Ubuntu SMP Fri Jan 8 14:54:52 UTC 2010 x86_64 GNU/Linux as my kernel. Attempts to mount the usbfs via these lines in /etc/fstab fail:

usbfs /proc/bus/usb usbfs auto 0 0
none /proc/bus/usb usbfs devgid=46,devmode=664 0 0

The message I receive is here:

mount: mount point /proc/bus/usb does not exist

Rebooting in 2.6.31-17-generic, everything works fine. Any ideas on what changed with 2.6.31-18-generic that disabled mounting usbfs?

---

