---
title: "HOWTO:  Use your iPhone or iPod Touch as a touchpad"
date: 2008-06-18
forum: Hardware
---

### Post by all2ez on 2008-06-18
I recently read about using the iPhone as a touchpad using the Touchpad Pro app, but was unable to find any help setting it up to work with Ubuntu.  The Touchpad Pro website only includes instructions for controlling Windows and Mac OS X.  After experimenting a little bit, I found that it was surprisingly easy to get working using the Ubuntu default remote desktop server, vino.  So I decided to make my own how to guide so other people don't waste a bunch of time trying things that don't work (like I did).

For anyone not familiar with Touchpad Pro, it is an iPhone app that uses VNC remote desktop to turn your iPhone into a touchpad for your computer.  There is also a touchscreen keyboard function that allows you to type.  I guess it may not be much use on a desktop, but it can replace a wireless mouse and keyboard if you have your computer hooked up to a tv or a projector for entertainment and for presentations on a large screen.  You can also purchase an upgrade that includes a Screen View feature which allows you to view your computer's screen on the iPhone/iPod.  I haven't purchased the screen view so I don't know if that also works.  I really just tried this for novelty but if I end up using it a lot then I'll pony up for the advanced features.  I also have not tried connecting from a different network or without wifi.  If anyone else tries the advanced stuff I'd love to know how it works.

I am using a jailbroken 8gb iPod Touch with 1.1.4 firmware and Ubuntu Gutsy.

So here's the steps to get up and running:

1.  Jailbreak your iPod/iPhone and install Touchpad Pro from the Utilities section of the Installer App.  If you've read this far you should already have this done but if not, instructions can be found at the Touchpad Pro website ( [http://www.touchpadpro.com/2008/04/touchpad-pro-setup-installing-touchpad.html](http://www.touchpadpro.com/2008/04/touchpad-pro-setup-installing-touchpad.html) )

2.  Setup the Ubuntu Remote Desktop as described in the 'Using the default vnc servers' section of the VNC community documentation ( [https://help.ubuntu.com/community/VNC](https://help.ubuntu.com/community/VNC) ).  Basically just go into System > Preferences > Remote Desktop and check the first two boxes to activate the service (Allow other users to view your desktop & Allow other users to control your desktop).  Then check the box to set a password and enter a password.

3.  Setup the Touchpad Pro app on the iPod/iPhone.  The key here is to enter the ip address with NO port number because vino defaults to zero as the port number.  You will get a message that the 'Connection Failed' if you enter zero as the port number.  Use the following settings (as described with screenshots on the Touchpad Pro website [http://www.touchpadpro.com/2008/04/touchpad-pro-setup-windows.html](http://www.touchpadpro.com/2008/04/touchpad-pro-setup-windows.html) ):

Name:  enter a friendly session name
Address:  enter your local ip adress with no port number (ie. 192.168.100.69)
Password:  enter the password you set in step 2
ScreenView:  turn this off unless you bought the ScreenView upgrade
Mac Mode:  turn this off
Media Server:  turn this off (this only works in Windows)

4.  Connect by tapping the new entry with your friendly session name.  You will see a message in the notification area of the Ubuntu screen that a remote user is connected and the iPod/iPhone will go to a black screen that acts as the touchpad and the buttons at the bottom will bring up the keyboard if you need it.

Enjoy!

---

### Post by bfgmovies on 2008-08-17
you know that touchpad pro is a crappy VNC client that is built off the more powerful FREE VNC client that you can get called vnsea... you should be able to find it after installing the community sources. It allows you to see your computer screen too! :)

---

### Post by all2ez on 2008-08-18
VNSea is cool.  I use it when I'm playing online poker (via virtualbox) and have to go to the bathroom or grab a drink from the kitchen.  It's easier than carrying my laptop around the house for sure.  However, VNSea doesn't work at all when the laptop screen is extended to an external monitor.

Also, VNSea doesn't actually move the mouse on the target computer except when dragging or clicking.  Touchpad Pro is meant as a replacement for the mouse which is not what VNSea is for exactly.  So, yes, both programs are built on the same VNC technology but they do different things and both have value in their own right.  

By the way, do you know if these apps are available on the 2.0 firmware?  I haven't upgraded yet because I don't wanna lose these and other apps I like.

---

### Post by Sigsaucer647 on 2008-12-10
theres a thing in the app store called snatch, basically the same thing except it specializes as a mouse and keyboard

---

### Post by sodalis on 2009-03-13
Hello,

I just dont get it here.

Tried touchpad pro an vnsea as well as i am sure that vino is properly configuered.

It allways gives me "connection failed" :(

I am using Intrepid and an Ipod Toch of the first generation with FW 1.1.5

Maybe there is something wrong with vino in Intrepid because even if i activate "allways display an icon in notification area" there is no response to it. So i am wondering wether the vnc server is running at all.

Do you have experiences with that problem?

---

### Post by nemetron on 2010-02-20
you need to get RemotePad
download and install the server in ubuntu
and download the app from Cydia

---

### Post by daniel309 on 2010-09-11
I just checked out apps in the appstore that allow me to use my iphone as a touchpad for remote controlling my laptop when I hooked it up with the TV. 

I have tested all touchpad apps and must say that "Touchpad Elite" is by far the best app available. [http://www.iteleportmobile.com/iphone/touchpad](http://www.iteleportmobile.com/iphone/touchpad)

Its only 0.79 € in the app store and works like a charm with ubuntu remote desktop. 
Just click System --> Preferences --> Remote Desktop and then "Allow others to view your Desktop" and "Allow others to control your Desktop". Done!

Works right out of the box, awesome!

---

### Post by grindboy on 2010-10-17
I've just had my mouse die on me (its sulking because I've just bought a new keyboard mouse combo from amazon which is yet to arrive!)

Found this thread looking for a way to get my iPod Touch to act as a mouse pad. Anyway after some research I found "hippo remote lite" in the app store. The description says that it requires special software to be installed on the host computer however all really needs is a password protected VNC connection which you can set up through the remote desktop menu in Ubuntu.

So I'm now sat here using my ipod touch as a mouse and the apple wireless bluetooth keyboard in an act of desperation trying to write my dissertation feeling like an apple fanboy! :-/

---

### Post by trinitydan on 2010-12-25
This is pretty sweet!  I love how simple it is to set up!  I had seen this a while back on a Mac, but native support in Ubuntu, I am pleasantly surprised!  I tried "hippo remote lite" but it requires 4.0 firmware and mine is 3.something, so I just searched for more VNC remote desktop apps and found actually an even cooler one IMO, called VNC Lite.  It has a keyboard function and mouse and is free.  It does not require jailbreaking or anything crazy, just go on the app store and get the VNC Lite app and do a little basic configuring on the host machine and iPod and viola!  Like magic!  I love my iPod touch all over again!  Now I can sit on the couch and play/pause my computer playing back videos and such.  :D

---

### Post by Bobbyrne01 on 2011-01-04
> **nemetron said:**
> you need to get RemotePad
download and install the server in ubuntu
and download the app from Cydia

just tried it out, been lookin for a decent mouse server tha'd work in linux for awhile, cheers :)

---

### Post by Bobbyrne01 on 2011-01-04
> **nemetron said:**
> you need to get RemotePad
download and install the server in ubuntu
and download the app from Cydia

just tried it out, been lookin for a decent mouse server tha'd work in linux for awhile, cheers :)

---

