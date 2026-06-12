---
title: "Mobile Broadband Connection - Verizon USB727 | 7.10 &amp; 8.10 HOWTO"
date: 2008-10-30
forum: Hardware
---

### Post by rileyporter on 2008-10-30
I recently was in the market for a USB CDMA connection through verizon that would work in linux.  

ONE THING TO NOTE:  Before using this card in Linux I think it is required that you run the Verizon software that came with it and connect to the net on a windows machine for the first time.  Once it connects once it will work in linux NP.


The card I found that works OUT OF BOX (8.10 that is,7.10 needs to install gnome-ppp) 

The Verizon [USB727]("http://www.verizonwireless.com/b2c/store/controller?item=phoneFirst&action=viewPhoneDetail&selectedPhoneId=3304") Card. 

I have upgraded to the 8.10 RC and there is a cool feature in the network manager applet.  The ability to connect to a mobile broad band connection through the applet.  


1.  Right click on the network manager applet on the top right portion of the screen and click edit networks.
2.  Click the mobile broadband connection and click add.
3.  Press forward. Then select T-MOBILE Internet.
4.  Name is something like "Verizon GPRS" err whatever
5.  Apply.
6.  Click edit on the newly created connection.
7.  Change the default number to #777 (THIS IS FOR VERIZON)
8.  Delete the APN string.
9.  Fill in the username:  with your cards phone number
10. Fill in your password with vzw
Press OK

To Connect:
Click on the top right network applet and select "Auto Mobile Broadband Connection (CDMA)

Browse and enjoy.

----------------------------------------------------------------------
FOR 7.10 Users
----------------------------------------------------------------------

For those of you who are not running the RC 8.10 you can still connect using this card by.

sudo apt-get install gnome-ppp

run gksudo gnome-ppp
click detect on the modem
change speed to 460800
on the options tab select ONLY the following:

Auto Reconnect
Check Default Route
Ignore Terminal Strings

For the username and password / phone number its the same as above.

---

### Post by orange_roughy on 2008-10-31
> **rileyporter said:**
> 
Click on the top right network applet and select "Auto Mobile Broadband Connection (CDMA)


Where is this in 8.10? What is the "top right network applet"?

Thanks very kindly,
orange roughy

---

### Post by cyphur on 2008-10-31
excellent post, thanks riley. Broadband with verizon up and working and no effort. 

this was ubuntu 8.10 and using a PCMCIA PC5750 card from verizon. 

thanks man!

-cyphur

---

### Post by orange_roughy on 2008-10-31
> **cyphur said:**
> excellent post, thanks riley. Broadband with verizon up and working and no effort. 

this was ubuntu 8.10 and using a PCMCIA PC5750 card from verizon. 

thanks man!

-cyphur

I am SOOO close ! I just didn't understand the last thing he wrote "Click on the top right network applet and select "Auto Mobile Broadband Connection (CDMA)"

Cyphur, how did you get it to connect? Do you have to tell it to dial somewhere?

---

### Post by cyphur on 2008-10-31
> **orange_roughy said:**
> I am SOOO close ! I just didn't understand the last thing he wrote "Click on the top right network applet and select "Auto Mobile Broadband Connection (CDMA)"

Cyphur, how did you get it to connect? Do you have to tell it to dial somewhere?

Orange - up on the top right hand corner the network app. Left click actually, not a right click and select "Auto Mobile Broadband Connection (CDMA)" it should connect as long as you followed his instructions and ubuntu see's the card. 

i'm heading home from work here in a bit so if you need some help post up a reply i'll watch the thread till i bail.

hope that helps!

-cyphur

---

### Post by orange_roughy on 2008-10-31
> **cyphur said:**
> Orange - up on the top right hand corner the network app. Left click actually, not a right click and select "Auto Mobile Broadband Connection (CDMA)" it should connect as long as you followed his instructions and ubuntu see's the card. 

