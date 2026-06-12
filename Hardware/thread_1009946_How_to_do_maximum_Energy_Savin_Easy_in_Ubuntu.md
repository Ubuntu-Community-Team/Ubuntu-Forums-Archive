---
title: "How to do maximum Energy Savin Easy in Ubuntu ?"
date: 2008-12-13
forum: Hardware
---

### Post by starfly on 2008-12-13
Hello,

Ive got an new notebook, an Asus V57.

The notebook is in use on my University, and now ive got the question, what to do, to get easy the maximum energy Saving ?!

The book and the accu work now for 2 and a half hours.

Iam thinking about a skript on the desktop, starting it, activates the maximum saving mode automaticaly, without powertop etc.

Please give me some hints for energy saving with my Processor ( Pushing down the voltage ?! ) and the Graphics boars (NV 9650GT)...

So what can i do, until now i only activate powersave for the energyprofile and dimm my display ( Compiz is deactivated 4 saving )

Thanks and sorry for the bad english ;-)

---

### Post by Casper Hansen on 2008-12-13
If your CPU is supported there's an application which can controle your MHz. Just right-click on a panel and add item.

---

### Post by sdennie on 2008-12-13
You may want to take a look at this thread: [http://ubuntuforums.org/showthread.php?t=988309](http://ubuntuforums.org/showthread.php?t=988309)

---

### Post by starfly on 2008-12-13
The Saving tool isnt working well...no effects on my notebook...

Iam controling it via the Ubuntu own cpu scaling thing in the kicker ( little applet)

But all over, i need a tool, like in the threat above, but working ;-)

---

### Post by iggykoopa on 2008-12-13
you may need to adjust the default settings, by default it is very conservative. If you right click on the tray icon and set it to advanced, then left click on the tray icon it will bring up the configuration menu. Also you should download the newest version I just uploaded, it fixed a couple bugs in the older one.

---

### Post by starfly on 2008-12-14
Okay then please explain the Programm to me. 

When i edit the configure thing, the files stay the same one... The dsiplay isnt dimming, but xbacklight is installed.

My processor isnt set to powersave via the programm, how to do that ?

What up with "enabled" and "detected", what check ive got to do, to use this feature, or can i only use this one that are marked as detected ?

---

### Post by iggykoopa on 2008-12-14
sorry I haven't written the documentation for it yet as it's still in heavy development. With the display not dimming it may be because the gnome power management options are overriding the xbacklight settings, you can try turning that off. Setting your processor to powersave can actually take more power, it should be set to ondemand for the most powersavings( if the process is finished sooner than your processer can go back to sleep sooner, saving more power overall). The detected options are what the program finds for hardware or software that you have, it's only recommended to use the detected options, if you know you have some hardware that was not detected then let me know and I'll try to figure out why it's not working correctly. If something is detected then you can enable it for the gui to control it's settings (it needs to be both detected and enabled for it to manage it). I'm working on documentation for it, but I'm waiting until the features are pretty much set before I do to much with it.

edit: I just noticed you said you have an nvidia card..if your disabling compiz then don't worry about the nvidia powersaving options in the script, they only apply if your running compiz. Also I'll be adding an option to configure your xorg.conf for nvidia powersaing soon...jsut have to figure out how I want to do it.

---

