---
title: "Toshiba Satellite M505D-s4970 Wireless and Fan Control"
date: 2010-06-01
forum: Hardware
---

### Post by Bearcrusher on 2010-06-01
[SIZE=2]Hello,
This is my first issue I've had with ubuntu in the two years I've been using it that I can't seem to figure out... I'm not necessarily a linux or ubuntu expert but I can for the most part get around in it

I dual boot ubuntu and windows 7 currently

The first problem I'm having is with the wireless card... Ubuntu will not recognize the card exists on the laptop. Windows 7 device manager says its a[/SIZE][SIZE=1][SIZE=2]realtek RTL8191SE Wireless... I have searched around the web and have found problems with this device but I can not find a solution. when I look up the networking connections it comes back as wlan0: Error..... Device Not Found (something along those lines... I can't remember since I currently don't have my laptop in front of me)

Second problem I have with this laptop is the fan control... The fan on my laptop seams to kick on only when its a couple degrees from overheating... (its uncomfortable to even type with the laptop.) when the fan does come on it comes on in short bursts for a couple seconds then settles back down to heat up again... If anyone knows of a way to control my fan, please let me know..


If someone knows a solutions to either problem, please let me know.

Thanks!

[/SIZE][/SIZE]

---

### Post by Jorge Alban on 2010-06-13
Having the very same issue with a friends Toshiba U505 Laptop. The fan ONLY comes on AFTER returning from suspension... She forgets the suspension trick, lets the laptop all alone and a couple of times has returned to a computer that shut itslef off from overheating... Ouch !

Theres still no definitive fix. Hoped the 10.04 kernel would fix this... and it didnt. Tried Linux Mint and the same thing happens (someone reported Mint took care of this). Here is  a through explanation of the problem (item No 3 FAN ISSUES):

[http://michaelminn.com/linux/toshiba-u505/](http://michaelminn.com/linux/toshiba-u505/)

Suspending the machine by pressing FN + F3, and then again to return from suspension with the fan on, seems the best workaround for now, but it must be done everytime the laptop is turned on...:frown:

[http://art.ubuntuforums.org/showthread.php?t=1420247&highlight=toshiba+U505+fan&page=2](http://art.ubuntuforums.org/showthread.php?t=1420247&highlight=toshiba+U505+fan&page=2)

In the above thread a user by the name of Ashima posted a fix that seems to work on some models but others are just stuck with FN + F3...

Jorge AD
[http://artenemo.org](http://artenemo.org)

---

### Post by Datar on 2010-06-30
Well... For the wireless the solution is download the driver from the page of realtek, and it works... Here is the link

[http://www.realtek.com.tw/Downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true](http://www.realtek.com.tw/Downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true)

But for the fan I couldn't find a solution, and suspending with FN+F3, suspend the computer but when it turns on the screen doesn't display anything :( just the screen stay black like when it's turn off, if someone know how could be the error please tell me...

I hope that this could help you :p

---

### Post by Facem on 2010-09-16
Fan control is probably an acpi issue.  You might try modifying /etc/default/grub.  Adding "acpi.power_nocheck=1" to the cmdline options (and subsequently running update-grub and rebooting) fixed the fan issue on my Toshiba M505D-s4930 using 10.04 Lucid.

---

### Post by Facem on 2010-09-17
For the wireless issue, if you are using 10.04 Lucid, it comes with the drivers for realtek devices, but they aren't automatically associated with the device for some reason.  I'm not sure if this will fix your problem or not since my problem was a little different.

Running "lshw -C network" listed my realtek device (8192 (rev 01)) as "Disabled" and configured with an "rtl819xE" (configuration= ... driver=...) driver.  "lsmod | grep r8" showed only r8169, so I used "modprobe r819" and tab-complete to show me the available applicable modules.  It returned r8192_pci, r8192se_pci, r8192s_usb so I used modprobe r8192_pci (I'm guessing you would use the se version).  Then I added "r8192_pci" (again, you would add your module name) to /etc/modules/ so it would load the module on boot.  Upon a reboot, I had working wireless!

---

