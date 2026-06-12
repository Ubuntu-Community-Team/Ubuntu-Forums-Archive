---
title: "How I got my Palm m500 to sync with Gnome-Pilot"
date: 2004-11-07
forum: Hardware &amp; Laptops
---

### Post by ahood on 2004-11-07
**To Ubuntu Users Having Trouble Getting USB Palm Pilot To Sync With Gnome-Pilot**

I found synching with the Palm m500 (USB connection) to be not quite as simple as I expected. I will first describe the problem I was experiencing and how I got it to sync.

[SIZE=1][I]Note #1: Getting a USB Palm Pilot has never been an easy task for me. It took me six months to get the m500 to sync using Xandros 2.0. It has now taken me a week to get it to successfully sync with Ubuntu, so it is getting easier.

Note #2: The palm cradle was connected to the computer when I installed Ubuntu Warty 4.10 (released 10-20-204). The Palm PDA was not in the cradle during installation.

Note #3: If you want the immediate answer, jump to the summary at the bottom of this message.[/I][/SIZE]


**THE PROBLEM**

I launched the Gnome-Pilot tool and the configuration wizard began.
[B]
[COLOR=Blue]Wizard Screen #1:[/COLOR][/B] Introduction screen. Click Forward

**[COLOR=Blue]Wizard Screen #2:[/COLOR]** I changed the settings to the following...

_Default Settings:_
Name: Cradle
Connection Speed: 9600 (default was 5600)
Device: /dev/ttyUSB1 or /dev/ttyUSB0 (default was /dev/pilot)
Timeout: 20 (default was 2)

**[COLOR=Blue]Wizard Screen #3:[/COLOR]** You are asked if you have sync'd the device previously (i.e., if the PDA has a user name and data entered already). Default is 'Yes'.

**[COLOR=Blue]Wizard Screen #4:[/COLOR]** You are instructed to press the 'SYNC' button on the cradle

**PROBLEM:** After I pressed the sync button on the cradle, nothing happened. It refused to carry out the sync operation. No matter what settings I used in Wizard Screen #2, it absolutely would not sync.


**HOW I FOUND THE SOLUTION THAT SOLVED THE PROBLEM**

