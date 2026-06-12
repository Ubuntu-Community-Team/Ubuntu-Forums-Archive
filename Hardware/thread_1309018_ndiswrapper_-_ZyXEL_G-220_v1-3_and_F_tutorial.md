---
title: "ndiswrapper - ZyXEL G-220 v1-3 and F tutorial"
date: 2009-11-01
forum: Hardware
---

### Post by Anthenima on 2009-11-01
Okay, Let's get started. This tutorial for your first cup of Ubuntu shows you how to install ndiswrapper, get the correct drivers for your ZyXEL G-220 v1-3 F Device, and setting up a connection to your WiFi network.

[B][I]Installing ndiswrapper
[/I][/B]   
[LIST]
[*]Start Add/Remove Programs or Ubuntu Software Center.
[*]Search "ndiswrapper" and install it.
[*]We're done with ndiswrapper for now.
[/LIST]
 [B][I]Getting your ZyXEL G-220 Drivers
[/I][/B]
[LIST]
[*]For G-220 v1 [Click here]("ftp://ftp.zyxel.com/G-220/driver/G-220_3.0.0.zip")
[*]For G-220 F [Click here]("http://us.zyxel.com/upload/download_library/G-220F_2.0.zip")
[*]For G-220 v2 [Click here]("http://us.zyxel.com/upload/download_library/ZyAIR_3_1_0_b4_6112.zip")
[*]For G-220 v3 [Click here]("http://us.zyxel.com/upload/download_library/Driver.rar")
[/LIST]
[I][B]Extracting your Driver
[/B][/I]Linux doesn't support RAR out of the box, so we must enable it.

[LIST]
[*]Open Terminal and type "sudo apt-get install rar unrar" Without the quotes, of course.
[*]Go to the directory you downloaded your diver, right click and select extract here.
[/LIST]
[I][B]Configuring ndiswrapper
[/B][/I]
[LIST]
[*]Find the application "Windows Wireless Drivers" under System
[*]Click on "Install New Driver"
[*]Navigate to the folder where your driver is extracted
[*]Find the .INF file and open it
[*]Close ndiswrapper
[/LIST]
Congratulations. You set up your ZyXEL G-220 device. Go to the network icon in the panel and click on it. Find your WiFi hot spot and connect. :D

---

### Post by sp2000 on 2011-01-10
Thanks so much!! 
...However, I've two wireless adapters that we're sharing in my house.  

1- a Linksys WUSB54GC (this loads with no problems / no NDISWRAPPER necessary)
2- ZyXEL G220 V-3

When I switch from the Linksys to the ZyXel I have to re-install the driver for the ZyXEL thru NDISWrapper in order for it to work(again).

Of, course I'm taking permanent usership of (1) to avoid this, however, do you have any ideas how to debug This?:confused:

---

### Post by Anthenima on 2011-01-31
> **sp2000 said:**
> Thanks so much!! 
...However, I've two wireless adapters that we're sharing in my house.  

1- a Linksys WUSB54GC (this loads with no problems / no NDISWRAPPER necessary)
2- ZyXEL G220 V-3

When I switch from the Linksys to the ZyXel I have to re-install the driver for the ZyXEL thru NDISWrapper in order for it to work(again).

Of, course I'm taking permanent usership of (1) to avoid this, however, do you have any ideas how to debug This?:confused:

I have no clue :(

---

