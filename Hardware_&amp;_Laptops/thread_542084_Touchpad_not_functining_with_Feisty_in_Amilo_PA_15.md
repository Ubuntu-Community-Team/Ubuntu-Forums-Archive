---
title: "Touchpad not functining with Feisty in Amilo PA 1538"
date: 2007-09-03
forum: Hardware &amp; Laptops
---

### Post by enas on 2007-09-03
I am running feisty on a fujitsu-siemens amilo pa 1538 notebook and i am having trouble with the touchpad. 

here is my uname -a output:
```
Linux berliner 2.6.20-16-generic #2 SMP Fri Aug 31 00:55:27 UTC 2007 i686 GNU/Linux

```

I have done some reading and trying of diffeent stuff but nothing works.

Here is my relevant xorg.conf sections:
```
...
Section "Module"
	Load		"i2c"
	Load		"bitmap"
	Load		"ddc"
	Load		"extmod"
	Load		"freetype"
	Load		"glx"
	Load		"int10"
	Load		"vbe"
        Load            "synaptics"
EndSection
...
Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
        Option          "Emulate3Buttons" "True"
	Option		"HorizScrollDelta"	"0"
        Option          "SHMConfig"              "True"
EndSection
...

Section "ServerLayout"
	Identifier	"Default Layout"
        screen          "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"stylus"	"SendCoreEvents"
	Inputdevice	"cursor"	"SendCoreEvents"
	Inputdevice	"eraser"	"SendCoreEvents"
	Inputdevice	"Synaptics Touchpad"
EndSection

```

Nonetheless i think the problem lies somewhere in the detection of my touchpad hardware.
Here is my /proc/bus/input/devices content:
```
I: Bus=0017 Vendor=0001 Product=0001 Version=0100
N: Name="Macintosh mouse button emulation"
P: Phys=
S: Sysfs=/class/input/input0
H: Handlers=mouse0 event0 ts0 
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3

I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/class/input/input1
H: Handlers=kbd event1 
B: EV=120013
B: KEY=4 2000000 3802078 f840d001 feffffdf ffefffff ffffffff fffffffe
B: MSC=10
B: LED=7

I: Bus=0003 Vendor=1058 Product=0903 Version=0111
N: Name="Western Digital External HDD"
P: Phys=usb-0000:00:0b.1-5/input1
S: Sysfs=/class/input/input2
H: Handlers=event2 
B: EV=20003
B: KEY=ff 0 0 0 0 0 0 0 0
B: LED=ff00

I: Bus=0010 Vendor=001f Product=0001 Version=0100
N: Name="PC Speaker"
P: Phys=isa0061/input0
S: Sysfs=/class/input/input3
H: Handlers=kbd event3 
B: EV=40001
B: SND=6

I: Bus=0011 Vendor=0002 Product=0006 Version=0000
N: Name="ImExPS/2 Generic Explorer Mouse"
P: Phys=isa0060/serio4/input0
S: Sysfs=/class/input/input4
H: Handlers=mouse1 event4 ts1 
B: EV=7
B: KEY=1f0000 0 0 0 0 0 0 0 0
B: REL=143

I: Bus=0019 Vendor=0000 Product=0002 Version=0000
N: Name="Power Button (FF)"
P: Phys=ACPI_FPB/button/input0
S: Sysfs=/class/input/input5
H: Handlers=kbd event5 
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button (CM)"
P: Phys=PNP0C0C/button/input0
S: Sysfs=/class/input/input6
H: Handlers=kbd event6 
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0019 Vendor=0000 Product=0005 Version=0000
N: Name="Lid Switch"
P: Phys=PNP0C0D/button/input0
S: Sysfs=/class/input/input7
H: Handlers=event7 
B: EV=21
B: SW=1

```

I cannot locate where my touchpad is in there (if it is there).

Apart from that, no matter what i have tried, i have never managed to get rid of the errors in the /var/log/Xorg.0.log file:
```

(EE) Synaptics Touchpad no synaptics touchpad detected and no repeater device
(EE) Synaptics Touchpad Unable to query/initialize Synaptics hardware.
(EE) PreInit failed for input device "Synaptics Touchpad"

```

Do I stand any chance of making it work?

