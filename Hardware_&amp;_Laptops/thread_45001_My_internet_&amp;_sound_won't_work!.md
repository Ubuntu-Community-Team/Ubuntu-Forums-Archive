---
title: "My internet &amp; sound won't work!"
date: 2005-06-28
forum: Hardware &amp; Laptops
---

### Post by linuxrobot on 2005-06-28
Hello all,
I just installed Ubuntu Linux version 5.04 yesterday on my PC.  I partitioned the hard drive so I could run either Linux or my other; MS Windows 98SE.

First question...
My internet is cable, going into the house to a modem, then a wireless router (D-Link) which my computer picks up with a 802.11G PCI wireless adapter card. (also D-Link)  When I booted up in Ubuntu, FireFox couldn't connect to the internet.  I tried to install the software (on Linux) for the wireless adapter.  But, the files are Windows files, (exe files, etc.) and Ubuntu can't open them.  ](*,)   So what should I do? :???: 

Next question...
After I installed Ubuntu, linux hasn't played one single sounds.  The sounds are checked, to happen, in the games and boot-up.  I have the speakers turned all the way up, and I have heard nothing!   I would like to be able to watch DVDs and play music, but right now I can't.  What should I do?

Thanks in advance!
LinuxRobot :)

---

### Post by emmet on 2005-06-28
Hi,

I don't know if I can help you, but I *do* know that if you could give a smidgen more information, then there's much more chance that someone can give you a hand.

The Windows drivers for your network card will not work with Linux but this does not mean that you card is not supported by Ubuntu.

The information that people will need is primarily: what is the make/model of your network card? This will give people a clue on what steps you need to take next.

The same goes for the sound card. If you can get this information, then so much the better.

Without this information, it's going to be tough going. Sorry.

Like I said at the beginning, I'm not a hardware expert, but I'm sure there is someone out here who *can* give you some hints given the right intial information.

Cheers

Emmet

---

### Post by linuxrobot on 2005-06-28
**emmet**,

Good idea...

My wireless card is a:
*D-Link AirPlus Xtreme G DWL-G520 High-Speed 802.11g Wireless PCI Adapter*

My sound card is integrated into my motherboard.  Is there anyway to figure out that part without taking apart my pc?  I do know this about the motherboard; it has a Pentium II 400Mhz processor.

Thanks!
**LinuxRobot** :)

*P.S.  Your signature is awesome, emmet!  I love it!*

---

### Post by Lunde on 2005-06-28
[QUOTE=linuxrobot]**emmet**,

Good idea...

My wireless card is a:
*D-Link AirPlus Xtreme G DWL-G520 High-Speed 802.11g Wireless PCI Adapter*

My sound card is integrated into my motherboard.  Is there anyway to figure out that part without taking apart my pc?  I do know this about the motherboard; it has a Pentium II 400Mhz processor.

Thanks!
**LinuxRobot** :)[/QUOTE]
 OK.. I'll just give you some hints now, gotta go. 