i'm heading home from work here in a bit so if you need some help post up a reply i'll watch the thread till i bail.

hope that helps!

-cyphur

Thanks for the reply, but I still don't see it. Here is a screenshot of both dialog boxes for my System->Preferences->Network Configuration applet. This is on 8.10 (Ibex). Any ideas? Maybe if you have a chance to post a screenshot of your screen, it would help?

[http://img528.imageshack.us/my.php?image=screenshotme5.png]("http://img528.imageshack.us/my.php?image=screenshotme5.png")

---

### Post by RiffRaff06078 on 2008-11-02
Does this method work for a tethered cell phone?  Not seeing the option to connect to that network in the network manager.

If not, does tethering still require Gnome-PPP?

Thanks,
Riff

---

### Post by rileyporter on 2008-11-02
Cypher: Glad this helped someone out!  Thx for the thanks.

Orange_roughy:

By looking at your desktop it would appear that you have modified the "default look" to ubuntu.  

Here is a link to the applet that is up and installed by default in Ubuntu.

[http://www.gnome.org/projects/NetworkManager/](http://www.gnome.org/projects/NetworkManager/)

This is the network applet int the "top right" that I was referring to.  You need to add this back to your menu bar so you can click on the connection that you just created to start it.  If you do not want to do this however you can just click the "auto connect" box so that when you plug in your device it picks it up by default.  Let me know if you need more help.

RiffRaff06078:
I would assume this would work via tethering.  If you can do it in gnome-ppp then you SHOULD be able to do it like this.  I could be wrong though.  I say this because there is no a place to specify like /dev/USB0 for your device.  I have not looked at the network applet code to see what its exactly doing but I would have to assume that its looking for a certain type of device to bind to by default.  So a default Bluetooth device prolly would fall under the listing of "Mobile Broadband" 

Please let me know if it works though.

Riley

---

### Post by RiffRaff06078 on 2008-11-03
Riley:

I'm not seeing the option to connect to the Verizon network under network manager using those instructions.  Any thoughts?

Thanks,
Riff

---

### Post by rileyporter on 2008-11-03
Riff:

There is not an option.  You have to select the T-Mobile Internet one then just edit that one and set it up with your verizon information.  

Re-Read my post again with this information you just read and I am sure you will understand what I am talking about.

But if you need more help just post and I will do what I can.

Riley

---

### Post by RiffRaff06078 on 2008-11-03
> **rileyporter said:**
> Riff:

There is not an option.  You have to select the T-Mobile Internet one then just edit that one and set it up with your verizon information.

No, I mean I did that already. I set up and edited a T-Mobile Internet connection with my Verizon information.  But when I click on the Network Manager icon, all I get are my available WLAN connections; no option to connect to the T-Mobile connection I set up.

---

### Post by orange_roughy on 2008-11-03
> **rileyporter said:**
> Orange_roughy:

By looking at your desktop it would appear that you have modified the "default look" to ubuntu.  

Here is a link to the applet that is up and installed by default in Ubuntu.

[http://www.gnome.org/projects/NetworkManager/](http://www.gnome.org/projects/NetworkManager/)

This is the network applet int the "top right" that I was referring to.  You need to add this back to your menu bar so you can click on the connection that you just created to start it.  If you do not want to do this however you can just click the "auto connect" box so that when you plug in your device it picks it up by default.  Let me know if you need more help.

Thanks. I got it working. I reinstalled Ubuntu and have that icon back. I never changed the default look; something happened to NetworkManager that it wasn't working after an upgrade to 8.10.

I'm going to get screenshots for all of your steps so this is easier for others.

Many thanks for doing this. I can now ditch Windows on my laptop.

orange roughy

---

### Post by rileyporter on 2008-11-03
> **RiffRaff06078 said:**
> No, I mean I did that already. I set up and edited a T-Mobile Internet connection with my Verizon information.  But when I click on the Network Manager icon, all I get are my available WLAN connections; no option to connect to the T-Mobile connection I set up.

Have you tried deleting the "Tmobile" connection and doing it again?  also.. perhaps..

```
sudo ifconfig ppp0 up
```

Of course I am assuming that your verizon card is ppp0.
If it doesn't show up look that the below commands output and see what it's listed as.  Since this was not an issue for me I am just guessing Riff.   Sorry bud that I can not help more.  What does it list anything about  Mobile Broadband at all?
```
sudo ifconfig -a 
```

---

### Post by RiffRaff06078 on 2008-11-04
> **rileyporter said:**
> Have you tried deleting the "Tmobile" connection and doing it again?
Tried deleting and recreating, that brought the option to connect to the Network Manager.  Clicking on it causes the Network Manager icon to very quickly change to the "connecting" image, then to the "not connected" image, then back to the wireless connection image, all withing a split second.


> **rileyporter said:**
> ```
sudo ifconfig -a 
```
That brings back:
```
pan0      Link encap:Ethernet  HWaddr 26:a4:af:1e:dc:a5  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-1A-73-38-29-5B-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

Tried bringing both of those connections up, with no change in ability to dial out on the cell phone.  Are you sure the APN field can be blank?  Any other suggestions?

Thanks,
Riff

---

### Post by rileyporter on 2008-11-04
What card is this?

I can only verify that the USB727 is the one I got working :)

---

### Post by orange_roughy on 2008-11-04
I can confirm this works perfectly for the Novatel USB727. Thanks again, rileyporter!

---

### Post by RiffRaff06078 on 2008-11-04
> **rileyporter said:**
> What card is this?

I can only verify that the USB727 is the one I got working :)

Well, that's just it; it's not a card.  I'm tethering my LG phone via USB cable.

---

### Post by orange_roughy on 2008-11-04
> **RiffRaff06078 said:**
> Well, that's just it; it's not a card.  I'm tethering my LG phone via USB cable.

You should read the title of this thread. It has nothing to do with LG phones. Hijacking threads isn't very nice :cry:

---

### Post by RiffRaff06078 on 2008-11-04
> **orange_roughy said:**
> You should read the title of this thread. It has nothing to do with LG phones. Hijacking threads isn't very nice :cry:

> **orange_roughy said:**
> Mobile Broadband Connection - Verizon USB727 | 7.10 & 8.10 HOWTO
I recently was in the market for a USB CDMA connection through verizon that would work in linux.

Hmmm.... you're posting about getting a Verizon USB CDMA connection working, and I have a Verizon cell phone that connects to my Verizon Mobile Broadband account via a USB port.  Not a far leap of logic there that maybe your technique would work for me.

Thread hijacking?  I think not; but my bad for wasting your time.

---

### Post by rileyporter on 2008-11-06
Not a problem Riff.  I knew that someone was trying to get the BT connection working with this but I think that they way this new update to the applet works is that its looking for specific device strings to identify what can be identified as an "mobile broadband connection" to the application I think that your "connection" just looks like a BT device not an mobile broadband device.

Riley

---

### Post by Tom.Servo on 2008-11-06
FYI: I just tried it with my Sprint Compass 597 and it works great also! Thanks for the info! You're the man!

---

### Post by jka4321 on 2008-11-21
sprint pentech 500 card works right out of the box

---

### Post by THE TECH on 2008-12-01
Any help with version 8.04 on a Dell Mini?

---

### Post by orange_roughy on 2008-12-02
After 3 fresh installs of 8.10 on 3 different laptops, I've found that I don't need the OP's instructions at all. Ubuntu 8.10 automatically detects the Novatel/Verizon USB727 automatically and dials correctly. Just plug it in and click on the top right network applet and select "Auto Mobile Broadband Connection (CDMA)"

---

### Post by dpcamp on 2008-12-08
I am not able to log in with my usb727 card. I have the connection made in the Network Manager but it doesn't connect. This is a brand new card and account. Do i need to activate it or something on a different machine before i can use it in linux?

---

### Post by orange_roughy on 2008-12-08
> **dpcamp said:**
> I am not able to log in with my usb727 card. I have the connection made in the Network Manager but it doesn't connect. This is a brand new card and account. Do i need to activate it or something on a different machine before i can use it in linux?

yes, it has to be activated. i activated mine on Windows first using the Verizon software. If you don't have Windows or OS/X (assuming there is an OS/X version of their software), bring the device to a Verizon retail store and ask them to activate it for you.

---

### Post by donwinchell on 2008-12-15
SOLVED - Just today I upgraded my network manager, everything started working
I am using ubuntu 8.10, bell mobility canada, novatel P720. The card seems to connect just fine using NetworkManager.
I can get a list of dns servers (see below) an internal and an external IP address, but I can not actually access the internet. Any ideas?
(I know the connection terminated, but I was trying to access things while it was connected)
tail -f /var/log/messages
Dec 15 15:45:17 d510 kernel: [15378.134626] PPP generic driver version 2.4.2
Dec 15 15:45:17 d510 pppd[20061]: pppd 2.4.4 started by root, uid 0
Dec 15 15:45:17 d510 pppd[20061]: Using interface ppp0
Dec 15 15:45:17 d510 pppd[20061]: Connect: ppp0 <--> /dev/ttyUSB0
Dec 15 15:45:17 d510 kernel: [15378.303635] PPP BSD Compression module registered
Dec 15 15:45:17 d510 kernel: [15378.399948] PPP Deflate Compression module registered
Dec 15 15:45:17 d510 pppd[20061]: local  IP address 76.70.135.234
Dec 15 15:45:17 d510 pppd[20061]: remote IP address 206.47.201.2
Dec 15 15:45:17 d510 pppd[20061]: primary   DNS address 206.47.201.246
Dec 15 15:45:17 d510 pppd[20061]: secondary DNS address 204.101.237.136
Dec 15 15:58:23 d510 pppd[20061]: Modem hangup
Dec 15 15:58:23 d510 pppd[20061]: Connect time 13.1 minutes.
Dec 15 15:58:23 d510 pppd[20061]: Sent 588 bytes, received 588 bytes.
Dec 15 15:58:23 d510 pppd[20061]: Connection terminated.

---

### Post by rileyporter on 2008-12-16
issue a route command and see what it says..

perhaps your default route is not working also make sure you are not connected to a ethernet connection etc.  


so run this and paste what it says..

route

---

### Post by donwinchell on 2008-12-18
Thank you riley porter for your input.
UPDATE -- while I thought everything was working, here is what I have now.
I can use broadband and wireless at the same time but I can not use broadband and network connection at the same time.
broad band works great, network works great but they don't seem to work together even if I provide and ip address (via dhpc server) to the wired connection.
99.9% THERE !

---

### Post by donwinchell on 2009-01-19
100% ! Bell canada mobile broad band .
searched some more forums and tried some things.
INSTALLED FIRE STARTER FIREWALL and used its internet connection sharing function, everything started working.

Then it stopped.  It turned out the dhcp3 was not being started.  why it stopped I have no idea.  reinstalled dhcp3-server and reinstalled firestarter.  now I seem to be functional.

oh, I also setup a fixed IP network connection that I use when doing internet connection sharing.  so I start the bell broad band, then start the fixed IP connection (I called it connection sharing), then start fire starter.  Yes actually quite a few steps, but the funny thing is the broad band starts almost instantly on ubuntu while in windows using the bell connect software it goes through a bunch of steps and actually takes a couple of minutes.

If I could only get my hard drive to stop clicking I would be 100% sold on ubuntu !  But still am dual booting with xp.  I ONLY use xp for 2 applications that just will not run on ubuntu (not with VM not with wine)
but I am about 99.5% ubuntu at this point on a dell latitude laptop

---

### Post by rileyporter on 2009-01-19
donwinchell: Glad everything is working!  However it funny that you mentioned your hard drive kept clicking... On my site I posted a fix for this.

[http://www.synthetos.com/node/4]("http://www.synthetos.com/node/4")

Follow my instructions there and it should be fixed.  In regards to your other comments about both networks working.  I assume that this is possible if you really wanted it to work.  All you need to do is setup your default gateway / route to use the correct path belonging to the correct interface.

Anyhow hope I helped.

Riley

---

### Post by donwinchell on 2009-01-20
Thanks for the reply.
well we may be getting off topic here (shifting from mobile network to hard drive clicks), 
but
I think I had been to your web site and tried 
sudo hdparm -B 254 /dev/sda
It seemed to work, for a while, then the clicking was back.
I am kind of bewildered about this because it has to be a finite software setting of some kind as my machine is dual boot.  Unequivocally and without fail, the drive does NOT click on XP ,but DOES click (sometimes) in Ubuntu. so in my mind, it is not hardware, it is not bios, it is OS level or higher.

I have also tried hdparm -B 255 /dev/sda. by the way my drive as dual boot, is sda, sda1, sda2, sda3.  my assumption is if configure sda I get all 3-4 of them).
I tried your method again  and this is the output.  
don@d510:/dev$ sudo hdparm -I /dev/sda | grep "Advanced"
[sudo] password for don: 
	Advanced power management level: disabled
	    	Advanced Power Management feature set
don@d510:/dev$ sudo hdparm -v -B 254 /dev/sda

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 IO_support    =  0 (default) 
 readonly      =  0 (off)
 readahead     = 256 (on)
 geometry      = 14593/255/63, sectors = 234441648, start = 0


so far it is NOT clicking, I will let you know if it starts again.  

I also did put it in rc.local,  previously I had put it in /etc/hdparm.conf   which also seemed to work, that is Advanced Power Management was set to disable upon reboot.
I like the rc.local thing, it look like I can put all kinds of tweaks in there.

thanks much for your help.   
Don

---

### Post by whitepaw on 2009-03-09
Confirmed this using Kubuntu 8.10 and a UM175. The networking app was diffrent than described, but I guess thats since Kubuntu used KDE and not Gnome.

---

### Post by johnnylavah on 2009-03-29
> **cyphur said:**
> excellent post, thanks riley. Broadband with verizon up and working and no effort. 

this was ubuntu 8.10 and using a PCMCIA PC5750 card from verizon. 

thanks man!

-cyphur

what did you do to get the pc5750 to work?  i cannot get it to connect even though ubuntu recognizes the card

---

### Post by euriconeto on 2009-03-30
Hi There,

Would any of you know how to set Three mobile broad band on 8.10? I just arrived in Australia and have been using a friend's one without major problems, just following the network configurations (but without changing any of the standard features).

My friend's mobile broad band is the one with a small calbe and looks like a small white soap, and mine one is a internet key modem (ZTE MODEL MF627). I tried to use in his computer (following tips from the forum) and then back in to mine, but nothing happened. I saw that there was a way to solve with other company's mobile modem, would it work for Three one? If so And about the codes for

---

### Post by euriconeto on 2009-03-30
Sorry, flicked my message without finishing it...

I was about to ask how to follow those steps (of editing internet configuration using the right click on the icon).

Cheers,
Eurico

---

### Post by GeorgeVita on 2009-04-01
Hi **euriconeto**,
regarding ZTE MF627 take a look at 

[http://ubuntuforums.org/showthread.php?t=1101251](http://ubuntuforums.org/showthread.php?t=1101251)

where another Ubuntu user solved it.

Regards,
George

---

### Post by pizza-is-good on 2010-02-03
Any idea on how to get it working in Karmic?

I just wont do it.

~pizza

---

