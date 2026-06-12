---
title: "Install Broadcom Wireless LAN driver for ubuntu 10.10"
date: 2010-11-24
forum: Hardware
---

### Post by kwaK1983 on 2010-11-24
Hi guys,
 
I'm a complete newbie to Linux/ubuntu to start with ;-)
First off all I was tired of random crashes from Windows on my Netbook, so I wanted to test the critically acclaimed ubuntu.
I went to [http://www.ubuntu.com/netbook/get-ubuntu/download](http://www.ubuntu.com/netbook/get-ubuntu/download) and followed the steps to make a USB-stick (no CD-ROM drive attached).
So far so good, plugged the USB-stick in my Netbook and clicked the Install Ubuntu-button.
After the install everything seemed to work fine (as far as a noob like me could tell) except browsing the internet.
UPDATE: In the top-right corner there's an wifi-icon saying Wireless Networks --> Device not ready (firmware missing).
I have no clue on where to download the drivers/firmware for the Broadcom Wireless LAN Driver for ubuntu as opposed to Windows([http://h10025.www1.hp.com/ewfrf/wc/softwareDownloadIndex?softwareitem=ob-68699-1&lc=nl&dlc=nl&cc=nl&os=228&product=3946725&sw_lang=]("http://h10025.www1.hp.com/ewfrf/wc/softwareDownloadIndex?softwareitem=ob-68699-1&lc=nl&dlc=nl&cc=nl&os=228&product=3946725&sw_lang")).
 
Please help, cause I want to give it a fair shot :p

---

### Post by garvinrick4 on 2010-11-24
System/Admin to Hardware drivers.
If not you have to tell us what your wifi card is.
I imagine you have a Dell?

---

### Post by kwaK1983 on 2010-11-24
Thanks, I'll have a look in the netbook when I'm back at home.
Netbook is HP Compaq Mini 735ED btw.
It was visible when trying to download the Windows-driver from the link stated, but didn't make that too clear I guess ;-)

---

### Post by kwaK1983 on 2010-11-25
When I go to Applications --> System I don't see Admin nor Hardware Drivers :(
I plugged in a networkcable and went to Applications --> Additional Drivers.
A new screen comes up with "Searching foravailable drivers" and then the text "No proprietary drivers are in use on this system."
Followed by alot of text and 2 radio buttons and Broadcom B43 wireless driver and Broadcom STA wireless driver.
And then a radio button with "This driver is not activated" and a Activate-button.

When I click on of the 2 and then Activate and Authenticate with the right password, I get this error: 
SystemError: installArchives() failed

Also I ran the Update Manager (158 updates --> 166.0 MB) but still no driver for my built-in Wifi.

 
Ps updated the error in my OP.

---

### Post by garvinrick4 on 2010-11-25
There are a ton of threads on broadcom wireless, lets find one.
Look in System to Administration to synaptic and type in broadcom
I believe there is broadcom-sta-common package

---

### Post by garvinrick4 on 2010-11-25
[http://ubuntuforums.org/showthread.php?t=1604868&highlight=broadcom](http://ubuntuforums.org/showthread.php?t=1604868&highlight=broadcom)

---

### Post by kwaK1983 on 2010-11-29
> **garvinrick4 said:**
> Look in System to Administration to synaptic and type in broadcom
I believe there is broadcom-sta-common package

Thanks, I got the job done now =)
Couldn find the Administration-button, but System --> Synaptic Package Manager did the trick for me!

---

