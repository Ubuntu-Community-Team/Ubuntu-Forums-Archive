---
title: "Setting up a Secure Wireless Network"
date: 2010-04-10
forum: Hardware
---

### Post by Majik_420 on 2010-04-10
I've searched and searched and searched the past three days so Now I'm going to start asking questions.

I just bought a wireless router, I would like to setup a secure wireless connection. Everything I read seems to concern just getting the wifi to work. My Wifi has worked since I first installed Ubuntu/Kubuntu so I don't need help there. I've been able to pick up signals and use other people internet for months.

So without using the cd that came with the router, since the cd only works on windows and mac, How do I Make a New Connection, give it a name, password, and keep it hidden?

Everything I read is either of no help because I already have wifi, or it gets too techy and over my head.

Dell Inspiron 1525 karmic kubuntu

---

### Post by 2hot6ft2 on 2010-04-10
Well not every router has the same firmware so they are all going to be a little different so you'll have to play around in it and find everything. Just about all are accessed by typing 192.168.0.1 or 192.168.1.1 in the address bar of a web browser and hitting Enter. Then log in according to that routers instructions.

Set Wireless security to WPA2 Personal and use AES encryption create a strong password up to 63 characters in length.
[https://help.ubuntu.com/community/StrongPasswords](https://help.ubuntu.com/community/StrongPasswords)

The router should have an option to not broadcast so it wont be seen.
That's pretty much it.

You can assign IP Addresses to your adapters MAC address on some if not all routers.

---

### Post by emanuel.b on 2010-04-10
I'm a bit unsure about what you're asking. But if you want to secure your router, then you can usually access the settings page by typing "192.168.0.1" (without quotes) in your web browser. To create a new wireless connection between laptops, then you click on the Network Manager Applet in the notification bar, and select "Create New Wireless Network"...

---

### Post by shaka_zulu on 2010-04-10
I am not sure as well what is your question but generally that CD which got with your router is probably with some manual on it and maybe with some GUI for setting up your router. Generally like gentlemen before me said you should open your favorite browser and type 192.168.0.1 or 192.168.1.1 (this two are most common so if one doesn't work try another one). After that small window will pop up and it will ask for password and username which is usually admin and admin if you didn't change it. 

Once you enter the router set up you will be able to make all kind of modifications.

Cheers,

---

### Post by seenthelite on 2010-04-10
I use D-link for my wireless network and everything that is on the CD is available for download on their web site it may the same for other brands. I personally find it faster to connect by ethernet cable to the router or access point during initial setup. What you need is the manual with a step by step guide to follow and the correct IP address to use to connect to configure it.

---

### Post by efflandt on 2010-04-11
It would be best to temporarily connect with ethernet to the router to configure it.  If you get an automatic IP, do **route -n** in a terminal and the router IP should be your default gateway at the bottom.  Connect to that IP with an http:// URL in a web browser.

If you try to do that from wireless, as soon as you change wireless security settings you will lose it.  And if you made a mistake, may not be able to connect even when you think you entered proper wireless security code on your PC.

---