I found the solution to this problem after I read the following post [Treo600](http://ubuntuforums.org/showthread.php?t=3328&highlight=palm). This post led me to the following website ([Linuxbroker - PalmOS-HowTo](http://howtos.linuxbroker.com/howtoreader.php?file=PalmOS-HOWTO.html#PC-CONNECT)) that eventually had the tip I needed to resolve the synching problem.

Because the link above is a long page, the specific text I am referring to is the following:

> Once USB support is set up, you should use device /dev/ttyUSB1 to communicate with your PDA. Note that this device name only exists after you have pressed the hotsync button on the cradle. You must press the button before running the connection software.

**THE SOLUTION - GETTING USB PALM m500 TO SYNC**

(1) I launch the Gnome-Pilot wizard
(2) I changed the settings in Wizard Screen #2 to the following:

Default Settings:
Name: Cradle
Connection Speed: 9600
Device: /dev/ttyUSB1 
Timeout: 20

(3) I PRESSED THE SYNC BUTTON ON THE CRADLE BEFORE GOING TO WIZARD SCREEN #3

(4) I then proceeded to Wizard Screen #3 (see above for what this screen asks).

(5) I then proceeded to Wizard Screen #4...

To my amazement it synched (nearly immediately!).


**SUMMARY**
The reason Gnome-Pilot refused to synch with the USB Palm Pilot m500 when Gnome-Pilot instructed me to press the 'Hot-Sync' button (on the cradle) was because the OS had not created the 'ttyUSB1' port. Only after I used /dev/ttyUSB1 AND pressing the 'Hot-Sync' button on the cradle _BEFORE_ I left the Gnome-Pilot Wizard Settings Screen (*i.e.*, the screen where you enter /dev/ttyUSB1, see Wizard Screen #2 above) was I able to achieve a successful sync.

I hope this useful to others.

Alan Hood

---

### Post by Yoda_Oz on 2005-01-30
not useful to me, sorry.

i did everything exacly as you said and it still doesnt work!

after i press the hoysync button i goto dmesg and i get:
usb 1-1: new full speed USB device using uhci_hcd and address 24
visor 1-1:1.0: Handspring Visor / Palm OS converter detected
usb 1-1: Handspring Visor / Palm OS converter now attached to ttyUSB0
usb 1-1: Handspring Visor / Palm OS converter now attached to ttyUSB1

yet gnome-pilot still hangs there as if there is nothing to connect to!
this is basically the only thing i need to get working properly for me to get rid of windows!

I hate jpilot too. the sync works in that but i would very much prefer to be able to sync with evolution or thunderbird.

any suggestions?

---

### Post by TravisNewman on 2005-01-30
It took me a long time to get mine working in Gentoo.
It took me about 10 minutes in Ubuntu, because I found this link :)
[http://howtos.linuxbroker.com/PalmOS-HOWTO.html](http://howtos.linuxbroker.com/PalmOS-HOWTO.html)
Hope it helps

---

### Post by Yoda_Oz on 2005-01-30
no matter what forum i go to people point me to that web site...

IT CONTAINS NOTHING USEFUL TO ME... 
sorry for the caps but im starting to get a little annoyed. i'm doing everything right and to the letter and to the book in TFM!

my computer can see the pilot: lsusb
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 003: ID 046d:c016 Logitech, Inc. Optical Mouse
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 032: ID 0830:0061 Palm, Inc.
Bus 001 Device 001: ID 0000:0000

and dmesg:
visor 1-1:1.0: device disconnected
usb 1-1: new full speed USB device using uhci_hcd and address 32
visor 1-1:1.0: Handspring Visor / Palm OS converter detected
usb 1-1: Handspring Visor / Palm OS converter now attached to ttyUSB0
usb 1-1: Handspring Visor / Palm OS converter now attached to ttyUSB1

i can also sync with jpilot (which is a crappy program).

i've even edited /usr/share/gnome-pilot/devices.xml to add my vendorID and deviceID in there...

i am pressing the hotsync button at the setup window screen #2.

Come on people!!! there has to be something im missing!!!

---

### Post by Viro on 2005-01-30
[QUOTE=Yoda_Oz]not useful to me, sorry.

i did everything exacly as you said and it still doesnt work!

after i press the hoysync button i goto dmesg and i get:
usb 1-1: new full speed USB device using uhci_hcd and address 24
visor 1-1:1.0: Handspring Visor / Palm OS converter detected
usb 1-1: Handspring Visor / Palm OS converter now attached to ttyUSB0
usb 1-1: Handspring Visor / Palm OS converter now attached to ttyUSB1

yet gnome-pilot still hangs there as if there is nothing to connect to!
this is basically the only thing i need to get working properly for me to get rid of windows!

I hate jpilot too. the sync works in that but i would very much prefer to be able to sync with evolution or thunderbird.

any suggestions?[/QUOTE]
 What device are you using? If it's the Palm Zire 31, I've written a HOWTO on the Ubuntu Wiki site. If it's something else, you could just post the type of Palm, and we'll try to sort it out.

Basically, you need to make sure that your Palm model is listed in the file /usr/share/gnome-pilot/devices.xml

If it isn't you need to add it.

I've just checkout pilot-link.org. The Tungsten T5 should sync using the instructions in the [Palm Zire 31 HOWTO](https://www.ubuntulinux.org/wiki/PalmZire31HOWTO). It's a very new WiKi, so do try out the instructions and if tell me whether they work, and if there is anything that I (or anyone else) can improve on in that WiKi.

---

### Post by Sirenian on 2005-04-09
I had the same problem with my Tungsten T3; did everything Ahood suggested above and it still didn't work.

I now know what the problem is and have fixed it. Here's a tiny addition to Ahood's excellent instructions:

**[COLOR=Blue]Wizard Screen #2:[/COLOR]**

_Default Settings:_
Name: Cradle
Connection Speed: 9600 (default was 5600)
Device: /dev/ttyUSB1 or /dev/ttyUSB0 (default was /dev/pilot)
Timeout: 20 (default was 2)
[COLOR=DarkRed]Connection: USB[/COLOR] (not Serial. Doh!)

It's easy to miss the small things when you're following everything to the letter.

NB: I have a cable as well as a cradle. The cable is plugged into my USB hub, and the cradle is in a USB port on my PC. I've not managed to get the cable working (can't even decipher the dev device which the T3 appears on). Cradle works fine, though.

---

### Post by Rxke on 2005-04-17
i got my Palm m500 syncing using ttyUSB3, heh...

(running on PPC architecture)

EDIT

Sigh... still no joy... Palm said hotsync succesful, but... There was some sort of errormessage that i didn't follow up, and now nothing.

i got 'success' by listing 4 palms, on USB0-4...

BTW, how do you guys restart the wizard? I only got it once...

---

### Post by Haus on 2005-06-30
[QUOTE=Rxke]i got my Palm m500 syncing using ttyUSB3, heh...

(running on PPC architecture)

EDIT

Sigh... still no joy... Palm said hotsync succesful, but... There was some sort of errormessage that i didn't follow up, and now nothing.

i got 'success' by listing 4 palms, on USB0-4...

BTW, how do you guys restart the wizard? I only got it once...[/QUOTE]
 Just thought I'd add to this...

Kyocera 7135 works when following the above advice in Hoary through the supplied USB cradle.

Added the device string into the XML file.

The gotcha that I had was that I never actually typed the DAMN port correctly!!!

I could do DMESG and it'd show me that there were the 2 TTY USB listings, but every time I tried the gnome pilot, i wouldn't type it in right.  

You gotta put /dev/ttyUSB1 and NOT /dev/USB1 !!!  DUH!

BTW, I *think* i added the updated conduits that supposedly added 7135 support, but I have a feeling it would have worked before.

Maybe that'll help at least one out there!  :P

---

### Post by Jarz Corp on 2005-08-10
Hi ahood.

Just wanted to express my gratitude.

This was so nice and so easy to do, with your tip in hand (don't go there man) it took me 5 minutes to sync with my M500.

U are my hero of the day.

Jarz Corp

---

### Post by DW5 on 2005-08-10
Got my Tungsten C connecting with this tip.

Thanks,

DW

---

### Post by lothar_m on 2005-08-10
@ ahood

i was trying to get my palm zire to work with ubuntu for about 6 months.

i had done it all. Read all the info i could get my hands into. but it just refused to sync.

Now thanks to your input it works great. a million thanks man.

---

### Post by Jacinto on 2005-08-20
Haus, please, what did you write in the xml files?. I'm doing everything that Ahood explained with no luck.. Mine is a Kyocera 7135.

Thanks a lot.

---

### Post by Jarz Corp on 2005-08-22
Okay this is slightly off topic. Just wanted to use all the bright pda heads here.

I have, as mentioned earlier, the sync working like a charm. But how the heck does one go about installing apps/files. Where should I place them in order for them to move to my palm m500.

/Jarz Corp

---

### Post by strips on 2005-08-24
Tip:

To test the connectivity  or do a manual backup of your palm:
1. Press the HotSync button on the palm/cradle
2. $ pilot-xfer -p /dev/ttyUSB1 -b ./backupdir

Then you can se if it starts backing up your palm or not. Gnome-pilot uses pilot-link as back-end so you can test the basics if you have problems with gnome-pilot.

---

### Post by strips on 2005-08-24
[QUOTE=Jarz Corp]But how the heck does one go about installing apps/files. Where should I place them in order for them to move to my palm m500.[/QUOTE]

You can use the pilot-link commandline tools.

1. Press the HotSync button on the palm/cradle
2. $ pilot-xfer -p /dev/ttyUSB1 -i filetoinstall.prc

---

### Post by robenroute on 2005-10-19
I've posted a possible solution to the sync problem:

[http://www.ubuntuforums.org/showthread.php?t=78918](http://www.ubuntuforums.org/showthread.php?t=78918)

---

### Post by dannemil on 2006-03-02
> **Sirenian]I had the same problem with my Tungsten T3 said:**
> Wizard Screen #2:[/COLOR]**

_Default Settings:_
Name: Cradle
Connection Speed: 9600 (default was 5600)
Device: /dev/ttyUSB1 or /dev/ttyUSB0 (default was /dev/pilot)
Timeout: 20 (default was 2)
[COLOR=DarkRed]Connection: USB[/COLOR] (not Serial. Doh!)

It's easy to miss the small things when you're following everything to the letter.



dude, you're a genius :)  - that one switch from serial to usb made it work. thanks -- Jim

---

### Post by revdev on 2007-06-19
I tried the above with my m500, and it didn't work. I did get it solved though, and it was easy.

All I did was on the wizard screen with the connection settings, I selected USB, changed the speed to 9600, and the port to "usb:"

It synced immediately.

Using Palm m500 os 4, Ubuntu Feisty, kernel 2.6.20-16.

---

