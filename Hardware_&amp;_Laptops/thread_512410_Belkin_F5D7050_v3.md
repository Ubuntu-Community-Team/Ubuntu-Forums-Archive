---
title: "Belkin F5D7050 v3"
date: 2007-07-29
forum: Hardware &amp; Laptops
---

### Post by shift_06 on 2007-07-29
I'm having trouble installing this. 

I have tried:


> 1. First, go into Synaptic Package Manager, and search for "ndiswrapper-utils"

2. Install it.

3. Go into Terminal and go to the directory where the .inf file and .sys file(s) are for the driver. (I had the CD for mine, but if you don't have one, research how to find your driver.)

4. Type in "sudo ndiswrapper -i driver.inf", where "driver" is the name of the .inf file.

(example: My .inf file was called "netwg111.inf". Yours will probably be different unless you have a Netgear WG111 usb or laptop card.)

5. Type in "sudo modprobe ndiswrapper"

6. Type in "sudo ndiswrapper -m"

7. Go into Networking (System > Administration > Networking

8. There should be a choice that says "Wireless Connection". It should also say that it is inactive.

9. Click "Wireless Connection" and then click properties.

10. Click "Enable this connection" and fill out the information accordingly. Make sure that you have the correct network name filled out. The Key type will normally be Hexadecimal. I don't know what the WEP key is, but I left it blank and it works fine. My network is configured with DHCP, so I chose DHCP as mine. If your network is not configured with DHCP, select "Static IP Address" and fill out the information accordingly.

11. Internet should work at this point. If it doesn't, you probably don't have something configured right. Go back and check everything.

12. To make this enable itself every time you boot up, open a terminal and type in "sudo gedit /etc/modules".

13. Add "ndiswrapper" to the bottom of all the text. There! Wireless should be configured an ready to go!

And after step 10 I cant go on google.

I also tried 

> [https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_(Ralink_rt73_driver](https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_(Ralink_rt73_driver))

And I cant do the fromdos thing, it says 
> 
E: Couldn't find package tofrodos

---

### Post by shift_06 on 2007-07-29
Okay well i have managed to get fromdos installed manually. But i  using the tutorial at 

> [https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_(Ralink_rt73_driver](https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_(Ralink_rt73_driver))

Step 6 - Configure the network settings for the rt73 device i am stuck and this is what i pasted into the text document

> [INDENT]# rt73 wireless network device using DHCP
iface wlan0 inet dhcp
pre-up ifconfig wlan0 up
wireless-essid belkin54g
wireless-key f9fe82abc0
auto wlan0[/INDENT]

But when i go to step 7 it doesnt work

---

