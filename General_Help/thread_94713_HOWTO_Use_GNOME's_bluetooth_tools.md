---
title: "HOWTO: Use GNOME's bluetooth tools"
date: 2005-11-24
forum: General Help
---

### Post by Randy Sparks on 2005-11-24
I've been playing around trying to use the GNOME bluetooth tools to transfer files to and from my mobile phone (a Nokia 6680). Somebody's already posted a message here about using KDE bits and pieces to do this, but I wanted to explore the more elegant GNOME tools. So here's how it's done.
[B]
INSTALLING GNOME-BLUETOOTH[/B]
- assuming your system is configured to use the online software repositories, open Synaptic Package Manager and search for gnome-bluetooth.
- choose to install gnome-bluetooth. There's no need to search for and install the bluez utilities because, under Ubuntu 5.10, they're installed by default
[B]
SENDING FILES TO ANOTHER DEVICE[/B]
You'll need to create a desktop shortcut for this to work: 
- right-click on the desktop and click Create Launcher
- in the Name field, type something like "Send file via bluetooth". 
- in the command field, type gnome-obex-send
- give it a cool icon if you wish (I like the road icon near the top of the list)
- Click OK to create the shortcut.
- from now on, just drag and drop a file onto the shortcut to send it via bluetooth. You'll then be able to choose your device in the dialog that comes up (assuming that your phone is set to be "visible" so it can be detected by other bluetooth devices)

**RECEIVING FILES VIA BLUETOOTH**
- click the Applications - System Tools menu and click Bluetooth File Sharing
- nothing will seem to happen but a new icon will appear top right of the screen in the system tray
- on the device you're sending the file from, choose to send the file and search for your computer. It should be called something like ubuntu-0. 
- send the file
- a dialog will appear on your PC asking if you want to receive the file. Click Yes
- the file will be saved to your Home folder
- you can add this program to your startup by clicking System - Preferences - Sessions, and clicking the Startup tab. The program's called gnome-obex-server

And that's all there is to it. There's another component installed along with gnome-bluetooth called Bluetooth Manager. I don't know what this does. It can see my phone after searching for some time but when I click on Properties it just doesn't do anything. Similarly, if I try and pair my phone to Ubuntu, I'm asked for a PIN code, yet I haven't been supplied with any by the Gnome-Bluetooth tools. If anybody knows of any documentation for Gnome-Bluetooth (the official website has none), post it below.

---

### Post by Randy Sparks on 2005-11-24
I've just realised that this HOWTO will only work with phones that don't have to be paired before they can transfer files. My 6680 doesn't need pairing to swap files but I think some, like the Sony model a friend of mine had, aren't as easy going.

Doing some more research found the following thread which, half way down, seems to solve the pairing issue via a tweaked config file. I haven't tried this myself:

[http://www.ubuntuforums.org/showthread.php?t=28312&highlight=gnome-bluetooth](http://www.ubuntuforums.org/showthread.php?t=28312&highlight=gnome-bluetooth)

To quote from the thread:

```
i know its quite an old thread, but in case anyone is 
still wondering, I managed to fix this issue by changing 
hcid.conf to use /usr/bin/bluepin instead of bluez-pin and 
then restarting bluez-utils with /etc/init.d/bluez-utils restart.
```

---

### Post by TheCondor on 2005-12-11
Hello, has anyone figured a way to transfer the contacts from the cell phone to the pc?? 

Ive tried and tried with several how-tos and applications but nothing worked.

---

### Post by pek on 2006-02-09
yeah! i'm looking for a way to sync my ngage to evolution too.

---

### Post by Garyu on 2006-02-11
thank you thank you thank you.

I previously found the HOWTO on the KDE equivalent, but it didn't work for me at all. But the gnome tools work flawlessly. Great job! =)

---

### Post by FrankTM on 2006-02-11
very nice... thank you very much

got it working with the greatest of ease with my 6230i

---

### Post by almostlinux on 2006-02-12
works great .. thanks a lot

---

### Post by engla on 2006-02-12
Sending from the computer works.. I'm thrilled so far.

However, I can't recieve a thing from the phone.. I've paired them up, but when sending it just says "It's not possible to send" after a short delay.

....

Am I dreaming? Five minutes later recieving files just works. Nifty!

---

### Post by index_0@ya.com on 2006-02-12
hi , 
i have searched and tired , is thr any way to send files to the phone to different folder other than inbox , My ngage phone is very limited with memory ,

pls guide ,

---

### Post by Garyu on 2006-02-12
[QUOTE=index_0@ya.com]hi , 
i have searched and tired , is thr any way to send files to the phone to different folder other than inbox , My ngage phone is very limited with memory ,
[/QUOTE]

I'm not sure, but I don't think this can be controlled from Ubuntu. You should probably read your phone manual and see if there are settings in your phone that allows this.

---

### Post by theh0g on 2006-03-19
Hmm, all this worked, pairing works and I can send stuff to my phone (N70), but I can't seem to send images from phone to PC. Any ideas? It just says "Sending failed"

---

### Post by abgpt on 2006-03-25
This is a really great article, thanks for such a nice info...

---

### Post by jannol on 2006-03-26
Works great with my Z1010, thx

---

### Post by lordofkhemenu on 2006-04-02
Works perfectly with my Nokia 6682 and Kensington USB BT "dongle"

---

### Post by bigken on 2006-04-08
Thanks works a treat on my V3 razor :)

---

### Post by ruffneck on 2006-04-10
Thanks! Works great with Motorola V3 razor and Zonet Bluetooth USB Dongle. Thanks alot.

---

### Post by rado_london on 2006-04-11
Works great with N70. I use this method to receive files and also I use KDE bluetooth to send.

Cheers

---

### Post by rykel on 2006-04-11
[QUOTE=Randy Sparks]
**RECEIVING FILES VIA BLUETOOTH**
- click the Applications - System Tools menu and click Bluetooth File Sharing... There's another component installed along with gnome-bluetooth called Bluetooth Manager.[/QUOTE]

Hi,

I am trying to send files to my laptop from my Sony Ericsson Z520i, but I can't find the two programs you mentioned above... neither the Bluetooth File Sharing menu entry (it's not there!) nor the Bluetooth Manager...

Any help please?

---

### Post by hopspitfire on 2006-04-12
it works amazingly well on my treo650, thank you

---

### Post by rado_london on 2006-04-12
Fire up the menu editor and check the 2 programs. By default they were hidden for me.

---

### Post by illuniel on 2006-05-13
Great! Wonderful Shortcut! yet, can I just put a 'send via Bluetooth'  option on the right click menu? 

