---
title: "Acer one (120gb/1gb) WLAN not working with 8.10?"
date: 2008-11-16
forum: Hardware
---

### Post by Henkster on 2008-11-16
I have just upgraded ubuntu 8.04 to 8.10 following the tutorial on [https://help.ubuntu.com/community/AspireOne](https://help.ubuntu.com/community/AspireOne) (on my aspire one 120gb/1gb version).
I had some issues with WLAN not working in 8.04 (madwifi step AND ndiswrapper would not work somehow allthough I could see my own wifi router in there)... so I thought upgrading would help... NOT! 
For example when I go to Network configuration (menu "System" in 8.10) I can not change the DNS (error: "connection not supported (read-only)"). Also I can not see any network icon in the taskbar..

However, if I would look in Konsole with ifconfig it seems that ip and such are correctly assigned to the wlan (settings that it got from 8.04 presumably).

So my question at this stage is...how can I assign network settings like DNS and so forth with the help with the Konsole? anybody?

I am becoming kinda frustrated over this... 
I am not computer ignorant.. but I am a bit of a Linux noob.. so excuse me if I just overlooked something obvious ... :)
tia for any answer!

---

### Post by Olivier2371 on 2008-11-16
Hi There,

I have an acer laptop. I am running ubuntu 8.04 and I have no problem. On my laptop I have a button to turn on or off my wireless.
The light is on when under windows vista to indicate that it is working.

Under ubuntu the light is off but the wireless adapter works fine.

Good luck.

ps: invilink is not a wireless adapter. You probably have a broadcom 43 wireless. Works fine and is detected under hardware drivers.
System-> Administration -> Hardware Drivers.

---

