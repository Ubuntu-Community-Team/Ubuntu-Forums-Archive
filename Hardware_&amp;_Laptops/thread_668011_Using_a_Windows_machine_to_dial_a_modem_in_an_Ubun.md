---
title: "Using a Windows machine to dial a modem in an Ubuntu machine"
date: 2008-01-14
forum: Hardware &amp; Laptops
---

### Post by Vlizzard on 2008-01-14
I have a Toshiba laptop with Ubuntu Feisty installed on it.  My other computer is an older desktop with Windows Xp on it.  The problem is that ubuntu doesn't recognize my internal modem and i can't get on the internet. The pc doesn't have a modem so I have to use the laptop to connect if I want internet.  I have tried going through the linmodems.org drivers and nothing has worked.  What I am wondering is if there is a way to create a network that allows the windows machine to use the modem in the laptop and then share the connection with the laptop.  I know on windows you can let other computers control your internet connection on a network, but is it possible to do this sort of thing with Ubuntu?  Thank you!

---

### Post by travm on 2008-01-15
you bet there is.  only downfall with this is you cannot "connect" to the internet with the linux box.  it can access the internet, but only after you have connected to the internet manually on the windows machine (laptop).

I have a network at home, where i share my dialup connection (which is made through a windows box) to 3 other computers, 2 run windows, and my laptop uses linux.  on the 2 windows computers i can "connect" to the internet from their seat, but on my laptop i have to get up and connect manuallly on the windows box first.  They are connected through a router ( a hub works better for this) that has been specifically configured NOT to use DHCP.  I can talk you through this if this is your case.  If you have a simple hub or switch it will be easier for your.

if you just have a hub, you need to plug both machines into the hub and verify that your network is functioning.  (if you only have one windows machine, you might only be able to check that the lights are on the hub and eth adapters)

Then you go into your windows box, network connections, right click your internet connection (dial-up connection) and select "properties" i believe.  on the window that pops up there is a tab called "advanced",  inside this tab there should be a box that says "allow other users on the network to use this connection" or something similar.  after you select this you should be ready roll.  click ok.  then simply connect to the internet on your windows machine and your linux box then should be getting internet packets routed to it through the windows machine accross your network.   I dont recommend selecting "establish a dialup connection whenever a computer on my network tries to access the internet" as when I did this my modem got a mind of its own and connected regularly at random.  Your mileage may vary.

If you have a router like i said it is more involved since the router will intercept the internet packets and then be like, wtf i'm not connected to a WAN.  it will fail.  finding the setting in your router config to turn off DHCP will solve this problem, but only if you turn this off before you share your internet connection, since doing this installs a DHCP server onto your windows machine ( you can do this in reverse with linux I believe, and in fact when i get some time I intend to do this, then connect to the web via SSH'ing into my linux server and connecting with a script or something).  

anyway, i am a terrible teacher and blog like a 12 year old so let me know if you have any questions.  or if i misinterpreted your questions.

---

### Post by Vlizzard on 2008-01-16
I think that you understood my question, but I don't know anything about routers.  What I am using to connect the two computers together is crossover cable.  The modem is an internal modem on the linux machine, but linux doesn't recognize it and won't dial it.  I want to use the windows machine to dial this modem (because it doesn't have its own modem), and then share the connection with the linux machine.  So in effect, I want to access the modem on the linux box with the windows machine to get my network online.  Is this kind of thing possible using a crossover cable to network the computers together.  :confused:  Anyway, thank you for your help so far!:)

---

### Post by travm on 2008-01-16
yes, i have never used a cross-over cable but as far as I know for the two computers it will do.   You will not have access to the modem however, but you will get DHCP [(WIKIPEDIA SAYS DHCP)]("http://en.wikipedia.org/wiki/Dynamic_Host_Configuration_Protocol") if you set up your internet connection sharing on the windows box (laptop) like i mentioned above.  it should work.  after you have the internet connection sharing set up, simply connect to the internet with the laptop, then try to use the desktop.  should work like a charm.  At least mine does, I have it sharing my internet wirelessly through my dlink wireless router to my linux laptop i can use anywhere in the house.
but for you you dont need a hub or a router, but you will only be able to share the connection between 2 computers using a cross over cable.
let me know if you have any problems.

---

