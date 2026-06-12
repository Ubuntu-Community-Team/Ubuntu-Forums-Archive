---
title: "Karmic and USB devices?"
date: 2009-11-09
forum: Installation &amp; Upgrades
---

### Post by hipogrito on 2009-11-09
Hi,

I have a USB to Serial cable that allows me to work via "serial" communication with an external machine (embedded system).

The Braille package has to be removed from an Ubuntu installation in order to make this to work properly. Alright. So, I have been working with the same system at least from Ubuntu 8.04... probably even from 7.04... and I have never had any problem once I discovered the Braille thingy.

Now, I upgraded to 9.10 and the communication between the 2 machines is not there anymore. Well, the application that I am using does not say that there is not a connexion, which is what normally says when there is not a connexion... in this case it loads but it seems to be in a funny state... like hung. 

So, the questions are 2:

1.- Has anybody had any similar kind of problem with a USB to Serial device in Koala or any other non/standard USB device?

2.- Has anything changed in the USB software-land in Koala from Jackalope?


I am thinking in downgrading...

Thank you very much!

Kind regards,
Fran

---

### Post by hipogrito on 2009-11-10
Hi,

So, I decided to reinstall Karmic from scratch...

No problems in the installation by the way.

Sadly it did not work either.... the USB to serial only seems to be working from Ubuntu to the Embedded Device, but not in the other way around... 


Oh, by the way, The other problem I am having is with Eclipse: Sometimes when you click on a button, the button turns gray but it does not do the action is supposed to do... I have to press ENTER in order to have the action done... 

The mouse is a serial device... so, I am wondering if there is something interfering in Karmic in the serial port... like the Braille package that I have to remove... but a new package also doing nasty things in there...

As I said before, the same machine got tons of other previous Ubuntu versions and everything worked perfect, so something is broken here...

Any idea?

Thanks,
Regards,
Fran

---

### Post by hipogrito on 2009-11-11
Hi,

The Serial Port problem is definitively from the external device to Ubuntu... the other way around it works...


And the Eclipse problem is a known issue very easy to fix:
[https://bugs.eclipse.org/bugs/show_bug.cgi?id=291257](https://bugs.eclipse.org/bugs/show_bug.cgi?id=291257)

Regards,
Fran

---

### Post by tvst on 2009-11-12
1.- Has anybody had any similar kind of problem with a USB to Serial device in Koala or any other non/standard USB device?

Yes, I'm having trouble getting my Arduino ([http://www.arduino.cc](http://www.arduino.cc)) & ttyMidi ([http://www.varal.org/media/ttymidi](http://www.varal.org/media/ttymidi)) to work under Karmic. Same thing with another completely unrelated USB serial device I use (an Intel iMote2). 

There is definitely something strange going on with USB serial devices here, but it's not just on Ubuntu. There are other users having similar problems with other distros as well. 
[http://www.arduino.cc/cgi-bin/yabb2/YaBB.pl?num=1202147376/15#16](http://www.arduino.cc/cgi-bin/yabb2/YaBB.pl?num=1202147376/15#16)

---

### Post by hipogrito on 2009-11-16
Hi,

Thanks for the info.

I am waiting for the next Kernel to see if that fixes it... although a million things could have caused this... 

Regards,
Fran

---

### Post by hipogrito on 2009-11-30
Hi,

It seems that the driver is broken... at least this proves that I am not getting crazy...

[http://ubuntuforums.org/showthread.php?t=1327965](http://ubuntuforums.org/showthread.php?t=1327965)


Regards,
Fran

---

### Post by bluesquall on 2009-12-10
I am having similar issues with an Arduino (ATmega328) and the Arduino IDE (0017) on the Karmic Netbook Remix.

The funny thing is that I can see my Arduino when I plug it in as `/dev/ttyUSB0' in >Tools>Serial Port, but I cannot load a new sketch onto the board. I get the error: 
avrdude: usbdev_open(): did not find any USB device "usb"

Still trying to figure this out. I'd like to use the Arduino IDE to work with my Pololu 3pi robot as well (ATmega328p) but I can't even see that one in the serial port menu.

I'm not using 64-bit, but I tried all the rxtx stuff I've seen around (e.g. [http://ubuntuforums.org/showthread.php?t=1321330&referrerid=793952](http://ubuntuforums.org/showthread.php?t=1321330&referrerid=793952)) but no dice.

---

### Post by graham_midi on 2010-01-09
Hi, I am new to all this (linux and midi) and I have also been trying to send midi data through ttymidi on Karmic. Though I seem to be breaking down at a different point then some of the posts I have seen and I wonder if it is my own ignorance of how midi works that is letting me down. I have tried several different things to solve this including:

1) Removing the braille driver
2) Reinstalling the ftdi.iso driver (copying and pasting the one supplied by tvst on one of these pages, and then also rebuilding the kernel and using the new built driver).
3) Umpteen combinations of things I have forgotten. 

If I run TTYmidi with the -v option I can see the "NOTE ON" etc messages being sent in the terminal, so that side of things is fine (?). I am trying to use aconnect to link that up to TIMIDITY but so far no sound. I can link vkeybd to TIMIDITY and it plays like a charm so I assume that my use of aconnect if fine. Does anyone know if there is something more that  have to do other than "aconnect" to get sound produced? I have tried using JACK but TTYMIDI does not show up as an input in the connect options (in fact I have nothing showing up in the MIDI options tab).

Any help would be appreciated.

Regards
Graham

---

### Post by graham_midi on 2010-01-15
Ok, so in my genius of trying to install a soundfont before learning how the thing worked I have worked out that I was playing my midi on a channel that had no sound associated to it. With a new sound font (or I suppose i could have tried changing the channel) I get a not very exciting, if not at all glamorous, car alarm sounding midi play back. Sweet

---

### Post by hipogrito on 2011-07-29
Hi,

Now that I am working in 11.04 I did not have to uninstall the Braille package to work with my serial port anymore. The serial port just worked.

Well done.

Thanks,

Regards,
Fran

---

