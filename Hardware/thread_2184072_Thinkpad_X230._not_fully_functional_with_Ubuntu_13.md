---
title: "Thinkpad X230. not fully functional with Ubuntu 13.10 64 Bit?"
date: 2013-10-27
forum: Hardware
---

### Post by germanix on 2013-10-27
Took delivery og my new Thinkpad X230 yesterday and installed Ubuntu 13.10. Not the "runs perfectly out of the box" experience I had hoped for. Having the following issues:
1. F8 and F9 buttons for dimming and brightening the screen not functioning. (funny thing is I first install the 32 bit version of the software and then it worked, but not with the 64 bit version)
2. The trackpad as well as the trackpoint is not functioning. Have to work with a mouse? Could be they are switched off somewhere but I dont know where to check? (also worked under the 32 bit version of Ubuntu)

Any help in solving these issues will be greatly appreciated.

Found an answer for the fingerprint reader but rest still outstanding. Both the trackpad and the trackpoint are activated in bios

---

### Post by germanix on 2013-10-28
Update: Something must have gone wrong with the drivers I think? I again installed Ubuntu 12.04 (32 bit) on which the trackpoint was both working before, but it now does not work there either. I also tried it on mint 15 with the same results. Users of this machine all claim that everything works out of the box when installing Ubuntu, and at first it did but then stopped working. Searching for answers on the internet to this problem it is suggested to re-install the drivers from the Lenovo site but there are no linux drivers to be found there nor the model number of my specific machine. I am at a loss how to solve this problem.
Any ideas, anybody?

---

### Post by germanix on 2013-10-29
I have now realised that the touchpad/trackpoint is not detected at all. 
I tried the following which I found on :
[https://help.ubuntu.com/community/synapticsTouchpad](https://help.ubuntu.com/community/synapticsTouchpad)

Determine whether a touchpad has been detected

To check if a touchpad has been detected open a terminal and check the input device list given by this command:

xinput list

Only the mouse, keyboard and some extra buttons are detected but no trackpad or trackpoint. Is this a hardware or software problem? Unfortunately this site does not tell you what to do when the trackpad is not detected and how to fix this! Any ideas?

---

### Post by cpbl on 2013-11-13
Wow, that sounds worse than my experience. 
I think the trackpad defaulted to "off", possibly.
Under system settings,  you can turn it on under mouse/trackpad. In any case, mine worked immediately or after doing that.
The trackpoint also worked fine.

I suspect whoever said to install drivers was thinking about a different, proprietary operating system.

However, I'm not claiming the X230 (Tablet, in my case) worked out of the box:
[http://cpbl.wordpress.com/2013/10/24/ubuntu-13-04-and-13-10-on-lenovo-x230x230t-convertible-tablet/](http://cpbl.wordpress.com/2013/10/24/ubuntu-13-04-and-13-10-on-lenovo-x230x230t-convertible-tablet/)

Did you get your fingerprint reader working?

---

### Post by germanix on 2013-11-14
I tried just about anything I could think of, but could not get it to work. I returned the machine on the assumption that a hardware problem existed and had it replaced. The replacement machine was delivered and trackpad/trackpoint worked out of the box. Still cannot get the buttons for dimming the screen to work but as I can do that over "system settings" I can live with it. Did find a driver for the fingerprint reader but did not install it. Do not realy want to use it. My laptop is on a docking station at home 90 % of the time. Biggest problem I found with the X230 and Ubuntu 12.04 and 13.10 combination is getting the external monitor to function properly. It works fine but when you close the laptop lid the external monitor goes black. Checked to ensure that the power settings reflect to "do nothing" when closing the lid but same issue. Found out by mistake that when this happens you need to do a left click on the mouse to get the picture back on the external monitor. Should not have to be but there you are. I do not have this problem when booting KDE as in Kubuntu or openSuse. Keyboard backlight works fine. Running Ubuntu 13.10 as sole OS at the moment. Looks good but not very stable. Most stable and most functional OS on my machine I found to be openSuse but also Kubuntu does a nice job. Only problem with openSuse is the build in speakers of the external monitor wont work, it only plays on the laptop speakers and I could not fox that. Here Kubuntu had no such problem. Strange how some things work with Kubuntu but not Ubuntu. Do these guys not talk to each other?
In general however I am very happy with the X230.
Thank you for responding and the information you provided.

---

