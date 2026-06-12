---
title: "wireless card"
date: 2008-09-05
forum: General Help
---

### Post by pikabuntu on 2008-09-05
I have a wireless card in my desktop.  On the live cd, ubuntu would recognize it, but installed, it does not seem to... How could I go about fixing this?

---

### Post by pastalavista on 2008-09-05
Maybe the drivers aren't enabled, you haven't really given us enough information to go on. Go to System > Administration > Hardware Drivers and see if they need to be enabled or if they even were installed. If they are enabled, try disabling and re-enabling. Have you tried configuring your wireless manually?

---

### Post by Twitch6000 on 2008-09-05
In the upper right do you see the thing that is kind of greyed out?
That looks like a wireless bar?
Right click,find your wireless area,and click enable.

It sometimes disables on a install for no reason :(.

---

### Post by enderal on 2008-09-05
I'm far from an expert but I have been through the wireless part a number of times and I only have experience with my own driver.

Try to left click the computer at the top right of the screen and see if you can see the wireless networks. If so click on yours and the bar connection icon should appear.

If it works then even if weak, click on the gear icon at the top right and update by clicking on "check".

Then go to System > Administration > Synaptic Package Manager and install ndiswrapper-common., Then go to Applications > Add/Remove and install Windows Wireless drivers.

Read the Sticky post at 
[http://ubuntuforums.org/showthread.php?t=885847](http://ubuntuforums.org/showthread.php?t=885847)
Excellent post.

You will have to find out your wireless driver and probably download it and then install it. You can do this with no internet connection as long as you can get the files to ubuntu.

I could not get mine to download directly into ubuntu and had to get them there through the file manager.

Hard the first time. Keep plugging away.

Don't know if I've been any help but hope I've shed a bit of light on things for you.

This is a difficult part of ubuntu but there is lots of help available.

---

### Post by Dan78 on 2008-09-05
i had same problem wen i installed ubuntu 8.04.1 there's only certain wireless cards or dongles that it will reconize, i've got a netgear wireless g, ver 3...ubuntu didn't pick it up, but got info on cards that are reconized, i know for sure 100% that the Belkin F5D7050 works because that's what i'm using now, ubuntu will reconize it straight away...otherwize you'll hav to get online somehow to d/l the driver's and go through a heap of steps to get your card to work..

---

