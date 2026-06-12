---
title: "I need help with clear wireless internet/USB"
date: 2009-08-18
forum: Hardware
---

### Post by serenelune on 2009-08-18
I've very recently switched over to Ubuntu (9.04 Jaunty release) after being aware of it for a few years (Yes, newbie here). Now, I'm aware that Wine runs Windows programs, but I want to ask just in case. My current internet provider is Clear Wireless and to run my internet, I have to use a USB and an executable program. Without the executable, I can't connect to the internet (I'm currently on my windows OS). So how can I execute this program in WINE? The instructions as far as I saw it required you to link inside one of the processes for 3rd party applications, but that requires internet connection, which I can't get on Ubuntu. I apologize in advance if this could've been answered by reading something but I don't quite understand the instructions and maybe someone with prior experience in this could help me out. Thank you.

Aditional details: I connect via a program called Wi-max and the USB model 25100 by Motorola, a 3G connection.

---

### Post by sitendurocks@gmail.com on 2009-08-18
hi
great to have you here.. could you give me some details about the type of your connection. my connection is similar to yours and after i asked my Internet provider they said i can log in to their website through the browser.  iam sure there is some linux version for the program yoou are talking about..

each and every Internet provider has provision for Linux support, so it will save you a lot of hassle if you could get in touch with the customer care and ask them..

---

### Post by Katalog on 2009-08-18
Have you spoken to anyone in customer support with your internet provider yet? You may get lucky and they'll actually be able to point you in the right direction or provide you with software that will work under Linux. I wouldn't hold my breath, but you never know. But in any case, I know there are people out there who are using Wimax from other providers under Ubuntu, so hopefully you should be able to get it to work.

Oh, and welcome! :)

---

### Post by epidemiks on 2009-08-18
Sounds similar to the 3G usb sticks for Optus in australia.

these links might help:

