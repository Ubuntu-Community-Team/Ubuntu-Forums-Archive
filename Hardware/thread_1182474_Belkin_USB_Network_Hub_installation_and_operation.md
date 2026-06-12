---
title: "Belkin USB Network Hub installation and operation"
date: 2009-06-09
forum: Hardware
---

### Post by timobrien on 2009-06-09
I wanted these comments and question to a previous thread on this topic, but that was closed to new comments.  I am also sorry if I am treading well-trod ground.  And I am sorry that my knowledge is quite limited, being very new to linux.  That said, here is what I am trying to do...

I have a Belkin USB Network Hub, which I purchased before attempting to migrate to linux.  (I installed Ubuntu without checking hardware compatability because the crashing of my WindowsXP encouraged me to jump into linux quickly.)

Anyway, I soon encountered the problem others hit that Belkin has no linux version of the "Control Center" software that operates their USB Network Hub.  After reading past threads on this and experimenting a lot, here is what I did (as best as I can remember):

1. I found on the Internet and downloaded a copy of the "SXUPTP" driver, and I copied those files onto my (Ubuntu) computer.  This is important, because just trying to run the installer from the Belkin site in Wine did not work - it ended saying that it could not start the sxuptp driver.  So it was important to find an isolated version of this driver so it could be run.

2. I ran the Autorun.exe program inside the sxuptp driver folder.  That started the Hub set-up application, and I started down the process of completing it.

3. Taking the advice from previous threads, I found my way to using my browser to access the Network HUB - which allows one to type in the IP address of the Hub and see the devices attached to the hub, but not actually connect to those devices.  However, this browser-based access allowed me to see the various IP addresses in the Network Settings of the hub so that I was able to fill-in information needed to get the sxuptp driver to connect my computer to the Network HUB.  That worked.

3. Then I copied the already installed files for the Control Center from a Windows computer - including the connect.exe application - and I copied that onto my Ubuntu computer.  Using Wine, I got the computer to run connect.exe.  That opened the application that, in Windows, allows you to connect and disconnect from printers and other USB hardware connected to the HUB.  And I was delighted to see that the viewer window in the connect.exe application even showed the icons representing the printers attached to the HUB.

But that was as far as I got.  When I actually tried to select a printer and get the application to connect to it, the application started cloning multiple copies of printer icons and would not stop until I closed down the application completely.  In fact, the application did not truely close down and kept growing in resource usage until I used the Process tab in the System Monitor to end the application process.

Given that I have gotten tantalizingly close getting this hardware to work on Ubuntu, but not quite there, I wanted to throw this information out there to see if there is anyone who might know how to get to the finish line on this.

Any thoughts would be great.

Thanks!

---

### Post by IcarusR on 2009-06-09
It would help if you told us the model of this hub.

---

### Post by timobrien on 2009-06-09
OK... It's model #F5L009.  Thanks!

---

### Post by timobrien on 2009-06-11
I would also add that advice on any hardware that can accomplish the same (or similar) thing compatible with ubuntu (without costing much) would also be appreciated.

What the Belkin Network Hub does is attach to my wireless router, allowing any computer linked to that router (including wirelessly) to use any of the USB devices attached to the Network Hub.

---

### Post by TekNullOG on 2009-06-12
I just ordered this online and found out that it isn't Linux compatible. I thought it was going to have a windows share that I could connect to using samba but no!!!!

So far, I've been looking for a solution online for 20 mins. no luck...

f*!#

---

### Post by Ian Ferguson on 2009-06-27
I've tried a different route, but ended up with the same problem as timobrien. I'm running Ubuntu inside Windows Vista, and I'm able to get to my windows files from Ubuntu, so I tried right clicking connect.exe and selecting "Open with Wine Windows Program Loader". The first time, nothing happens.  The second time the Control Centre window opens just like in Windows, but showing no devices available. Clicking the "Refresh" button shows the devices that are plugged in to the hub (printer and external HDD), but not connected. trying to connect a device creates multiple clones of the device icon, and it can only be stopped from System Monitor.

I've submitted my test results for review to the Wine Application Database ([http://appdb.winehq.org/](http://appdb.winehq.org/)), so maybe someone there can come up with an answer.

I wonder if it's worth the trouble, though, since even in Windows I've found this Belkin hub a bit of a pain. It keeps losing connection with the devices plugged in to it, and the only way I can get them back is to reboot, so like Tim I would also welcome any suggestions for other (not too expensive!) ways of doing the same thing which will work in Linux and in Windows.

---

### Post by Ian Ferguson on 2009-07-01
Further to my last post, I've tried running Connect.exe from Command line (Pardon my newbiness, but I've only just learned how to do this!:p), and this is the result:

```
ian@ubuntu:~$ wine ~/.wine/dosdevices/c:/Program\ Files/Network\ USB\ Hub\ Control\ Center/Connect.exe
fixme:reg:GetNativeSystemInfo (0x32fa5c) using GetSystemInfo()
fixme:wtsapi:WTSRegisterSessionNotification Stub 0x10030 0x00000000
fixme:shdocvw:PersistStreamInit_InitNew (0x136c00)
fixme:shdocvw:OleObject_Advise (0x136c00)->(0x641c2d, 0x641c79)
fixme:shdocvw:ViewObject_SetAdvise (0x136c00)->(1 00000000 0x641c2d)
fixme:shdocvw:ViewObject_Draw (0x136c00)->(1 -1 (nil) (nil) (nil) 0x338 0x641c91 0x641c91 (nil) 00000000)
fixme:urlmon:URLMoniker_BindToObject use running object table
fixme:shdocvw:bind_to_object BindToObject failed: 800401e4
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x136c00)->(0x32d7a4)
fixme:urlmon:URLMoniker_BindToObject use running object table
fixme:shdocvw:bind_to_object BindToObject failed: 80070057
  

```
I'm sure this means more to some of you out there than it does to me, but even I can see there are a lot of things asking to be fixed!

Just a thought, but could I be right in thinking that "NativeSystem" means Windows, and I need to find some more files in Windows?

---

### Post by sim0ne on 2010-11-27
Hi! 
I'm interested to migrate from windows to ubuntu, and I have the same problem with my Belkin USB hub.
I'd like to know if someone have found a "good working" solution to get it work in ubuntu.
Thanks
Simone

---

### Post by melneilla on 2012-04-18
Hi I`m using Ubuntu 11.10 and I`m trying to use a printer (HP laserjet p1005) conected via wifi through a belkin f5l009 usb network hub . 
The problem is that I've installed the printer like network printer lookin for it with its IP, the Ubuntu requested me for installing the driver. Now I can see it but when I send a print order, it doesnt work.
Can anyone help me.
Thanks

---

### Post by northrup on 2012-09-14
I realize this thread is a bit old, but we might have some progress.

I plastered up a [teardown of the F5L009 on iFixit](http://www.ifixit.com/Teardown/Belkin-F5L009-Network-USB-Hub-Teardown/10455/1) using one of these that I happened to pick up at my town's local thrift store, and I did my best to at least give cursory documentation on the four chips involved.  If my hunches are correct, it might be possible to get this device (and similar ones) working under Ubuntu and other Linux distributions.

There are two main chips that come into play: a Micrel KSZ8695PX system-on-chip and a NEC D720101GJ USB controller.  The Micrel SoC is basically an ARM9 core, as well RAM, ROM, PCI, and ethernet control interfaces.  It's designed to run either Windows CE or Linux from said ROM; if Belkin went the Linux route, then hopefully they'll pony up the source code to the device's firmware so it can be studied to develop open-source drivers for it (I've already put in a request).

The other chip - the one from NEC - is basically the driving force behind a number of different 5-6 port USB PCI cards (including the Belkin F5U220).  Given that, this is probably utilizing the Micrel SoC's PCI support, which means that a driver for a PCI card using the D720101GJ as its core would most likely be part of the solution.

With all that said, the missing link is the firmware.  If Belkin plays nice, there might be some source code to work with so we can understand the details on how the firmware communicates with the client-side software over the network.  Once that's fully established, it should be a matter of writing up some kind of driver that routes the USB connection through the firmware's expected network protocol as if it were a local device.

If Belkin doesn't play nice, the hardware itself is documented well enough that developing custom firmware for it is at least theoretically possible, and since the SoC driving the F5L009 is intended for routers, projects like OpenWRT might be a valuable resource.

**Update:** Belkin didn't play nice.  However, we might not be totally shafted.  [This guy](http://daeken.com/hacking-the-belkin-network-usb-hub) put in quite a bit of work on deciphering the message formats, though there are still quite a few gaps.

---

### Post by netwar on 2012-12-19
I have this usb hub as well, it was gifted to me about two years ago and it still works but not on linux or unix :( the only machine that i have that runs windows is a ancient XP machine that triple boots Lubuntu and Damn Small Linux. Would like to keep this  thread alive need

---

### Post by edwaleni on 2013-06-16
The Belkin Network USB Hub was developed by Silex.

Belkin does have a source library for this device. I do not have the link.

Silex also has a development library for Linux as well here:

[http://www.silexamerica.com/products/oem_software/sx-virtual_usb_sdk.html](http://www.silexamerica.com/products/oem_software/sx-virtual_usb_sdk.html)

Those with Windows were shocked to see that Silex updated the software for Win7, but Belkin never carried the update forward.

I have not had it work with Ubuntu yet. That is why I landed here.

---