something like:
[http://usefulinc.com/software/gnome-bluetooth/nautilus-send.png](http://usefulinc.com/software/gnome-bluetooth/nautilus-send.png)

---

### Post by Lord Illidan on 2006-05-14
[quote=illuniel]Great! Wonderful Shortcut! yet, can I just put a 'send via Bluetooth'  option on the right click menu? 

something like:
[http://usefulinc.com/software/gnome-bluetooth/nautilus-send.png]("http://usefulinc.com/software/gnome-bluetooth/nautilus-send.png")[/quote] 
I did something similar with Nautilus Scripts.

All I did was fire up Nautilus.

Then I clicked on File.

Then Scripts.

Then I made a new text file there with gedit, and put this in it.

```
#!/bin/bash
gnome-obex-send $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS
``` 
Then save it as send-bluetooth  (or anything you like) and exit gedit.

Right click on the file. Open permissions tab, and make it owner -> execute.

Then right click on any file, and chose scripts -> send-bluetooth from the right click menu.

---

### Post by adam.tropics on 2006-05-23
[http://packages.debian.org/unstable/gnome/nautilus-actions]("http://packages.debian.org/unstable/gnome/nautilus-actions")

The Link above is to a db package (that does work fine on Ubuntu) of Nautilus Actions Configurator.
Makes adding context options very simple in nautilus. Install then 

System-->Preferences-->Nautilus Actions Configuration

---

### Post by adam.tropics on 2006-05-23
I forgot! Does anyone know where or if there is a way to specify the **incoming** destination folder. Say /home/adam/nokia rather than /home/adam ??

And has anyone, amongst the massive amount of info available managed to filter out a way to allow a bluetooth device to make use of the local network net connection? I am trying, but am suffering 'tomanyhowtositus' badly!

---

### Post by Roner on 2006-05-28
You can easily manage the contacts and the SMS messages of any gsm bluetooth phone. 

With the phone's bluetooth activated, type in the terminal
```

hcitool inq

```

This will provide you with the phone's bind address, in the form of 11:22:33:44:55:66.  When you have that address, type in a terminal (you can later create a bash script and a launcher that opens in a terminal, if you wish):
```

rfcomm connect 0 11:22:33:44:55:66 1

```
Naturally, replace the 11:22:33:44:55:66 with the address provided by the hcitool.

Now your phone is recognized as a new serial device attached to the computer, until you hit Ctrl+C in the terminal.  That device is /dev/rfcomm0.

Next you can apt-get either kmobiletools or gnokii; both provide a similar functionality, although kmobiletools (available in Dapper only) worked slightly better for me, and was more pleasant to the eye.  In Dapper they will add entries to your Accessories menu.

When you first run kmobiletools, there will be an error message (because it cannot find your phone with its default configuration) and the configuration screen will appear.  Change the device to /dev/rfcomm0, and you are good to go.

In gnokii it is a little more complex: you must edit the file /etc/gnokiirc and make sure that the only port defined is /dev/rfcomm0, and that the model is AT (the file contains very useful descriptions).  The file also mentions options for direct bluetooth connection, but I have not tried that.

My phone is a Motorola L6 (slvr), but I think this should work on any gsm bluetooth phone.

---

### Post by Roner on 2006-05-28
While we're at it, I just figured out how to use a bluetooth GSM phone as a modem, in a simple - and cheap - configuration.  Using this configuration you will dial with your phone to the ISP of your choice, get connected in very slow speeds, but be charged only for your airtime.  It's execellent for checking email and doing very basic IMing, but not for anything more substantial.

1. Follow the initial steps in my previous post to create /dev/rfcomm.

2. Make sure you know which of your serial ports (/dev/ttySX, with a capital S, and X a number between 0 and 3) is not in use.  This is important, because you will otherwise disable one of your serial devices.  You can discover this by a method of trial and error; I believe any modifications you make here will be reset upon the next boot.

Remove that unused device. For ttyS1, you will type:
```

sudo rm /dev/ttyS1

```

Create a link to your working /dev/rfcomm0 connection:
```

sudo ln -s /dev/rfcomm0 /dev/ttyS1

```

While your rfcomm connection is still up, run the following command:
```

sudo dpkg-reconfigure wvdial

```

This will prompt you with the phone number to dial, your username and your password, and configure your phone.  Just to make sure, check that the resulting file, /etc/wvdial.conf, has your phone's AT commands and your connection info.

To connect from a terminal, type
```

sudo wvdial

```

And that should take care of everything.  When you want to disconnect, hit Ctrl-C in the terminal running wvdial.  It will also disconnect rfcomm.

As I said before, this configuration will probably not last into the next boot, so you might want to create a shell script that does everything (you will not need to reconfigure wvdial again, just the hardware).  The script can be something like this:

```

bin/bash

rfcomm connect 0 11:22:33:44:55:66 1 &
sleep 10
sudo rm /dev/ttyS1
sudo ln -s /dev/rfcomm0 /dev/ttyS1
wvdial

```
(Change the 11:22:33:44:55:66 to your phone's bind address.)

Please let me know if someone comes up with a more elegant way to get wvdial to recognize rfcomm.  On my custom kernel it only scans ttyS0 through ttyS3.

**EDIT:** I did find a more elegant solution.  After you go through all of the steps above and have your /etc/wvdial.conf file completely configured, edit it, and replace the line 

```

Modem = /dev/ttyS1

```
with
```

Modem = /dev/rfcomm0

```

Now you can modify the bash script and take out deleting /dev/ttyS1 and creating a link to /dev/rfcomm0.

---

### Post by adam.tropics on 2006-05-29
Sounds good. I am currently trying to get the phone to use it's bluetooth connection to connect to the pc, then get online through the broadband connection. Sounds unnecessary, but my phone provider, virgin, limits you to gprs within the virgin domain! That sucks!

---

### Post by bluenova on 2006-06-05
Nice touch, but how can I make

$NAUTILUS_SCRIPT_SELECTED_FILE_PATHS

Accept file names with spaces in them?

---

### Post by irw on 2006-06-06
have you tried a '\' before the spaces?
eg. name\ with\ spaces\ in\ it

---

### Post by Footissimo on 2006-06-06
[QUOTE=adam.tropics][http://packages.debian.org/unstable/gnome/nautilus-actions]("http://packages.debian.org/unstable/gnome/nautilus-actions")

The Link above is to a db package (that does work fine on Ubuntu) of Nautilus Actions Configurator.
Makes adding context options very simple in nautilus. Install then 

System-->Preferences-->Nautilus Actions Configuration[/QUOTE]

Apologies for newbieness, but would you mind explaining how to configure to do a right-click send via bluetooth using this?

---

### Post by Kenzy on 2006-06-09
> **Roner]While we're at it, I just figured out how to use a bluetooth GSM phone as a modem, in a simple - and cheap - configuration.  Using this configuration you will dial with your phone to the ISP of your choice, get connected in very slow speeds, but be charged only for your airtime.  It's execellent for checking email and doing very basic IMing, but not for anything more substantial.

1. Follow the initial steps in my previous post to create /dev/rfcomm.

2. Make sure you know which of your serial ports (/dev/ttySX, with a capital S, and X a number between 0 and 3) is not in use.  This is important, because you will otherwise disable one of your serial devices.  You can discover this by a method of trial and error said:**
> 

Thanks for a nice howto, I tried that, and I think that I'm very very close to reach the connection... but:
[quote]
--> WvDial: Internet dialer version 1.55
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
--> Sending: ATQ0
--> Re-Sending: ATZ
--> Modem not responding.

When running the sudo wvdial-line, my phone (Nokia N70) shows that there's activity in bluetooth-connection, but does nothing. I would appreciate if you could post your wvdial.conf here, so I could figure out what's wrong..](*,)

---

### Post by matthewc on 2006-06-16
It's a happy day indeed when a linux install CD detects and sets up my wireless connection without any user intervention, leaving me to play around with bluetooth (who would have thought!) ...and it's working. I got the message asking for a password (on my phone) at first, but after loading up Bluetooth Manager (in ubuntu) and locating my phone, it seems that got my phone and pc to pair, and now I can send images back and forth from my phone camera to the PC. Nice work gnome-bluetooth! Synchronising my addressbook and (maybe, just maybe) getting mobile internet over bluetooth set up can wait for another day - I'll post back here if I get anywhere with that.

---

### Post by tripppy on 2006-06-20
i can surf the net with my 6600 thru dapper.
i can send and receive files with dapper.



how do i auto accept all files from all phones without authorizing them first?

how do i change the directory they save to?

---

### Post by Kenzy on 2006-06-21
[QUOTE=tripppy]i can surf the net with my 6600 thru dapper.
i can send and receive files with dapper.



how do i auto accept all files from all phones without authorizing them first?

how do i change the directory they save to?[/QUOTE]

Could you tell us how did you manage to get your internet working via bluetooth? I've tried propably all the ways with my Nokia N70, but no internet.

The questions you asked... I don't know how do you get these things working in Gnome, but in KDE you have a tool called "kdebluetooth" that has an option to save phones or other bluetooth-devices in "trusted" list. It's a little bit easier and nicer tool than Gnome's obexserver.

---

### Post by phatmonkey on 2006-07-27
> **Lord Illidan said:**
> I did something similar with Nautilus Scripts.

All I did was fire up Nautilus.

Then I clicked on File.

Then Scripts.

Then I made a new text file there with gedit, and put this in it.

```
#!/bin/bash
gnome-obex-send $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS
``` 
Then save it as send-bluetooth  (or anything you like) and exit gedit.

Right click on the file. Open permissions tab, and make it owner -> execute.

Then right click on any file, and chose scripts -> send-bluetooth from the right click menu.
That should be:

```
#!/bin/bash
gnome-obex-send "$NAUTILUS_SCRIPT_SELECTED_FILE_PATHS"
```

... or it won't work with filenames with spaces!

---

### Post by camman on 2006-09-02
Thanks to all, good thread.

Nokia 6230 now connecting to dapper on Compaq nx8220 through built-in bluetooth.
Using /dev/ttyS30 for serial device.

---

### Post by Dual Cortex on 2006-10-17
Great! Sending mp3 file to nokia 6265 worked perfectly using a tiny D-Link DBT-120 Bluetooth adapter.
Im surprise at how fast I was able to make something work that was somewhat 'networkish' related.

---

### Post by jakonj on 2006-11-15
nope, on my xubuntu 6,10 final this is not working. I instaled bluez (with all dependencies) and still im stuck with it. I tried gnome-bluetooth but then i can send only files to pc but not to mobile :(

i have MSI btooth (class2) and nokia 7610

help? please?


m.p. i looked at [https://help.ubuntu.com/community/BluetoothSetup](https://help.ubuntu.com/community/BluetoothSetup) but i couldn`t find any solution (i hate console so i need gui tool). i`m not linux expert so...

---

### Post by bolognese on 2006-11-15
That's strange...I can only send to my phone, not to the computer. The phone keeps asking for a password (pin?), that seems to be false everytime. I don't know how to handle this pin thing.

---

### Post by jakonj on 2006-11-15
i belive that default pin is 12345 (or something like that ;) )

---

### Post by bolognese on 2006-11-15
12345 wasn't the right one. Have to look for "something like that.":confused:

---

### Post by bigken on 2006-11-15
its 1234 well that worked for me :-k

---

### Post by apalacheno on 2006-11-28
Nice thread!
One of the things I'm still missing is a way to read all sms messages from my Nokia 6230i. I know it should be possible with KMobileTools, but I'd rather not install the whole KDE environment to get only one application running.
Is sms reading possible with a nice GNOME app? :)

---

### Post by bmhm on 2006-11-28
[FONT="Verdana"]Got a Samsung SGH-D500

I can recieve files with gnome-bluetooth (this littl icon)

but when I try to send to my phone, I always get "could not pair"

oddly enough, my phone asks me for a code. Altering hcid.conf didn't work, didn't matter what I tried.

Any Idea?[/FONT]

---

### Post by pavel_kbc on 2006-11-29
wow its works for me :D

---

### Post by cvmostert on 2006-12-16
Thank you for the Launcher for sending files from pc, it was what i was missing. I somehow seemd to get my phone paired with my pc aswell... it is a mystery, a great one!

---

### Post by Circus-Killer on 2006-12-19
strange, cant seem to get my D600 paired. my computer cant see my phone, my phone cant see my computer.

when i do lsusb and other stuff it shows my bluetooth device, just actual bluetooth not working. #-o

---

### Post by dcstar on 2007-01-06
> **apalacheno said:**
> Nice thread!
One of the things I'm still missing is a way to read all sms messages from my Nokia 6230i. I know it should be possible with KMobileTools, but I'd rather not install the whole KDE environment to get only one application running.
Is sms reading possible with a nice GNOME app? :)

If you want to run a KDE app in Gnome then all it does is install the required files for running any KDE apps, not "the whole KDE environment", it is not a problem.

---

### Post by mrmailer on 2007-02-02
Hmm, I am using Moto Q for Sprint and have the same problem with wvdial...

rfcomm connect 0 00:1A:77:ED:D1:97 1
Connected /dev/rfcomm0 to 00:1A:77:ED:D1:97 on channel 1
Press CTRL-C for hangup


wvdial
--> WvDial: Internet dialer version 1.54.0
--> Warning: section [Dialer Defaults] does not exist in wvdial.conf.
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
--> Sending: ATQ0
--> Re-Sending: ATZ
--> Modem not responding.


any ideas?

---

### Post by mrmailer on 2007-02-02
Every time I use gnome-obex-send, it acts ok on pc side, but on phone it says...

(moto q)
"bluetooth authorization...."
... was received and cannot be put into pocket outlook

do you want ot save this file in your "\" folder?


and i put yes

but where did it go?  it's not in root dir under file manager.

---

### Post by ctsdownloads on 2007-02-06
Worked great in Dapper, but in Edgy...NOPE (Three machines and two dongles). Glad I upgraded...lol.

Hopefully we can wait a little while before breaking the ability to *receive* files with bluetooth with the next release. :roll:

---

### Post by mrmailer on 2007-02-06
I got my Moto Q working with it after changing the channel to 4.

For you who are having problems with wvdial and DUN here, you need to find out what the DUN channel is on your bluetooth phone.

---

### Post by Coburn on 2007-02-12
> **adam.tropics said:**
> [http://packages.debian.org/unstable/gnome/nautilus-actions]("http://packages.debian.org/unstable/gnome/nautilus-actions")

The Link above is to a db package (that does work fine on Ubuntu) of Nautilus Actions Configurator.
Makes adding context options very simple in nautilus. Install then 

System-->Preferences-->Nautilus Actions Configuration

This package is now in the Ubuntu repositories.:popcorn:

---

### Post by CybaCowboy on 2007-02-13
> **Randy Sparks said:**
> **RECEIVING FILES VIA BLUETOOTH**
- click the Applications - System Tools menu and click Bluetooth File Sharing
- nothing will seem to happen but a new icon will appear top right of the screen in the system tray

> **rado_london said:**
> Fire up the menu editor and check the 2 programs. By default they were hidden for me.

These icons aren't available and when I try to edit my menu, I cannot find any icons that might be the ones you're referring to!

Can someone please help me?

---

### Post by CybaCowboy on 2007-02-13
> **Randy Sparks said:**
> **INSTALLING GNOME-BLUETOOTH**
- assuming your system is configured to use the online software repositories, open Synaptic Package Manager and search for gnome-bluetooth.
- choose to install gnome-bluetooth. There's no need to search for and install the bluez utilities because, under Ubuntu 5.10, they're installed by default
[B]
SENDING FILES TO ANOTHER DEVICE[/B]
You'll need to create a desktop shortcut for this to work: 
- right-click on the desktop and click Create Launcher
- in the Name field, type something like "Send file via bluetooth". 
- in the command field, type gnome-obex-send
- give it a cool icon if you wish (I like the road icon near the top of the list)
- Click OK to create the shortcut.
- from now on, just drag and drop a file onto the shortcut to send it via bluetooth. You'll then be able to choose your device in the dialog that comes up (assuming that your phone is set to be "visible" so it can be detected by other bluetooth devices)

I've done this, with Synaptic showing that "gnome-bluetooth *is* installed, however when I drag a file onto the send-to icon on my desktop, I am told:
[I]
There was an error launching the application.
Details: Failed to execute child process "gnome-obex-send" (no such file or directory)[/I]

Any ideas?


> **Randy Sparks said:**
> **RECEIVING FILES VIA BLUETOOTH**
- click the Applications - System Tools menu and click Bluetooth File Sharing
- nothing will seem to happen but a new icon will appear top right of the screen in the system tray

> **rado_london said:**
> Fire up the menu editor and check the 2 programs. By default they were hidden for me.

These icons aren't available and when I try to edit my menu, I cannot find any icons that might be the ones you're referring to!

Can someone please help me?

---

### Post by Cody Krodle on 2007-02-14
I can't get the device finder to find my phone. It will search all day long but never find it!!

---

### Post by Cody Krodle on 2007-02-14
Nevermind my previous post... I did get the shortcut method to work, but i had to do it a little different. When i created the shortcut and would drag a file to it, a search box would appear and attempt to search for bluetooth devices. Well it would search for ever and never find my phone. So instead i went to the terminal and used "hciscan" to find my phone's mac address. After that i edited the shortcut's command field to: gnome-obex-send -d (my phone's mac address). Now that shortcut will send files to my phone. I guess if i use another phone i will need to create another shortcut. Not as convient as i would like but i guess it will do.

If anybody knows how to fix the problem with the GUI not being able to find devices.... please let me know! thanks

---

### Post by purfier on 2007-02-16
Nice thread:)

Sending files from my phone( SE K800i ) to my pc did work with the gnome-bluetooth pack and what that brings. But to get the "send to" in nautilus to work I did install every bluez-* back and obex* pack. Now it works great:) Dont know the exact pack that did solve the problem but recommend you guys having problems sending files to your phone do that and try:)

---

### Post by mrmailer on 2007-02-16
I can't do it:(  My moto Q says, when i try to send it to my desktop, that it;s not supported or whatever.

Did you need to do something special for bluez?  konqueror bluetooth:/// works

---

### Post by tipping point on 2007-04-09
Thanks for how-to, works great with Edgy & Nokia 6600. I could previously send to Ubuntu PC,now I can also receive.

---

### Post by trondhuso on 2007-05-08
> **adam.tropics said:**
> I forgot! Does anyone know where or if there is a way to specify the **incoming** destination folder. Say /home/adam/nokia rather than /home/adam ??

And has anyone, amongst the massive amount of info available managed to filter out a way to allow a bluetooth device to make use of the local network net connection? I am trying, but am suffering 'tomanyhowtositus' badly!
As asked above: Where do you tell where to put incoming files. I get the desktop cluttered with whatever I get from the phone.

I would also like to know if it is possible to get rid of the "this file is downloaded what do you want to do with it" message that pops up everytime you get something from your external bluetooth device.

trond

---

### Post by sabrewolf2006 on 2007-06-07
> **trondhuso said:**
> As asked above: Where do you tell where to put incoming files. I get the desktop cluttered with whatever I get from the phone.

I would also like to know if it is possible to get rid of the "this file is downloaded what do you want to do with it" message that pops up everytime you get something from your external bluetooth device.

trond

gconf-editor and navigate to /apps/gnome-obex-server
there is a key called savedir.. set it to whatever you want and it will save all files received via bluetooth there..

from my experience if you click 'automatically accept files' in the first dialog when a file is sent to the computer it no longer asks what you want to do with the file.. YMMV

Hope this helps

---

### Post by ema_3344 on 2007-06-30
Mmm I have created the launcher but it won't find my phone.

My phone won't find my computer either.

Any ideas what's wrong?

---

### Post by AbuAnsar on 2007-07-24
Finally managed to pair my Blackberry 8100 with Targus Bluetooth Adapter. The file transfer FROM BB to my laptop was successfully acomplished! However, I can't send anything from my computer to BB device. An error pops up saying: "Remote device doesn't support receiving objects" 


NOTE: I'm using a media card on my blackberry device. The files I unsuccessfully tried to send to my phone were of .jpg and .mp3 format.

Thanks!

---

### Post by AbuAnsar on 2007-07-24
I've just solved the problem. simply had to hit on Receive trhough Bluetooth button on my Blackberry :)

---

### Post by AbuAnsar on 2007-07-24
> **ema_3344 said:**
> Mmm I have created the launcher but it won't find my phone.

My phone won't find my computer either.

Any ideas what's wrong?

in your terminal type :

sudo hciconfig hci0 reset
password:

(thus, it will manually start your bluetooth). then, turn on the bluetooth on your phone and type the followin command  in the terminal:

hcitool scan

it should pair your compute with your phone. 

NOTE: you have to run "sudo hciconfig hci0 reset" in your terminal evey time you plug you bluetooth device into the USB port.

i hope this will help.

---

### Post by Psyphre on 2007-08-19
When i send a file over, it asks on my phone to type a password in. I have tried 1234, 12345 etc but no luck. Also it says "failed to connect to remote device" after i type something in, I dont know if thats just cos I got the wrong password, or because it actually cant connect. Im confused :S

---

### Post by johnfarrow on 2007-08-25
Anyway to use this to connect a bluetooth headset to computer so as to allow listening to audio from the computer?:)