[http://ubuntuforums.org/showthread.php?t=843973](http://ubuntuforums.org/showthread.php?t=843973)
[http://www.dhanapalan.com/blog/2008/10/09/huawei-e169-3g-modem-on-ubuntu-804/](http://www.dhanapalan.com/blog/2008/10/09/huawei-e169-3g-modem-on-ubuntu-804/)
[http://forums.whirlpool.net.au/forum-replies-archive.cfm/1046813.html](http://forums.whirlpool.net.au/forum-replies-archive.cfm/1046813.html)

---

### Post by serenelune on 2009-08-18
> **sitendurocks@gmail.com said:**
> hi
great to have you here.. could you give me some details about the type of your connection. my connection is similar to yours and after i asked my Internet provider they said i can log in to their website through the browser.  iam sure there is some linux version for the program yoou are talking about..

each and every Internet provider has provision for Linux support, so it will save you a lot of hassle if you could get in touch with the customer care and ask them..
I connect via a program called Wi-max and the USB model 25100 by Motorola, a 3G connection. My internet provider is Clearwire internet services. I asked in a live chat but the chat ended O.o. I sent them an e-mail but, I'm not too sure. They're in a few areas.

---

### Post by longhaired1 on 2009-08-22
I just discovered this resource:

[http://www.linuxwimax.org/](http://www.linuxwimax.org/)

and will be spending some time this weekend trying to get my laptop connect to Clear via my usb modem.

I will check in here and tell everyone how it goes. I have to start cracking the books right now and figure things out.

---

### Post by bjtuna on 2009-10-23
Did the Linux WiMax stack work?

---

### Post by Brian2177b on 2009-11-14
I'm having the same problem getting the motorola 25100working under ubuntu nbr 9.10. It's driving me nuts because this is literally the only thing preventing me from removing windows from my last pc for good. Any help would be greatly appreciated.

---

### Post by tastyllama on 2009-11-18
I have the same wireless adapter.  Just got Clear today.  Talked to tech support, they only say that they do not support anything other than windows and mac.  If you can get the service working, that's great, but they will not support it.  Apparently, they do get lots of requests for ubuntu though (although no plans to support it in the future).

When I plug it into ubuntu, it shows a usb device connected.  But I don't see any new network adapters in network-manager. And under mobile broadband, there is not an option for Clear. (no Option for WiMax either.

The device model is "Motorola USBw 25100".  It looks exactly like [this one]("http://www.motorola.com/Business/US-EN/Product+Lines/MOTOwi4/USBw_100_US-EN"), but with a [Clear]("http://www.clear.com/") logo on it.  Box says it is compatible with 802.16e and WiMAX Wave 2 networks.

Any help would be appreciated.

---

### Post by gman16000 on 2009-11-23
I also have the clearwire/motorola USB Modem (USBw 25100).  I was going to try the Linux WiMAX stack until I noticed that they are currently only supporting Intel chips.  This clearwire dongle uses Beceem chipset which the site claims is not currently supported.

---

### Post by majestic-x on 2009-11-27
I have found a very temporary solution that will probably not work for everyone.  I must say I'm not good at this sort of stuff so I will try to answer any questions but I am no expert so helpfully others will help.

This solution eats up a ton of resources and by no means is it the ultimate fix, but with the lack of anybody offering something better this is what I have done.

First your pc will need to be a dual-core 2ghz or better and have a few gigs of ram.

You will need to download and install Virtualbox, I use 3.0 non free version.  It is free just not Open Source.  You will need to download the app from their site using this link [http://www.virtualbox.org/wiki/Linux_Downloads]("http://www.virtualbox.org/wiki/Linux_Downloads")

Do not use the OSE, it does not support USB which you will need.

Once you have installed Virtualbox you will need to blow the dust off your old Windows XP disk or ISO...

follow the directions from the link below and start at Creating a Virtual machine.

once you have Windblows installed you need to activate the guest consepts.  You can do this from the menu on your virtual machine.  When you do this it will create a virtual cdrom click and run the installation. 

Now you will need to enable USB.  Do this when the virtual machine is not running.  Open the Virtualbox app and select your xp install. you will see settings on the right hand side.  One of your options will be USB  enable it and when you do this make sure your wimax addapter is plugged in.  select your adapter from the list and BOOM you will see the device in your Windblows virtual machine. 

If you did not do so at the start make sure you have enabled a network adapter in the same menu use the NAT settings.  You will need this to download the clear software.  If you have a disk don't worry about network settings.

Start the pig up "Windblows" and you should see the usb adapter in your stack if not then toy with the usb settings in the bottom right corner of your virtual machine.  

Download your Clear software via Internet Exploder or install via the disk.

Now if all goes well you should have Clear software running and be able to connect to the network in Windblows.  If not I will try to help but I am still a NO.ob.

Now for the tricky stuff.  We need to make linux see the clear internet connection.

Go to your Connection Settings in XP.  You should see the Clear device there.  Right click and enable Internet Sharing.  Shut down your XP and go back to VB.  in the network settings enable a second adapter and use host only mode.  Make sure to select vboxnet0 in the bottom selection box.

Now open a terminal and run an ifconfig.  You should see vboxnet0.

Run these two commands
ifconfig vboxnet0 192.168.0.3 255.255.255.0

route add default gw 192.168.0.1

I do not know what those commands do I just know after I run them I have Internet in Ubuntu.

The good news about this is that you now have Internet.  The bad news is it will consume a ton of cpu and ram.  Please if anybody can find a better way let me know.  As you can tell I hate Windows and do not like it infesting my computer...

As I said I am a bit of a noob but will try to help.

A tip if you can find a tutorial to enable and run remote desktop and virtualbox headless mode it runs much lighter then actualy running the whole interface through Virtualbox.

Hope this helps and please someone fix this!!!!

---

### Post by icemandb3 on 2009-12-13
Clear has a portable hot spot (wireless router) that uses a rechargeable battery. You plug your Motorola device into the hot spot. Price is a bit steep, but this device could be used in a multiplicity of places.

They call it the Clear Spot. This device, while not Linux in nature, would enable your laptop to connect to Clear via the wireless device most laptops have. 

I've not found a solution for the lack of compatibility yet.

---

### Post by zafo on 2010-01-06
I just got Clear WiMax Internet today, and it meets all my needs at home. I bought the USB Modem and the Clearpoint Personal Hotspot for use outside the home. I can either boot into Windows XP and use the modem, or boot up the hotspot for Linux. Starting up a hotspot a foot away from the netbook is overkill, and I would love to be able to use the modem directly in Linux. I hope that there is someone more technical than I am that can come up with Linux driver support.

If you look inside Setup.exe, all the files (dll's etc.) are there. Is there any way, perhaps, to use ndiswrapper to get the basic modem driver working in Linux? 

Rod

---

### Post by rvndmnmt on 2010-01-26
Posted before.  Trying to search for a solution to this problem myself.

No.  NDISwrapper does not work.  Linux WiMAX does not work.  Perhaps the Moblin drivers might.  However Moblin is based off of a slimmed down hashed version of Fedora 10 ported by the nice folks at Intel for the 1.6 Atom processor.  So good luck.  

After spending a week of my spare time hacking Open Office to install with Java (you would figure it would be as simple as adding a symbolic link but noooooooooooo) I'm pretty exhausted of that distro.  Don't get me wrong.  As far as flavors go Moblin is pretty solid.  Just not very geek friendly.

Guess im stuck with VM for the time being.

---

### Post by rvndmnmt on 2010-01-26
Anyways.  Don't know what the guy did.  While virtual box will recognize the USB drive.  Ubuntu and the Virtual Machine, however, will not.  And it is driving me nuts.  Wonder if VMware will do the trick?  Been away from linux for a while.  While the learning curve is steep, its a little easier the second time around.

I'm not to worried about system resources.  Have 8 gig of RAM on my notebook (upgraded to run the previous form of Vista, then 7. Ran 7 like a champ) and a 2.1GHz core 2 duo.  Linux runs better than Windows past 2 gig.  Seems to be a wall, the closer Windows comes to occupying 2gig of RAM the slower it runs.  Anything past that and its like molasses.  Ready Boost or not.

I do however need this dongle.  So the VM solution is workable.  I would hate to sacrifice the penguin on the altar of Windows to the anti-christ Bill Gates.

---

### Post by zafo on 2010-01-26
An update to my previous post.

I did have a problem with the Clear Spot WiFi router at the beginning. Every morning I had to talk to Clear and have them reset the USB modem for it to work. They were not able to give me a solution to the problem. I finally realized that it was shipped with an older version of firmware. As soon as I download the latest version, it works great.

I'd still love to have a Linux solution without the Clear Spot WiFi router, but it does work fine.

Rod

---

### Post by Bit Hacker on 2010-06-06
> **majestic-x said:**
> I have found a very temporary solution that will probably not work for everyone.  I must say I'm not good at this sort of stuff so I will try to answer any questions but I am no expert so helpfully others will help.

This solution eats up a ton of resources and by no means is it the ultimate fix, but with the lack of anybody offering something better this is what I have done.

First your pc will need to be a dual-core 2ghz or better and have a few gigs of ram.

You will need to download and install Virtualbox, I use 3.0 non free version.  It is free just not Open Source.  You will need to download the app from their site using this link [http://www.virtualbox.org/wiki/Linux_Downloads]("http://www.virtualbox.org/wiki/Linux_Downloads")

Do not use the OSE, it does not support USB which you will need.

Once you have installed Virtualbox you will need to blow the dust off your old Windows XP disk or ISO...

follow the directions from the link below and start at Creating a Virtual machine.

once you have Windblows installed you need to activate the guest consepts.  You can do this from the menu on your virtual machine.  When you do this it will create a virtual cdrom click and run the installation. 

Now you will need to enable USB.  Do this when the virtual machine is not running.  Open the Virtualbox app and select your xp install. you will see settings on the right hand side.  One of your options will be USB  enable it and when you do this make sure your wimax addapter is plugged in.  select your adapter from the list and BOOM you will see the device in your Windblows virtual machine. 

If you did not do so at the start make sure you have enabled a network adapter in the same menu use the NAT settings.  You will need this to download the clear software.  If you have a disk don't worry about network settings.

Start the pig up "Windblows" and you should see the usb adapter in your stack if not then toy with the usb settings in the bottom right corner of your virtual machine.  

Download your Clear software via Internet Exploder or install via the disk.

Now if all goes well you should have Clear software running and be able to connect to the network in Windblows.  If not I will try to help but I am still a NO.ob.

Now for the tricky stuff.  We need to make linux see the clear internet connection.

Go to your Connection Settings in XP.  You should see the Clear device there.  Right click and enable Internet Sharing.  Shut down your XP and go back to VB.  in the network settings enable a second adapter and use host only mode.  Make sure to select vboxnet0 in the bottom selection box.

Now open a terminal and run an ifconfig.  You should see vboxnet0.

Run these two commands
ifconfig vboxnet0 192.168.0.3 255.255.255.0

route add default gw 192.168.0.1

I do not know what those commands do I just know after I run them I have Internet in Ubuntu.

The good news about this is that you now have Internet.  The bad news is it will consume a ton of cpu and ram.  Please if anybody can find a better way let me know.  As you can tell I hate Windows and do not like it infesting my computer...

As I said I am a bit of a noob but will try to help.

A tip if you can find a tutorial to enable and run remote desktop and virtualbox headless mode it runs much lighter then actualy running the whole interface through Virtualbox.

Hope this helps and please someone fix this!!!!

I tried to follow your way but I'm having a little bit of trouble where linux can't see the internet connection in windowsxp. Can you help or give me a resource link where I can find help? Thanks in advance. :)

---

### Post by metallica1973 on 2010-08-07
I am a Field Engineering that work as a contractor for Clearwire 4G WiMax network deployment and was given a Motorola usbw 25100 network card and was told to use this with windows. I do not work as a IT consultant but rather a RF guy and am trying the avoid using windows by all means possible. I read the 

[http://community.4gdeveloper.com/attachments/20/NDnSAgentConfig_forDriver.xml]("http://community.4gdeveloper.com/attachments/20/NDnSAgentConfig_forDriver.xml")

from the [http://www.linuxwimax.org]("http://www.linuxwimax.org")

and hopefully will have an answer soon. Technical support from Clearwire wont help me out so I must venture out on my own.

---

### Post by flat49head on 2011-03-22
p { margin-bottom: 0.08in; }  Ubuntu 10.10
 Kernel 2.6.35-22
 Since my job takes me across the country I went with Clear Mobile Broadband.
 Here is how I got it working in Ubuntu...
 Systems>Preferences>Network Connections
 Mobile Broadband tab>Add
 Ubuntu picks up my wireless device and names it properly...
 'Sierra Wireless Device'
 This is a USB 3G/4G device I purchased when I signed up for Clear Mobile Broadband.
 It lists providers.  Clear was not listed.  I entered it manually.
 'Clear Mobile Broadband'
 Entered my user name and password I signed up with.
 Bang!  I am browsing!
 

 If you are using Clear at home, and it sees your device under the Wireless tab
 you should be good to go.  Ubuntu has to see your device first before you can do anything else.
 

 I am running both Windows XP and Ubuntu 10.10 on my old (2002!) Compaq laptop. 

 The beauty of running Clear in Ubuntu is, you DO NOT have to mess with their crappy Connection Manager software that Windows uses!

---

### Post by Krendarian on 2011-05-17
Have same issue with Ubuntu and my Clear USB device just not working. Been bouncing back to this for over a year and a half now, occasionally looking around for new info or advice. Initially I was told the same thing as someone else above by the Clear store tech guy in that there was no design or plan for the Clear company/service to implement any connection manager software for its Linux users. IMO, bad call there Clear.

I am going to try flat49head's fix tomorrow, and just cannot believe it will be that simple. Will post my result when I get it figured out.

---

### Post by DrSeabreeze on 2011-09-25
How did you find out what your user and password is for Clearwire?
I know my User and Password for account management website at Clearwire.
But the actual 4g WIMAX usb dongle just kind of magically logs in with the
windows connection manager.  So I do not know the password.
Help.. It looks like it should work...

---

### Post by DrSeabreeze on 2011-09-25
**Re: I need help with clear wireless internet/USB** 			
 			 			 		   		 		 		How did you find out what your user and password is for Clearwire?
I know my User and Password for account management website at Clearwire.
But the actual 4g WIMAX usb dongle just kind of magically logs in with the
windows connection manager.  So I do not know the password.
Help.. It looks like it should work...




> **flat49head said:**
> p { margin-bottom: 0.08in; }  Ubuntu 10.10
 Kernel 2.6.35-22
 Since my job takes me across the country I went with Clear Mobile Broadband.
 Here is how I got it working in Ubuntu...
 Systems>Preferences>Network Connections
 Mobile Broadband tab>Add
 Ubuntu picks up my wireless device and names it properly...
 'Sierra Wireless Device'
 This is a USB 3G/4G device I purchased when I signed up for Clear Mobile Broadband.
 It lists providers.  Clear was not listed.  I entered it manually.
 'Clear Mobile Broadband'
 Entered my user name and password I signed up with.
 Bang!  I am browsing!
 

 If you are using Clear at home, and it sees your device under the Wireless tab
 you should be good to go.  Ubuntu has to see your device first before you can do anything else.
 

 I am running both Windows XP and Ubuntu 10.10 on my old (2002!) Compaq laptop. 

 The beauty of running Clear in Ubuntu is, you DO NOT have to mess with their crappy Connection Manager software that Windows uses!

---

### Post by ronlybonly on 2011-10-06
Just wondering if anybody has had any luck getting their Clear USB devices to work. Mine is a Motorola WiMAX, and I have not been able to get it to work under Ubuntu.

---

