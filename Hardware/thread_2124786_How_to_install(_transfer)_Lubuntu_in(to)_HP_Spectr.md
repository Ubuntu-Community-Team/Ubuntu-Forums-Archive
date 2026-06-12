---
title: "How to install( transfer) Lubuntu in(to) HP Spectre xt 13''"
date: 2013-03-12
forum: Hardware
---

### Post by zsstie on 2013-03-12
[SIZE=3]**Howto install( transfer) Lubuntu in(to) HP Spectre xt 13''**[/SIZE]


Recently bought one ultrabook HPSpectre XT 13''  , couldn't get used to Windows 8 and decide to stick with Lubuntu which been put on my Acer aspire one D255e netbook. 




As my place is quite rural, post delivery and internet broadband is always a problem for me. At the moment I use mobile broadband 2GB data plan, every time when I got something to download , I just can't make a heart to get its traightaway from internet, big stuff like a .iso file or a important hug patch I will get them in public library when I am off from work.Limited situation leads me to transfer Lubuntu onto my brand new ultrabook. 


My installation plan is roughly as follow: 


**1** copy the windows 8 64bit product key on a piece of paper for the possible future use 


**2** backup all my personal documents in /home partition to a NTFS partition 
 
**3** empty all the files in Downloads Music Document Picture folders 
  
**4** clear up all the cache files,trash can, temporary folder and anything is not useful(probably need to get the root authority by run ****sudo pcmanfm****in Terminal ), or use Bleachbit to delete rubbish. 


**5** use Ucloner 10.10.1 to back up all my Lubuntu 12.04 to a squash file (.squashfs) like Ghost in windows. 
might need install python-vte (**sudo apt-get install python-gtk2 zenity python-vte**)  and squashfs-tools  ( **same as above:sudo apt-get install squashfs-tools**), Check the instruction [FONT=Droid Sans Fallback][SIZE=2]&#35828;&#26126;[/SIZE][/FONT].txt out. 
****cd  /ucloner/porgram/**,  then**sudo ./ucloner_gui.py**** 
you will figure it out in the GUI window, I prefer to use a separated  partition which is neither / nor/home as destination , a sole ntfs path or  one removable hard disk will do. 


Another choice is Clonezilla, made by Taiwanese, but not very friendly to use, you can **not ** restore into a smaller partition with image file which is backup from a bigger partition. 


**6** boot my hp spectre xt 13 with pressing ESC button,go F10  for bios ,set up to legacy support mode to disable UEFI mode, save and reboot, pressing F9 to select lubuntu live usb as the boot disk. 


**7** use live usb (can be made by**Unetbootin** in *buntu or **yumi-multiboot-usb-creator** in windows) to erase all the stupid  windows' and hp rubbish in my 128GBSSD( occupy nearly 60GB data!) then get the partitions sorted by **Gparted**,sda1 20GB for /, sda2 4GB for swap, sda3 50GB for/home,rest of the disk for NTFS. 


**8** use Ucloner again( do not extract to a Fat32 partition, extract to  a NTFS or a ext4 partition which you have authority to execute), restore all the data from the .squashfs   you saved. choose the proper path for your own use. 


**9** restart, looks everything in my acer netbook is coming back, no more blue screens in linux world! 
you can copy all your personal documents though samba.




 
[SIZE=3]**Modify few bugs in Lubuntu 12.04**[/SIZE]


After playing around for a while, found quite a few unacceptable  bugs. My machine is too new to suit the Lubuntu 12.04. and the frustrating thing is you can find nothing useful about linux on the damn hp website. 

update to 3.5.0 kernal first!

old kernal may casue freeze by no reson as the new ivy bridge bugs, update to 3.5.0 can solve quite  a few problems  on this new hardware.


sudo apt-get install linux-generic-lts-quantal xserver-xorg-lts-quantal



**#1** ***touchpad has no right click ***


The easiest way I find on Ubuntu forum is : 
 
1. Create 51-clickpad.conf in/etc/X11/xorg.conf.d directory. Note that xorg.conf.d directory did not exist for me so I had to make the directory. 
2. Put the following lines in51-clickpad.conf 


[FONT=Nimbus Sans L]Section"InputClass" [/FONT]
[FONT=Nimbus Sans L]Identifier"Default clickpad buttons" [/FONT]
[FONT=Nimbus Sans L]MatchDriver"synaptics" [/FONT]
[FONT=Nimbus Sans L]Option"SoftButtonAreas" "50% 0 70% 0 0 0 0 0" [/FONT]


[FONT=Nimbus Sans L]EndSection[/FONT]


Actually the conf  from the forum is longer than this, and I found the extra lines just not work very well on Hp spectre xt 13'', and in the option ''softbuttonArea'' , I change the right click area to 70% above instead of the original 82%.


logout then login again, the rightclick is back.  another clickpad problem is the left top function, I haven't figure it out yet. hopefully I can find the newest patch for this bug. 


**#2 Beatsaudio only have two front speakers working **


1  check this link to install and update  alsa to  v1.0.25 


[http://droid-hive.com/index.php?/topic/919-how-to-beats-audio-with-alsa-dv7-eoslubuntu/](http://droid-hive.com/index.php?/topic/919-how-to-beats-audio-with-alsa-dv7-eoslubuntu/)


2 download the **hda-jack-retask** deb package(for intel hda) from 
[https://launchpad.net/~diwic/+archive/hda/+packages](https://launchpad.net/~diwic/+archive/hda/+packages)


3 after installation, ****sudo hda-jack-retask**** in terminal , select codec IDT 92HD99BXX and select show unconnected pins 


4 make sure the configuration is as follow: 


pinID : 0X0a  override  microphone 
pinID:  0X0b  override  headphone 
pinID:  0X0c  override  microphone 
pinID:  0x0d  override  internal speaker 
pinID:  0x0f   override  internal speaker 
pinID:  0x11  override  internal mic 


apply now, may pop out  a error window,ignore it and install boot override 


5 reboot, open **alsamixer** in terminal, make sure speaker and speaker1 is not on mute and the two capture is on as well. 


6 now,play your favourite music, rock out! 


Probably you need to try  snd-hda-intel model=ref option ( **gksu gedit /etc/modprobe.d/alsa-base.conf**),good luck. 


**#3 ** **optimize ssd for Lubuntu **


follow this link:[https://sites.google.com/site/easylinuxtipsproject/ssd](https://sites.google.com/site/easylinuxtipsproject/ssd) 


**#4**  **card reader driver **


lspci in terminal: 


02:00.0 Unassigned class [ff00]:Realtek Semiconductor Co., Ltd. Device 5229 (rev 01) 


grub the driver from : 


[http://www.realtek.com.tw/Downloads/downloadsView.aspx?Langid=1&PNid=15&PFid=25&Level=4&Conn=3&DownTypeID=3&GetDown=false](http://www.realtek.com.tw/Downloads/downloadsView.aspx?Langid=1&PNid=15&PFid=25&Level=4&Conn=3&DownTypeID=3&GetDown=false)


extract then go into the path where you extracted by cd ***/rst5229 