D-Link:
if it's a DWL-g520+, its an acx111 chipset, and you need ot do the following..
[http://www.houseofcraig.net/acx100_howto.php](http://www.houseofcraig.net/acx100_howto.php)

if it's a DWL-g520 and an Atheros chipset, there's some info and a howto here..
[http://madwifi.sourceforge.net/](http://madwifi.sourceforge.net/)
[http://ubuntuforums.org/showthread.php?t=38972](http://ubuntuforums.org/showthread.php?t=38972)


Sound:
This will get you started...
[http://ubuntuforums.org/showthread.php?t=32063](http://ubuntuforums.org/showthread.php?t=32063)

EDIT: the sound problem... sorry I read a bit fast, you don't have sound at all? Not just the usual problem of not getting sound in some programs.. Have to get back on this, just start with your wireless

Hope this helps

---

### Post by linuxrobot on 2005-06-28
Lunde,
OK, I'll try it!
I think my card has an Atheros chipset, so I'll try those first.

**LinuxRobot ** :)

---

### Post by linuxrobot on 2005-06-28
I tried what they said to do at:
[http://ubuntuforums.org/showthread.php?t=38972](http://ubuntuforums.org/showthread.php?t=38972) 
But it didn't work.  My wireless card didn't show up!
I don't know what to do!
**LinuxRobot**  :???:

---

### Post by linuxrobot on 2005-06-28
I went back into Linux, and retried everything, it still didn't work, or show up.  Now, when I type **iwconfig** the *ath0* doesn't even show up anymore!  It used to have some info, but it says there is nothing now!
I hope I didn't mess something up! ](*,) 

**LinuxRobot**  :-?

---

### Post by Lunde on 2005-06-29
[QUOTE=linuxrobot]I tried what they said to do at:
[http://ubuntuforums.org/showthread.php?t=38972](http://ubuntuforums.org/showthread.php?t=38972) 
But it didn't work.  My wireless card didn't show up!
I don't know what to do!
**LinuxRobot**  :???:[/QUOTE]
 Are you sure it's not an acx111 chipset?
Type the follwing command in terminal:

lspci -n

if your last digits looks like one of these:
    104c:8400 
    104c:8401 
    104c:9066 
You have a acx card

---

### Post by linuxrobot on 2005-06-29
Ok, I'll try it.
Thanks!
**LinuxRobot**  :smile:

---

### Post by linuxrobot on 2005-06-29
Lunde,
You know that now my Linux doesn't even show anything when you type: *iwconfig*   That was on my main user.  So I got this brainy idea to delete my main user, and use the one of the other users.  That was an extremely stupid thing to do! ](*,)   Now, I can't log into Root Terminal or Users & Groups, because it says something like: _"Can't Access file; Child 1 status"_ , or something like that. I can't do anything, it's so annoying! Is there a "restore to factory settings" (like Windows)? I don't have a lot of info to loose, so I won't care! :-x
I haven't been able to do what you suggested yet, because of my huge mistake!
Thanks!

**LinuxRobot**  :-?

---

### Post by Lunde on 2005-06-29
[QUOTE=linuxrobot]Lunde,
You know that now my Linux doesn't even show anything when you type: *iwconfig*   That was on my main user.  So I got this brainy idea to delete my main user, and use the one of the other users.  That was an extremely stupid thing to do! ](*,)   Now, I can't log into Root Terminal or Users & Groups, because it says something like: _"Can't Access file; Child 1 status"_ , or something like that. I can't do anything, it's so annoying! Is there a "restore to factory settings" (like Windows)? I don't have a lot of info to loose, so I won't care! :-x
I haven't been able to do what you suggested yet, because of my huge mistake!
Thanks!

**LinuxRobot**  :-?[/QUOTE]
 Can you still before the GDM login press Alt+Ctrl+F2 and then login in console.

If you don't have to much to loose I would consider a fresh install. Then next time do a backup like discribed in this howto:
[http://www.ubuntuforums.org/showthread.php?t=35087](http://www.ubuntuforums.org/showthread.php?t=35087)

---

### Post by linuxrobot on 2005-06-29
Lunde,

Yes, I think I'm going to do a fresh install.
Thanks for the link to the info, by the way. :) 
Then, I'm going to renew the quest for _working_ internet and audio! :D 
Thanks!

**LinuxRobot**  ;-)

---

### Post by linuxrobot on 2005-06-29
Okay, everything is re-installed and ready!

I'm ready to keep going on pusuing internet for Linux! :arrow:

Heres what I found:
*D-Link  802.11g  	DWL-G520  	PCI  	Atheros*
That's my wireless card.  I found this info at:
[http://www.linux-wlan.org/docs/wlan_adapters.html.gz](http://www.linux-wlan.org/docs/wlan_adapters.html.gz) 
So, now we know that I'm dealing with an Atheros chipset.

Hope this helps!	

**LinuxRobot**  :)

---

### Post by Lunde on 2005-06-29
[QUOTE=linuxrobot]Okay, everything is re-installed and ready!

I'm ready to keep going on pusuing internet for Linux! :arrow:

Heres what I found:
*D-Link  802.11g  	DWL-G520  	PCI  	Atheros*
That's my wireless card.  I found this info at:
[http://www.linux-wlan.org/docs/wlan_adapters.html.gz](http://www.linux-wlan.org/docs/wlan_adapters.html.gz) 
So, now we know that I'm dealing with an Atheros chipset.

Hope this helps!	

**LinuxRobot**  :)[/QUOTE]
 OK
since your fresh install probably recognized your D-link card, try this to see if it works first:
[QUOTE=jaykay]Here is a simple and easy way to get the Netgear Wg511T card up and running in easy steps. In 5 minutes you will be up and running.

1. start up a root console

2.type: **iwconfig** ( this will give you your card info and network /wireless info)

3. type: **iwconfig ath0 channel 6** ( substitute channel 6 for whichever channel your router is transmitting on)

4. Type: **iwlist scan** ( this may take a minute, this will give you your routers wireless settings.)

5. Type: **iwconfig ath0 essid xxxxxx** ( replace xxxxxx with your routers essid)

6. Type: **iwconfig ath0 ap xx xx xx xx xx xx**( this is the six double digit mac address required and is listed in your iwlist scan message as above.)

7. Type: **iwconfig ath0 key XXXXXXXXXX** ( replace XXXXXXXX with your own hex wep key )

8. type: **dhclient** ( this gets your dhcp sorted ) you should now be up and running.

All of the information you need is right on the screen, although  you will need to make a note of your wep key from your routers settings, as the output above may list it only as a ******** output .

Hope this helps some one.

I have testd this on various linux systems and it appears to work fine including live CDs.

One thing to note if you are using a knoppix system step 8 above will not work but you can replace it with the following command 

step 8: type: **pump -i ath0**

Good Luck 

Jaykay[/QUOTE]

If this worked, try setting the settings permanent in:
System -> Administration -> Networking

Maybe you should consider taking a backup first like described here:
[http://www.ubuntuforums.org/showthread.php?t=35087](http://www.ubuntuforums.org/showthread.php?t=35087)

If the above did'nt work out, the MadWifi is probably the solution
What went wrong when you installed it the first time?

A solution for installing MadWifi a bit diffrent from earlier is described here:
[QUOTE=IcemanV9]Your info does help me to resolve the problem with my new cardbus adapter, D-Link DWL-G650.

Here's what I did:

wget [http://otaku42.de/madwifi/madwifi-cvs-current.tar.gz](http://otaku42.de/madwifi/madwifi-cvs-current.tar.gz)
sudo apt-get install build-essential (only if you don't have it)
sudo apt-get install linux-headers-(uname -r) (again, only if you don't have it)
sudo apt-get install sharutils

tar xvzf madwifi-cvs-current.tar.gz
cd madwifi
KERNELPATH=/usr/src/linux-headers-(uname -r); export KERNELPATH
KERNELRELEASE=(uname -r); export KERNELRELEASE
sudo make
sudo make install

sudo mv /lib/modules/2.6.10-5-686/kernel/drivers/net/wireless/ath_rate/onoe/ath_rate_onoe.ko /lib/modules/2.6.10-5-686/kernel/drivers/net/wireless/ath_rate/onoe/ath_rate_onoe.ko.orig
sudo mv /lib/modules/2.6.10-5-686/kernel/drivers/net/wireless/ath_hal/ath_hal.ko /lib/modules/2.6.10-5-686/kernel/drivers/net/wireless/ath_hal/ath_hal.ko.orig
sudo mv /lib/modules/2.6.10-5-686/kernel/drivers/net/wireless/ath/ath_pci.ko /lib/modules/2.6.10-5-686/kernel/drivers/net/wireless/ath/ath_pci.ko.orig

sudo cp /lib/modules/2.6.10-5-686/net/ath_rate_onoe.ko /lib/modules/2.6.10-5-686/kernel/drivers/net/wireless/ath_rate/onoe/ath_rate_onoe.ko
sudo cp /lib/modules/2.6.10-5-686/net/ath_hal.ko /lib/modules/2.6.10-5-686/kernel/drivers/net/wireless/ath_hal/ath_hal.ko
sudo cp /lib/modules/2.6.10-5-686/net/ath_pci.ko /lib/modules/2.6.10-5-686/kernel/drivers/net/wireless/ath/ath_pci.ko

reboot (leave your cardbus in the slot)

when boot up, it will recongize the cardbus adapter (without an error message)!

To TEST ath0, I just used some commands from jaykay's instruction. AND, it works great.[/QUOTE]

Below is the original MadWifi Howto for Linux
[http://www.linux-wireless.org/Wireless/Install-HOWTO/Drivers/atheros/0.Howto.Install.Madwifi.txt](http://www.linux-wireless.org/Wireless/Install-HOWTO/Drivers/atheros/0.Howto.Install.Madwifi.txt)

Hope this helped you out a bit

---

### Post by linuxrobot on 2005-06-30
I tried the first one, and it kept saying; "*Interface does not support scanning*"
I'm going to try the second one, and I'll yet you know.

**LinuxRobot**  :)

---

### Post by Lunde on 2005-06-30
[QUOTE=linuxrobot]I tried the first one, and it kept saying; "*Interface does not support scanning*"
I'm going to try the second one, and I'll yet you know.

**LinuxRobot**  :)[/QUOTE]
 I think the message interface does not support scannng disaperes when you set the correct settings. Do you know what channel you are supposed to comunicate on? Also the essid is case sensitive.

---

### Post by linuxrobot on 2005-06-30
How do I find out my hex wep?  And how do I get my router's essid?
Is there a way to tell what channel I'm using, also?
Thanks!

**LinuxRobot**  ;-)

---

### Post by Lunde on 2005-06-30
[QUOTE=linuxrobot]How do I find out my hex wep?  And how do I get my router's essid?
Is there a way to tell what channel I'm using, also?
Thanks!

**LinuxRobot**  ;-)[/QUOTE]
 Is it your access point you're connecting to? did you set it up? The WEP or WPA is the encryption key that scrambels the information over the network if you have set the router up to use encrypted security. If not, just leave this blank. If you have, the key can be found in the routers security settings.

As for the channel, 11 or 6 is mostly used. But also this information can be found in your router configuration.

The ESSID is the name of the router / access point, this is case sensitive and can also be found in the configuration of the router. Most wireless adapters are able to scan the area for available accesspoints. This is probably not a function for your default drivers as you get the error of "Interface does not support scanning"

---

### Post by linuxrobot on 2005-06-30
I tried the second method...I ran into some problems.

Since I'm not connected to the internet, I can't get the madwifi file in line 1.  Now, I have the file on my main desktop, but I can't get Root to find it.

Same thing in line 4; I have the sharutils file on my main desktop, but Root terminal can't do it (something about an error about the file's existance)

Then on line 5, it cant find the the madwifi file.  Again, this file (the same as in Line 1) is on my main desktop.

That's how far (Line 5) I got before it stopped.

I'm trying to connect to the wireless internet I have throughout my house.
(Cable line into house, goes into the Cable Modem - Which I have the MAC number - then to the D-Link wireless router, which sends out wireless internet.  My computer picks it up with a D-Link PCI Adapter.)  So I don't know what I'm trying to connect to would be called, if its the access point, or whatever.

All I setup was installing the wireless card, and plugging the adapter to the modem.  I wasn't here when the cable guy came and installed the line and modem, so I don't know much about it.

Also, do you know how to access the router configuration?  I have Windows 98SE, if that helps.

Another thing, I don't now how "encrypted" my wireless internet is; onetime, I was messing with somebody else's laptop, at my house.  (The laptop had XP)  All I had to do was click "connect to the internet" (or whatever it said) and it was connected immediately.

I'm going to retry the first method as best I can to see if I can get some results.

**LinuxRobot**   :???:

---

### Post by linuxrobot on 2005-06-30
I don't know what happened but now Linux recognizes my wireless card!   :-k 

It still doesn't work though... #-o 

I still need the *hex wep key*. :confused: 

**LinuxRobot**  8)

---

### Post by Lunde on 2005-06-30
**Madwifi**
OK you probably have to make the file executable to root (Same with the shareutils).
**$ sudo chmod 775 /home/your_user_name/Desktop/filename**
[B]
Router configuration[/B]
This differs a bit from router to router, but try this:
in win98 console / dos window write
[B]
ipconfig[/B]

and the IP address you have recieved is probably something like this 192.168.1.10 if so try to access the router at ip address 192.168.1.1 in IE (first in range)
If this does not work, try the same address as your Gateway.

You may be prompted for a username and password, but it's probably written in the login if you never been there before. This should, if so be changed. This depends on your service provider and how they set it up the first time.

If you still can't access your router, pst the model number here and I'll check

**Finding your ESSID**
In your wireless connection status window you should have an identifying name of the access point, Or while it's connecting it displays something like "connecting to NAME", I don't remember exactly in win98 but try to click your connection and lok at the details

You don't have an WEP encryption and do not need to provide this, but this also meens that your neighbors can also connect through your accesspoint. You should look up how to set this later.

---

### Post by Lunde on 2005-06-30
Don't know if you need the key, but you need the correct ESSID and Channel

---

### Post by linuxrobot on 2005-07-01
OK, I'll try this and let you know what happens!

Thanks!

**LinuxRobot** :)

---

### Post by Lunde on 2005-07-01
[QUOTE=linuxrobot]OK, I'll try this and let you know what happens!

Thanks!

**LinuxRobot** :)[/QUOTE]
 I found a great link for somebody else with the same card as you have. This is a description of how to maek an automated script for starting the wireless network at startup.

[http://www.mybizguard.com/modules/wfsection/print.php?articleid=11](http://www.mybizguard.com/modules/wfsection/print.php?articleid=11)

**Note:** that this is not for Ubuntu, but follow the steps from: 
**edit your /etc/modprobe.conf, add the line:**

**Note2:** the **/etc/rc.d/rc5.d/** is in Ubuntu just **/etc/rc5.d/**

---

### Post by linuxrobot on 2005-07-01
[QUOTE=Lunde]I found a great link for somebody else with the same card as you have. This is a description of how to maek an automated script for starting the wireless network at startup.

[http://www.mybizguard.com/modules/wfsection/print.php?articleid=11](http://www.mybizguard.com/modules/wfsection/print.php?articleid=11)

**Note:** that this is not for Ubuntu, but follow the steps from: 
**edit your /etc/modprobe.conf, add the line:**

**Note2:** the **/etc/rc.d/rc5.d/** is in Ubuntu just **/etc/rc5.d/**[/QUOTE]

OK, thanks!
I'm going to be out of town for the next 3 days, so I wont be able to do anything until after that.  When I get back I'll try the link.  Oh, real quick; how do you save a Root Terminal file?  The guy at MyBizGuard, said *save* the file.  I haven't yet figured that out. :roll: 
Until Tuesday! ;-) 

**LinuxRobot** :)

---

### Post by linuxrobot on 2005-07-07
Well, I'm back now!
I getting a little tired of the internet problem right now, so I would like to take a little break (if you don't mind) and work on getting the sound working.
Thanks!

**LinuxRobot**  8)

---

### Post by linuxrobot on 2005-07-10
Hello,
I was asking around at [http://www.linuxquestions.org/](http://www.linuxquestions.org/) to see if there was a Linux distro that could recognize and configure my wireless card for me.
One of the guys said SimplyMEPIS, worked for him with the same card.  So, I tried that and it worked.  I decided to download it and replace Ubuntu for now.  I liked Ubuntu better, but I want to learn the basics of Linux before I have to do a lot of coding.
I'm getting a new computer in the next few months, and I'm going to do a dual boot (Win XP and Ubuntu)  So, I'll be back in a while...

Thanks for all your help!
**LinuxRobot**  :smile:

---

