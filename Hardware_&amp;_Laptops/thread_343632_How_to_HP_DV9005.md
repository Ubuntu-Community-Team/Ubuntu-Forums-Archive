---
title: "How to HP DV9005"
date: 2007-01-21
forum: Hardware &amp; Laptops
---

### Post by rowee on 2007-01-21
I purchased an HP dv9005us about a week ago. This laptop has some really sweet  specs but has been a little difficult at times so I wanted to share my my successes. My explanations will be very terse, but it should be enough to get all but the newest newbie on the right track.

The Ubuntu live CD booted OK so I did an install with a complete hard drive wipe.

**1) Blank Screen After First reboot**
Add the following options to the kernel's boot command "apm=off noapic".
You can permanently add these by editing the end of the /boot/grub/menu.lst file and editing the appropriate kernel boot line.

**2) Won't boot into rescue mode**
The kernel will report that the TSC offset of the two cpu's is off. Add the following options to the rescue boot command "clock=tsc". You can add this option to the end of the  /boot/grub/menu.lst as well.

**3) NVidia drivers**
I found the following link useful: [http://ubuntuforums.org/showthread.php?t=263851](http://ubuntuforums.org/showthread.php?t=263851). I followed option 1 for the NVidia drivers.

**4) Screen Resolution**
After rebooting my system still didn't understand the display resolution this computer is capable of, you need to update /etc/X11/xorg.conf. In the Screen section of the file you will see the resolutions that X server understands; note that there is a set of resolution settings for each depth. Add "1440x900" to each depth.


**5) Wireless Networking**
Still have not idea how to get the built in WiFi card to work despite the fact that iwconfig sees the hardware, so I installed a LinkSys WUSB54GC. The WUSB54GC is a hot pluggable usb network adapter; I found the following link useful: [https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_(Ralink_rt73_driver](https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_(Ralink_rt73_driver))

Hope this helps someone!

---

### Post by Ephack on 2007-01-26
:KS Thanks a lot Rowee! You saved my Ubuntu! :D 

I have exactly the same notebook as you. I had installed Ubuntu, but it crashed 4 times out of 5 when booting. The apm option seems to fix that issue. 

And I couldn't also get the right screen resolution: the method you're linking to worked great! The drivers on the official depots seems to be too old for this card (which isn't so new).

Next step: the wifi! I could make the card work (the blue LED wents on), but Gnome-network manager doesn't find the network. I will try to find out why when I am back on my own network. Probably a WEP issue...

So, again, thanks for having posted that!

---

### Post by Ephack on 2007-02-17
So, it&#347; not everything perfect, but wifi works now!

I used this tuto, specific to the wifi card in this laptop:
[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29)

---

### Post by slackmaster on 2007-06-10
Hello,

We all have the same computer.  I'm thinking of installing the 64-bit Ubuntu.  Has anyone tried this for the DV9005?  How did it turn out?

I'm hesitant to install Ubuntu on my one last Windows computer in the network.  I've never used the migration assistant tool.  How comprehensive is it?  I'm mainly concerned about Outlook 2003 folders.  
I also am not sure how to restore files backed up with windows backup.  I also have a number of zip folders that I can't seem to unzip into ubuntu.   All these backups are on an external HD.   I want to unzip the entire backup at once and then search for particular extension types rather than go through everything file by file.  

I have one windows media center  computer which will not find the ubuntu server printer, unlike my Windows Professional XP laptop.   My media center machine can access the external HD through Ubuntu server, but Ubuntu cannot access any files on media center even though  I've allowed sharing of the entire C drive temporarily. 

Ubuntu sees the media computer on the network but won't give me access.  The media computer see the external HD connected to the Ubuntu server but the server won't let the pavilion alter files.  
Thanks for any tips ahead of time.

S

---

### Post by ozzyprv on 2007-12-10
> **Ephack said:**
> So, it&#347; not everything perfect, but wifi works now!

I used this tuto, specific to the wifi card in this laptop:
[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29)

Thank you Ephack, I followed the link you posted. I used section 1.3 of [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty)

My laptop is a dv9005ca

Still working on getting the WPA-PSK to work.

Edit: 
~WPA issue is SOLVED
~wireless does not work after restart unless I run modprobe bcm43xx

---

