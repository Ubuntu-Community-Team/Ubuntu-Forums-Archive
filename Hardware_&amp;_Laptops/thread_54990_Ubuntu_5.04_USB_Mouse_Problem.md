---
title: "Ubuntu 5.04 USB Mouse Problem"
date: 2005-08-07
forum: Hardware &amp; Laptops
---

### Post by Subfix on 2005-08-07
Hello, I just installed Ubuntu 5.04 and my USB mouse it's being detected, it just sits there in the middle of the screen... taunting me  :mad: 

Any ideas how to get it so work? Thanks in advance.

---

### Post by FLeiXiuS on 2005-08-07
What mouse do you have and which protocol are you using for your mouse.  Refer to /etc/X11/xorg.conf.

---

### Post by varunus on 2005-08-07
Can you post the content of your /etc/X11/xorg.conf file?  Ubuntu should work out of the box with USB mice...worked with mine, at least...

---

### Post by Subfix on 2005-08-07
Here's the InputDevice section... should the protocol be set to USB?
Oh, and it's a Logitech optical USB mouse, I'm not sure of the model or anything... never paid attention to mouse models  ;-) 

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

Also, I don't think Ubuntu is detecting my ethernet adapter(s)... I have an onboard VIA and a realtec LAN card... It found my connection fine during the setup, but I don't see it in any of the networking options (then again, it's hard to navigate with the keyboard, so maybe i missed it).

Thanks again.  ](*,)

---

### Post by Subfix on 2005-08-07
...bump...

Anyone?

---

### Post by Gezzer on 2005-08-07
[QUOTE=][/QUOTE]
 in a konsole/terminal write

sudo dpkg-reconfigure xserver-xorg

follow the on screen instructions ...

---

### Post by Teroedni on 2005-08-07
And if that doesnt work you may try reinstall and make sure everything is plugged in when doing it included network

Your mose should work so it is probably only a bad driver. In Ubuntu it is quite a buch to choose from:P

---

### Post by Subfix on 2005-08-07
As far as the mouse goes, I noticed this during boot:

modprobe : FAILED : could not load /lib/modules/2.6.11-6mdk/modules.dep

and the structure in my installation seems to be /lib/modules/2.6.10-5-386/modules.dep

I don't know how this happened but I'm going to rename the directory to what it's looking for..

modules.dep is a text file containing paths to various drivers... so I'll bet this is the problem, I'll let you know how it works out!  :?

---

### Post by Subfix on 2005-08-07
Ok... here's what I did:

The paths in modules.dep were still pointing to the old directory (2.6.10-5-386)
so I made a new directory (2.6.11-6mdk) and copied the modules.dep there...

So the error went away... my mouses optical light thing blinks during the boot, but still doesn't work in GNOME...

However, I got a new error type:

x: version magic '2.6.10-5-386 preempt 386 gcc-3.3' should be '2.6.11-6mdk 686 gcc-3.4'
where x = various things such as 'apm'.

To me it sounds like my entire /lib/modules/ directory is out of date somehow, I don't know how this could have happened, I downloaded Ubuntu 2 days ago from the main site -- this is the second install with the same results.

Any suggestions for this one?  ](*,)

---

### Post by Gezzer on 2005-08-07
[QUOTE=][/QUOTE]
 in synaptic/settings/repositories
tick all the repositories universe/multi universe
then use reload and see if there are any updates ...

---

### Post by Subfix on 2005-08-07
Ubuntu still isn't recognizing my ethernet connections... probably from this whole driver issue...  :-x

---

### Post by Gezzer on 2005-08-07
[QUOTE=][/QUOTE]
 sorry im using Kubuntu so i may miss the mark here

i believe in system/settings network adapters
use add
then pick eth0 press apply
see if the adapter is picked up if so
check the properties of it and tick dhcp
then try the connection ...

---

### Post by Subfix on 2005-08-07
Hmmmm... I don't see an add button there, just activate/properties etc.

In the device manager I can find both of my ethernet adaptors but they are labeled as follows:
Device: Unknown
Capabilites: Unknown

This is pretty much how the entire device manager looks besides my graphic card... including the CPU.

Edit:

Also it seems as if Ubuntu has made a new /lib/modules/2.6.11-6mdk with a new modules.dep reflecting the right directory name... weird enough.

---

### Post by Gezzer on 2005-08-07
[QUOTE=][/QUOTE]
 this just goes to show how limited my knowledge is
sorry i could not be of more help
it seems i have much to learn myself ...

---

### Post by Teroedni on 2005-08-07
Does your mouse work?
And the network card 
Can you tell me the name of it ....

---

### Post by IronKnuckles on 2005-08-08
Just a thought... you had 'mdk' at the end of your kernel dir name. Does that mean you had Mandrake/Mandriva installed previously? Could this cause a problem?

---

### Post by varunus on 2005-08-08
Yes, this is confusing as Ubuntu hoary uses 2.6.10, not 2.6.11...are you trying to use a mandrake kernel in ubuntu?  This could cause tons of problems...

Did you ever get your mouse working?

In GNOME, you can configure internet from System->Administration->Networking.

---

### Post by Subfix on 2005-08-10
Sorry I haven't replied, go figure I was reinstalling Ubuntu and lightning struck the house and fried my mobo.

New setup, reinstalled Ubuntu 5.04, I had the same mouse issue, but the mouse was actually getting power from the USB port this time, so I switched ports and it works finally.

Ubuntu also recognized the onboard ethernet, which is also a realtek, same as my old one... oh well, it works.

As far as the mdk b.s. I found out that LILO was booting Ubuntu with a Mandriva image, and messing everything up. Stupid n00b.

Now I'm working on getting my sound to work, etc.
Thanks for the help though.

Edit:

By the way, I have an Audiophile 2496, which is supported by ALSA... any suggestions?

---

### Post by varunus on 2005-08-10
What doesn't work with your sound?  Can you type "alsamixer" into a terminal and see if anything is muted?  Also, have you followed the "configure sound properly" howto at [http://www.ubuntuguide.org](http://www.ubuntuguide.org) ?

BUT:  Skip the step that asks you to disable GNOME sounds or the GNOME sound server startup, it should be unnecessary.  Disable it only if following that guide doesn't let you have sound.
And make sure to install libesd-alsa0 and reconfigure your esd.conf...Otherwise it won't work.

---