---

### Post by BeastlyKings on 2007-09-11
I can send files to my PC but I cannot send them from my PC to my phone, mainly because it cannot find my phone.

Help?


EDIT: I did "hcitool scan" and my phone was found but it doesn't show up in the "Send File" window...

---

### Post by vcallaway on 2007-09-23
I'm going through the same issue.

I did find this tidbit.  The gnome-obex-send not finding the devices was cured by the command:

sudo hciconfig hci0 inqmode 0

I am starting to think I have a crippled blackberry model.

---

### Post by richharding1 on 2007-10-15
I spent a few hours on Saturday night trying to get my laptop to pair with my bluetooth enabled LG phone using GNOME's bluetooth tools.  Finally I gave up and went to bed.  The next morning, for some reason, I decided to install KDE as an alternative desktop environment and ended up downloading the KDE bluetooth tools.  VOILA! Now I'm able to push objects back and forth between my laptop and my phone with ease.  Leaves me wondering if the support for Bluetooth might be easier to use in the KDE environment?  All in all, I am most pleased with GNOME, but this particular feature was much easier for me to set up with the KDE tools.

---

### Post by vishzilla on 2007-10-15
i used this [guide]("http://www.linuxquestions.org/linux/answers/Hardware/Bluetooth_Transferring_and_receiving_files_under_Ubuntu")

