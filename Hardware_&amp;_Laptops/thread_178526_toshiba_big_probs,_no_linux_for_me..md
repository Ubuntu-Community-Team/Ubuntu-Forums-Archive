---
title: "toshiba big probs, no linux for me."
date: 2006-05-17
forum: Hardware &amp; Laptops
---

### Post by wikman on 2006-05-17
i tried to install ubuntu 5.10 on a toshiba satellite a100 and everything went well while installing but when ubuntu start it crashes and i get a xwindow error message.  looks like ubuntu cant start my graphic card...

my laptop: 
toshiba satellite A100
celeron M 1.7 ghz
ati radeon xpress 200m with 128MB DDR shared video memory
TFT Active Matrix LCD display 15.4” Wide XGA TFT 1280x800 (16:10?)

i went and download the ati driver for linux and burned it on a cd and i booted in "safe mode" and got the "root@username: ~#" console to try to access the dvd drive to install the drivers by executing the ".run" driver file but no luck. anyway i dont know where to start... boohoo... i want ubuntu but i am a newbie at linux... any simple step-by-step guides outthere?

---

### Post by Sutekh on 2006-05-17
The problem probably lies with the open source **ati** drivers that come with Ubuntu by default.  Theyare foten the cuaseof this sort of problem.



Does this error leave you at a command line where you can log in with your username and password?
 


If so, you can use this command to change the video drivers temporarily to the **vesa** drivers, which seem to be a general fix-all driver.
 ```
sudo dpkg-reconfigure xserver-xorg
``` - when prompted for a password, use your users password. 
 
- this command will reconfigure the X server (the GUI), you will be asked a long string of questions regarding the input devices of your PC; your keyboard, mouse and monitor. If you don't know what you should answer to these questions go with the default/suggested ones.
 
  - the important step is when you are asked to choose the video card driver for the X server choose **vesa**
 
  - once you are done use this command
 ```
sudo /etc/init.d/gdm restart
```  - this will restart the GNOME Display Manager, and start the GUI.



  If you get the graphical interface working with the **vesa** drivers, you could look into installing the Official ATI drivers, through one of these means.  
 
 You can try either this HOWTO
  
  [Ubuntu Document Storage Facility - Install ATI Driver]("http://doc.gwos.org/index.php/Install_ATI_driver")
  
 or look into installing EasyUbuntu (for GUI install of ATI drivers and loads of other stuff)
  
  [Ubuntu Forums - Easy Ubuntu v2.2]("http://ubuntuforums.org/showthread.php?t=64629")
 
 [URL="http://www.ubuntuforums.org/showthread.php?t=75074"]
[/URL]

---

### Post by wikman on 2006-05-18
what a fast response! and ... dude...  it worked!!! thanks man!

i will know try to install the ati drivers!

thanks a million Sutekh!

wikman

:D

---

### Post by Sutekh on 2006-05-18
NP wikman,  I'm glad things are working. 

Those vesa drivers rarely fail.  I hope you will be able to get the ATI drivers installed too.

---

