---
title: "Gateway MX6027"
date: 2005-12-30
forum: Hardware &amp; Laptops
---

### Post by kumakun on 2005-12-30
Hey, all. After checking Linux on Laptops and the laptop test site here on the forums, I'm finding information for the Gateway MX6027 laptop lacking. I was wondering if anyone has this model and if they ran into any issues with it? I already expect WLAN to be a pain, but are there any other surprises I should be ready for?


Thanks!

---

### Post by Mikeynewbie on 2005-12-31
This may not help you much but if you cannot find info on the gateway laptop you have regarding support for ubuntu or anyother linux distro. the best suggestion I can give is to download the ubuntu live iso or anyother distro you want (live version).  the live cda can be booted from the cd you burn will not touch the hardrive and you  can see what works and what may need fixing.  you will need  a cd burning program like nero that can burn iso files but that should be easier than just checking the forums.

Hope that helps some?

---

### Post by kumakun on 2006-01-01
Yeah, I know I could do that. The idea though is to know about any potential problems before I bring the laptop home..

/K

---

### Post by noob_Lance on 2006-01-01
im running a gateway 6120GZ and so far... no probles except... wlan lol everything else works pretty much out of the box.. :D im happy with it. its been my main os for a few months for home and college :D

---

### Post by kumakun on 2006-01-01
And Is your Wlan actually up and running on that after using ndiswrapper or what have you, or is it still non-op?

/K

---

### Post by noob_Lance on 2006-01-01
yupp it worked right after ndiswrapper.. and now... the only propblem i have., my brother using the god damn cordless phone... damn 2.4ghz phones... now i have to go out of my way to get him a 5ghz phone just so he cant screw me up anymore lol :D.

if i couldnt get wireless to work... id shoot myself.. lol i only use wireless at home and at school no wired for me

---

### Post by gil on 2006-01-05
i'm running Ubuntu 5.10 on a Gateway MX4610m, and no problems so far, just the resolution, i want 1280 x 1024 and i only have 1024 x 768... You can find more about this laptop @ [http://gil.org.mx/index.php?gadget=StaticPage&id=4](http://gil.org.mx/index.php?gadget=StaticPage&id=4)

---

### Post by blueroyals on 2006-04-06
Hi There!
I had a problem installing Modem and Audio drivers on a MX6027. Actually i lost the recovery disc and i'm doing it manually. I did downloaded the Conexant_Audio_6.14.10.0565 and modem drivers from gateway website but when i'm trying to install its saying the installation will be done in the background but nothing happening there. I tried from the device manager as well but it's not detecting and still showing the yellow question mark.


Plz help me

many thanks 











[QUOTE=kumakun]Hey, all. After checking Linux on Laptops and the laptop test site here on the forums, I'm finding information for the Gateway MX6027 laptop lacking. I was wondering if anyone has this model and if they ran into any issues with it? I already expect WLAN to be a pain, but are there any other surprises I should be ready for?


Thanks![/QUOTE]

---

### Post by starfire1983 on 2006-04-07
I'm running it fine on a Gateway 7322GZ except the problems here: [http://www.ubuntuforums.org/showthread.php?t=156662](http://www.ubuntuforums.org/showthread.php?t=156662)

Wireless and correct power management will probably be the toughest things. Just install ndiswrapper and the graphical front-end for it, install the windows drivers for your wireless card (can snag them from an installation directory; .inf and .sys files).

---

### Post by duo007 on 2006-04-21
[QUOTE=blueroyals]Hi There!
I had a problem installing Modem and Audio drivers on a MX6027. Actually i lost the recovery disc and i'm doing it manually. I did downloaded the Conexant_Audio_6.14.10.0565 and modem drivers from gateway website but when i'm trying to install its saying the installation will be done in the background but nothing happening there. I tried from the device manager as well but it's not detecting and still showing the yellow question mark.


Plz help me

many thanks[/QUOTE]
i also have the same problem. icant install the drivers sound and modem into my mx6027. the gateway drivers are bs. and always say that they fail.i have tried to install in safemode and still no good. WILL SOMEONE PLEASE HELP ME PLEASE PLEASE. if you can help me install sound and modem drivers. i will paypal you 3bux. PLEASE PLEASE!!!!

---

### Post by duo007 on 2006-06-18
HI i have spoken with customer service and the only way to get the drivers working again is to have GATEWAY reinstall it for you. they reinstall windows and all the original applications. so that means you have to ship the laptop to them. they pay for shipping both ways. i got mine back up and going. ONLY WAY HOMEBOYS. make sure item is still under warranty.

---

### Post by kenny1215 on 2006-11-24
> **duo007 said:**
> HI i have spoken with customer service and the only way to get the drivers working again is to have GATEWAY reinstall it for you. they reinstall windows and all the original applications. so that means you have to ship the laptop to them. they pay for shipping both ways. i got mine back up and going. ONLY WAY HOMEBOYS. make sure item is still under warranty.

That's wrong. Maybe it was the case 5 months ago, but I had to search on Gateway's site for ALL the Conexant Audio drivers and try them one by one to find out the right one. The ones that worked are:

For Audio:
M360 / 6000 Series Conexant Audio Driver Version 6.14.10.0510
For Modem:
Conexant M360 / 6000 Series Modem Driver Version 7.18.00.50

I don't know why Gateway screwed it all up. But these drivers worked for me. Hopefully they do for you.

---