ps: I don't know if this will help but i have requested from fujitsu-siemens support page that they send me the hardware type of my touchpad, still nothing.

---

### Post by enas on 2007-09-03
Additional info i forgot to post:
-The touchpad mouse ponter is abnormal, sticky or jumpy. the buttons work alright though.
-No other mice are connected on the pc
-I have no idea if the hardware has a problem or not, i formatted my xp distribution as soon as i bought the machine
-Please help!

---

### Post by ThrobbingBrain66 on 2007-09-03
Did you use the LiveCD to install?  I have to think you would've noticed the problem then.

I would try to reconfigure your xserver
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by enas on 2007-09-03
Yes, i installed using a live CD but i skipped the trial part and installed right away.
How can x-server reconfigure help? And moreover, how do i make sure i do not destroy other stuff such as my video card settings?

---

### Post by ThrobbingBrain66 on 2007-09-03
You must've used the touchpad during the LiveCD session to select the install icon right?  So it obviously worked then, and should work on a normal install.

The xserver controls your Video, Keyboard, Mouse(touchpad) and things of that nature.  Reconfiguring it may correct a wrong configuration during the install.  To avoid messing up your current config, just make a backup of your xorg.conf file.
```
sudo cp /etc/X11/xorg.conf xorg.conf_bak
```

Also, on the questions the configuration asks you, that you're not sure of, just select the defaults.

---

### Post by ThrobbingBrain66 on 2007-09-03
I was researching your notebooks specs online, and found out that it has an AVC touchpad.  Potentially this is why it's not working correctly with the synaptics driver.  I'm doing more research, but haven't found anything yet on getting it working.

---

### Post by enas on 2007-09-03
tried the reconfiguring, nothing changed in terms of mouse ponter behaviour. apart from that, the window manager has problems and some stuff disappeared from my panels. i'm switching back to the previous xorg.conf. thanx for your research, i' ll keep on searching as well. now that you have identified the touchpad type i feel we're in a safer path than trying random reconfiguring and hoping to get lucky

---

### Post by enas on 2007-09-03
in the (german speaking) forum for amilo owners there are several posts reporting the same problem. i will use babelfish and my little knowledge of german to decode the posts and if/when i find a solution i will update this thread (in english)
thank you for our help

---

### Post by enas on 2007-09-04
In the [http://amilo-forum.de]("http://amilo-forum.de") there is much discussion about BIOS update. My version (1.1i) seemed to be very buggy, according to user reports.
Well, i have flashed the newest version (1.1L) and the problem is still here.
There is also discussion about the wireless card affecting the touchpad when there is high traffic. the prob with the mouse jumping and sticking is not related to wireless either.
i am quite desperate. i' ll check if i can find anything for my BUG #81 at boot time, maybe everything will be fixed after i corrct this thing. (i also had this bug with the previous bios version)

ps: i kept the "bonus" installation cds i paid with the laptop, even though i did not ask for any ms products. i don't want to install xp again, i thought i was through once and for all with micro$oft. 

Heeeelp!

---

### Post by ThrobbingBrain66 on 2007-09-04
Sorry, enas, I still have been unable to find anything in regards to your problem.

Just as a test, could you remove the following line from the Synaptics Touchpad section of your xorg.conf:
```
Option          "SHMConfig"              "True"
```

Then reboot and see if the problem persists.

That line is only needed if you use a graphical package to control your touchpad....it's possible that it's causing a conflict.

I'm off to work now, but I'll check in either when I get back or tomorrow morning. Good luck!

---

### Post by enas on 2007-09-04
before i started searching around for a solution the shmconfig line was not there. i do not think it affects in any way the touchpad. the shmconfig is for the various synaptics driver GUIs, gsynatics, qsynaptics etc. none of them works due to the failure of the synaptics driver to detect a compatible touchpad at bootup time.

now i started downloading stuff with azureus and the internet traffic is really high on my wireless cad and the touchpad performance got a lot worse. 

so the problem *is* somehow related to the wlan card

going to bed, i'll give it a try tomorrow again

thx anyway

---

### Post by enboig on 2007-11-02
I have AMILO pa 1510 and my touchpad also goes bad when using wifi or also wired network.

Did you find any solution to your problem? maybe I can also use it)

thanks

---