it worked for me

---

### Post by estanton on 2008-04-25
Is there a new method to do this in Hardy? Apparently gnome-obes-send is not supported any more.

---

### Post by trondhuso on 2008-05-03
> **sabrewolf2006 said:**
> gconf-editor and navigate to /apps/gnome-obex-server
there is a key called savedir.. set it to whatever you want and it will save all files received via bluetooth there..

from my experience if you click 'automatically accept files' in the first dialog when a file is sent to the computer it no longer asks what you want to do with the file.. YMMV

Hope this helps
Perfect. Thanks a lot.

---

### Post by Random20230808 on 2008-05-04
I use 8.04 Hardy Heron.
The gnome-bluetooth package works great for sending and receiving files from Motorola A1200 mobile phone.
You have to start gnome-bluetooth every time you want to send/receive files.
For automatic start you may read this one : [https://help.ubuntu.com/community/BluetoothSetup?highlight=(bluetooth)#head-f2239aaaf93d4186c83d5f57aa893e1dd108681d]("https://help.ubuntu.com/community/BluetoothSetup?highlight=(bluetooth)#head-f2239aaaf93d4186c83d5f57aa893e1dd108681d")

---

### Post by abhister on 2008-05-23
works gr8...no probs...thanks

---

### Post by karan mangat on 2008-07-13
got the gnome-bluetooth (synaptic) (using Hardy 8.04),
but executing gnome-obex-send in terminal shows command not found.

---

