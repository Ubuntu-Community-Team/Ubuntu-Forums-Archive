---
title: "intel 965 graphics and realtek 8189b wifi issues"
date: 2008-05-14
forum: Hardware
---

### Post by Rudedawg on 2008-05-14
So, I'm getting back into Linux after a long time away and I've heard a ton of great things about ubuntu. I threw a spare HD into my newer gateway laptop (1621 i think) and installed hardy. Love it so far aside from 2 issues: 

1) Wifi. I have the realtek 8189b internal card as was listed when running lsusb. I've read and tried all the methods listed in the forums for the issue with the realtek 8187b chipset. I also saw that some of those fixes were for 818X so I figured they would work for my card. I got the card installed using ndiswrapper and it will see several wireless networks, including my own. I can connect to my wifi, but I receive no signal or IP. I have WPA1 using TKIP encryption on my router. When I installed using ndiswrapper, I used the .inf file from winXP instead of win98, so I'm not sure if that is the issue. If it is, someone please tell me how to uninstall the one I used from winXP. 

2) screen resolution. I can set the background to use the whole screen in 1200X800 res, but the bars only go 3/4 of the way across the screen and the bottom one is not flush with the bottom of the screen. I also have some strange secondary display in the resolution settings. It's the Intel 965 graphics chipset.  

Any input on resolving either of these common problems would be greatly appriciated!

---

### Post by ubuntu-freak on 2008-05-14
I can offer some advice for your screen placement issue.
 
You're resolution is correct, but the desktop isn't displayed correctly? Press Alt F2, type "gksudo displayconfig-gtk" and your password when prompted, then try selecting an alternative monitor. If "Generic" is already selected, then I'm surprised you're having such issues, especially with an Intel graphics chipset.
 
Nathan

---

### Post by rockin_goliath on 2008-05-14
you might try the new "Screen Resolution" utility in System - Preferences - Screen Resolution. It's a nice gui for xrandr. You hay also try adding your correct resolution to your xorg.conf file.

---

### Post by ubuntu-freak on 2008-05-14
> **rockin_goliath said:**
> you might try the new "Screen Resolution" utility in System - Preferences - Screen Resolution. It's a nice gui for xrandr. You hay also try adding your correct resolution to your xorg.conf file.

 
That menu entry runs the command "gnome-display-properties". The GUI for RandR (URandR) isn't ready yet, but will hopefully be added in 8.04.1 and is more powerful than gnome-display-properties. 
 
Nathan

---

### Post by Rudedawg on 2008-05-14
Awesome. I'm going to try those out when I get home from work.  

Any particular reason why I would have multiple displays showing up in the resolution properties? The second display (the unknown display) has a max resolution of 1024X768 and a refresh rate of 30Hz while the 15.4 laptop monitor has a max res of 1200X800 and a refresh rate of 60Hz.

---

### Post by Rudedawg on 2008-05-15
I was able to change the video card to the intel 965 (which then displays the 810i...), But I get a low color setting error everytime I boot up and the load screen is highly distorted. Everything looks great once I get to the login screen however. The screen resolution is perfect.  

Anyone have any clues about the wireless issue?

---

### Post by ubuntu-freak on 2008-05-15
> **Rudedawg said:**
> I was able to change the video card to the intel 965 (which then displays the 810i...), But I get a low color setting error everytime I boot up and the load screen is highly distorted. Everything looks great once I get to the login screen however. The screen resolution is perfect.  

Anyone have any clues about the wireless issue?

 
I've no real experience with wireless. Search ugm6hr's posts, that user is always helping with wireless issues.
 
You selected a different driver how? Intel graphics chipsets use the "intel" driver now, instead of "i810". It wouldn't let you just change the resolution?
 
You may be able to fix your distorted usplash, by installing Start-Up Manager: 
 
**sudo apt-get install startupmanager** 
 
You will find it in System > Administration. Try changing the bit depth to 8.
 
Nathan

---

### Post by Rudedawg on 2008-05-15
I used Alt-F2 and ran gksudo displayconfig-gtk as was suggested. There was 2 tabs. One for "Screen" and the other was for "Graphics card". It actually lists 2 graphics card, both of which are set to vesa generic. If you click one, you're brought to a screen where you can choose a graphics card driver. You can choose by name or by model. Under model, I selected Intel and then 965 as the model. After doing that, it instantly changes it to 1810-intel intergrated graphics.  

Under screens, I somehow have 3 listed: Screen 1, Screen 2, and Screen 1 again.  

My Wireless works now, but it will only get signal strength from unsecured networks. I have to look for a thread about WPA in order to be able to connect to my wireless.

---