Build Steps 
=========== 


1) make 
2) make install 
3) depmod 
4) reboot your computer 


Note: Root privilege is required instep 2 and 3 


**#5 intel 6235 wireless is too slow**


lspci in terminal 


Network controller: Intel Corporation Centrino Advanced-N 6235 (rev 24) 


Lots of people said there is something wrong with the driver, and disabled 11n will solve the bug, but I don't think so. if you use the wireless with the AC power plugged in,everything is good. Once laptop runs on battery, the wireless will be bloody slow, at this time if you ping the router in your home, the latency(communication delay) is above 50ms sometimes, what the....!Definitely the power management is the bugger. 


Temporary solution is  run **sudo iwconfig wlan0 power off** in the  terminal, but you also can turn it off by create a  wireless script to  turn it off permanently: 


**cd /etc/pm/power.d**    (if itdoesn't exist,** sudo mkdir /etc/pm/power.d** to create one) 


create a wireless file and type two lines in: 


[FONT=DejaVu Sans]#!/bin/sh[/FONT]
                    
[FONT=DejaVu Sans]/sbin/iwconfigwlan0 power off [/FONT]
 
save and reboot, problem solved! 


**# 4GB memory support in 32bit lubuntu**

once you updated to 3.5.0, you dont have to do this:
[B]sudo apt-get install linux-generic-pae linux-headers-generic-pae
[/B]





I just gather all the information together, this is pretty much most of  issues about hp spectre xt 13''in Lubuntu 12.04. Hopefully this can help somebody.

---

### Post by Geomad89 on 2013-03-13
hi, i have bought too an hp spectre xt and I want to install ubuntu, I would like to ask you if the problem is the same of lubuntu. And another thing, how change the battery life with lubuntu?

PS : Sorry for my bad english :)

---

### Post by zsstie on 2013-03-13
I think it could have the same problem on ubuntu 12.04.. I din't give it a try on 12.10, but I believe you will work it out.

Battery can last about 4-5 hours with Lubuntu.

---

### Post by Geomad89 on 2013-03-16
ok thanks

---

