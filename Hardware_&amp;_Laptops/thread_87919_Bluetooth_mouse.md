---
title: "Bluetooth mouse"
date: 2005-11-09
forum: Hardware &amp; Laptops
---

### Post by shizow on 2005-11-09
i have macally bluetooth mouse and a IBM T43
and i am a bluetooth newbie

how do i get my mouse working in breezy(kubuntu)?

---

### Post by Burkey on 2005-11-09
I am by no means an expert on this but I do have it working well on mine.. I am using a Planex bluetooth mouse and usb adapter.

First make sure you have all the bluez stuff installed.

Do a ```
hcitool scan
```

To get the MAC addresses of all available devices, if this does not work then you may need to manually load the bluetooth modules, for me they auto-load on insert of the bluetooth device, you can see if the device is detected by checking the kernel messages.

Once you have that do a ```
sudo hidd --connect XX:XX:XX:XX:XX:XX
``` but substituting the MAC address of you're mouse.

It should just start working at that, since I want it to just work every time I plug the thing in I have edited /etc/default/bluez-utils on the lines ```
HIDD_ENABLED=1
HIDD_OPTIONS="-i XX:XX:XX:XX:XX:XX --server"
```

I am sure I left some stuff out, like that the mouse sometimes may not show up on a scan, in which case move it to ensure it is not asleep or press the little connect button on it.

Hope it works as well for you as it does for me

---

### Post by shizow on 2005-11-10
[QUOTE=Burkey]I am by no means an expert on this but I do have it working well on mine.. I am using a Planex bluetooth mouse and usb adapter.

First make sure you have all the bluez stuff installed.

Do a ```
hcitool scan
```

To get the MAC addresses of all available devices, if this does not work then you may need to manually load the bluetooth modules, for me they auto-load on insert of the bluetooth device, you can see if the device is detected by checking the kernel messages.

Once you have that do a ```
hcitool --connect XX:XX:XX:XX:XX:XX
``` but substituting the MAC address of you're mouse.

It should just start working at that, since I want it to just work every time I plug the thing in I have edited /etc/default/bluez-utils on the lines ```
HIDD_ENABLED=1
HIDD_OPTIONS="--connect XX:XX:XX:XX:XX:XX --server"
```

I am sure I left some stuff out, like that the mouse sometimes may not show up on a scan, in which case move it to ensure it is not asleep or press the little connect button on it.

Hope it works as well for you as it does for me[/QUOTE]



i tried that

```

sudo hcitool scan
Scanning ...
        00:0C:55:XX:XX:XX       Macally Bluetooth Mini Mouse

```

but
```

sudo hcitool --connect 00:0C:55:XX:XX:XX
hcitool: unrecognized option `--connect'
hcitool - HCI Tool ver 2.20

```
does not work

i tried
```

sudo hcitool cc 00:0C:55:xx:xx:xx

```
which does not say anything, but it gives not out an error
but the mouse still does not work

---

### Post by Burkey on 2005-11-10
sorry man, my bad..

```
hidd --connect <btaddr>
```

---

### Post by shizow on 2005-11-11
```

hcitool scan
Scanning ...
        00:0C:55:XX:XX:XX       Macally Bluetooth Mini Mouse

sudo hidd --connect 00:0C:55:XX:XX:XX
~$       

```

ok 
cool it works!!

---

### Post by Burkey on 2005-11-11
Glad I could help and even better you posted back to say it worked.. I edited the first post with the right "hidd" instead of "hcitool" command as well for anyone who finds this in the future.. heck, it is my first howto!

---

### Post by shizow on 2005-11-18
i can work with my mouse
but whenever it falls into sleepmode
i have to pair it again,
(press the pairing button and "sudo hidd --connect XX:XX:XX:XX:XX)

---

### Post by Burkey on 2005-11-20
Did you just pair or did you add the pairing command to the bluez script that I mentioned above?  My laptop can suspend and come back fine with working bluetooth mouse, I also have the mouse working after bootup without ever touching the console with that.

---

### Post by shizow on 2005-11-23
cool! thank you very much!

it works now

maybe i have a problem after a suspend with my lap, but thats not so important and i have to test that again,
my suspend to ram just works since yesterday

---

### Post by volkerbradley on 2005-11-28
Saw this very helpful post of yours.  Thanks for  putting it up.
I have a IBM Thinkpad T43p and am using it with a Microsoft Intellimouse for Bluetooth.  The pointer and  right and left buttons work.  However, the wheel does not.
Tried all kinds of combinations in the /etc/X11/xorg.config file but so far no luck getting the wheel to work (did check this mouse in MSWindows to make sure the wheel wasn't broken.  Wheel works in MSWindows).
Any suggestions?

---

### Post by shizow on 2005-11-28
[QUOTE=volkerbradley]Saw this very helpful post of yours.  Thanks for  putting it up.
I have a IBM Thinkpad T43p and am using it with a Microsoft Intellimouse for Bluetooth.  The pointer and  right and left buttons work.  However, the wheel does not.
Tried all kinds of combinations in the /etc/X11/xorg.config file but so far no luck getting the wheel to work (did check this mouse in MSWindows to make sure the wheel wasn't broken.  Wheel works in MSWindows).
Any suggestions?[/QUOTE]

with my macally mouse everything works even the wheel, it did not have to change something in xorg.conf
but here is part of my xorg.conf
```

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "Emulate3Buttons"       "true"
        Option          "ZAxisMapping"          "4 5"
EndSection

```

---

### Post by ichabod on 2005-12-02
Got my Logictech V270 mouse working easily after referring to this thread!  The only thing I needed to change to get it to automatically reconnet was using the "-i" option rather than the "--connect" option in /etc/default/bluez-utils 

```

#ichabod 2005-11-29 enabled for bluetooth mouse (logitech v270)

HIDD_ENABLED=1
HIDD_OPTIONS="-i XX:XX:XX:XX:XX:XX --server"

```

At first I didn't think it worked, because reconnects sometimes do take a few seconds (such as after mouse has been off, after computer resumes from suspend, or after wireless has been turned off, then on).  The green light on the bottom of the mouse appears to come on when a reconnect has been initiated by the computer.

I also found out that a quick 'n dirty connect can be made (perhaps to any input device?) with

```

sudo hidd --search

```

Great mouse, and I'm loving UBUNTU  - brand new UBUNTU user, and everything just works on my Compaq V2335US... incredible.

Thanks for the info about working with the Bluetooth mouse!

---

### Post by Burkey on 2005-12-12
Thanks for all the good responses everyone, sorry I cannot really advise on the MS Bluetooth mouse other than to suggest maybe you edit the xorg.conf file mouse section, I imagine that mouse has 7 buttons and you need the ZAxisMapping to be 6 7, then you need to run xmodmap after X starts to remap the side and scrol wheel buttons.

If you need more info, post back and I will elaborate.

Otherwise I edited the original post to fix the errors and I hope it just works for everyone now.

---

### Post by mtron on 2005-12-17
Hi! 

First thanks for the instructions, i got now my MS Bluetooth Keyboard and the IntelliMouse Bluetooth to work by using the "sudo hidd --connect XX:XX:XX:XX:XX:XX" commands for both devices, but i have no go to get them automatically connected at boot-up.

I tried adding 
HIDD_OPTIONS="-i XX:XX:XX:XX:XX:XX --server"

or
HIDD_OPTIONS="-connect XX:XX:XX:XX:XX:XX --server"

to the file /etc/default/bluez-utils, but there was no result. After the gnome login i ran the connect option from the terminal, and got "host offline" so i have to press the Connect button on the device and it works.

Anyway. does sb have an idea how i can initialize the mouse and keyboard on boot up? A script seems not to work, because of the "host offline" message....

---

### Post by er-ku on 2005-12-17
**mtron**,
what if you press the Connect button without going to the terminal?

---

### Post by mtron on 2005-12-17
I'm sorry i don't understand what you mean... no entry in the bluez-utis file and pressing "connect" on the device during boot up?

tried this but no go. is yours working as expected?

---

### Post by mtron on 2005-12-19
jeeha! i got it. after trickering a while with the config files it's now flawlessly working with ubuntu. nice to have hardware called "designed for Win" working...

As a reference for others:

My bluetooth devices:
- Transreciver (MS):Bus 004 Device 002: ID 045e:007e Microsoft Corp. Wireless Transceiver for Bluetooth
- Intelli Mouse for Bluetooth (MS): Adress (use "hcitool scan" to find it); Role: master, Direction: incoming, Link mode: 1 (0x1)
- Wireless Optical Desktop for Buletooth (MS) same settings...



Now open /etc/bluetooth/hcid.conf and adjust it to the following values:
```
# HCI daemon configuration file.
#
# $Id: hcid.conf,v 1.7 2004/12/13 14:16:03 holtmann Exp $
#

# HCId options
options {
	# Automatically initialize new devices
	autoinit yes;

	# Security Manager mode
	#   none - Security manager disabled
	#   auto - Use local PIN for incoming connections
	#   user - Always ask user for a PIN
	#
	security none;

	# Pairing mode
	#   none  - Pairing disabled
	#   multi - Allow pairing with already paired devices
	#   once  - Pair once and deny successive attempts
	pairing multi;

	# PIN helper
	#pin_helper /usr/bin/bluez-pin;

	# D-Bus PIN helper
	#dbus_pin_helper;
}

# Default settings for HCI devices
device {
	# Local device name
	#   %d - device id
	#   %h - host name
	name "%h-%d";

	# Local device class
	class 0x100100;

	# Default packet type
	#pkt_type DH1,DM1,HV1;

	# Inquiry and Page scan
	iscan enable; pscan enable;

	# Default link mode
	#   none   - no specific policy 
	#   accept - always accept incoming connections
	#   master - become master on incoming connections,
	#            deny role switch on outgoing connections
	lm accept;

	# Default link policy
	#   none    - no specific policy
	#   rswitch - allow role switch
	#   hold    - allow hold mode
	#   sniff   - allow sniff mode
	#   park    - allow park mode
	lp rswitch,hold,sniff,park;

	# Authentication and Encryption (Security Mode 3)
	#auth enable;
	#encrypt enable;
} 

```

next is /etc/default/bluez-utils, you need now the hardware addresses of the 2 devices. open a terminal and press the "connect" button, run "hcitool scan", and copy them in the file below... 

```
# Defaults for bluez-utils

# This file supersedes /etc/default/bluez-pan.  If
# that exists on your system, you should use this
# file instead and remove the old one.  Until you
# do so, the contents of this file will be ignored.

############ HIDD
#
# To have Bluetooth mouse and keyboard support, get the
# Linux 2.6.6 patch or better from bluez.org, and set 
# HIDD_ENABLED to 1.
HIDD_ENABLED=1
HIDD_OPTIONS="--server --search"
HIDD_OPTIONS="--connect 00:50:F2:7F:36:19 --server"
HIDD_OPTIONS="--connect 00:50:F2:80:45:29 --server"
# ...

```

now restart the buetooth subsystem or reboot. 

e voila!

---

### Post by lynng on 2006-01-28
[QUOTE=mtron]... i got now my MS Bluetooth Keyboard and the IntelliMouse Bluetooth to work ...[/QUOTE]

Did you get the scroll wheel or side buttons on the mouse to work?  I have the MS IntelliMouse Explorer for Bluetooth, and I cannot get even the scroll wheel working.  I previously had an Wireless Intellimouse Explorer (infrared type) working, but I just can't get the bluetooth one to work completely. :confused:   If you have it working, could you post the mouse section of your xorg.conf?

---

### Post by mtron on 2006-01-30
sure

```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"de"
	Option		"XkbVariant"	"nodeadkeys"
EndSection


Section "InputDevice"
 	 Identifier	"Configured Mouse"
 	 Driver		"mouse"
 	 Option		"CorePointer"
	 Option		"Device" 			 "/dev/input/mice"
	 Option		"Protocol"			 "ExplorerPS/2"
	 Option	 	"Buttons" 			 "7"
 	 Option	   	"ZAxisMapping"			 "6 7"
EndSection
```

Keep in mind that i can only confirm that this setup works for 

[IMG]http://i.pricerunner.com/prod/6_4_9_315045s/100x200/Microsoft_Wireless_IntelliMouse_Explorer_Bluetooth_2_0.jpg[/IMG]

this bluetooth mouse from microsoft.

If you have side buttons, see "Section 2: Side buttons and Nautilus" of [this post ]("http://www.ubuntuforums.org/showthread.php?t=65471&highlight=button+mouse"), then the forward & backward side button will work in nautilus & firefox.

cheers mtron

---

### Post by lynng on 2006-01-30
I confirmed the mouse section of my xorg.conf looks like yours.  Still no scroll wheel (or side buttons).  xev does not report any events for the wheel or side buttons.  Apparently the xserver can't see the events at all.

---

### Post by mtron on 2006-02-24
is the rest of your subsystem working? can other bt devices see and connect to the transreciver? 

I posed a wrong hcid.conf above, corrected it now. so if you used this settings it might be the cause sorry about that dude.

---

### Post by BatteryCell on 2006-02-27
mtron...u r my hero...

Oh and do you know how to make ubuntu realize I have five buttons and not just emulate three?

---

### Post by mtron on 2006-02-28
glad i could help.

try adjusting /etc/X11/xorg.conf 

```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"de"
	Option		"XkbVariant"	"nodeadkeys"
EndSection


Section "InputDevice"
 	 Identifier	"Configured Mouse"
 	 Driver		"mouse"
 	 Option		"CorePointer"
	 Option		"Device" 			 "/dev/input/mice"
	 Option		"Protocol"			 "ExplorerPS/2"
	 Option	 	"Buttons" 			 "7"
 	 Option	   	"ZAxisMapping"			 "6 7"
EndSection
```

that's all i needed to do. it works in nautilus, mozilla epiphany ect.

---

### Post by BatteryCell on 2006-02-28
Yeah I tried that and now my middle button (scroll wheel) scrolls forward and back ??

---

### Post by BatteryCell on 2006-02-28
like between websites...

---

### Post by mtron on 2006-03-01
and you have the same mouse that i have? strange. 

Try adjusting the ZAxismapping the 7 buttons are in my case:
1: left click
2: right click
3: middle click (on scroll wheel)
4: scroll wheel up
5: scroll wheele down
6: sidebutton page forward
7: sidebutton page back

Maybe it helps to change the line
Option	   	"ZAxisMapping"			 "4 5"

or whatever. If not, is there any terminal output if you scroll the wheel?

---

### Post by rangar on 2006-03-01
I bought a microsoft blueetooth mouse-keyboard-combo today and found this thread very helpful so far. But there is still a problem left. Beneath Ubuntu i also want to use Windows XP. In Windows i established a secure connection to the keyboard. But if my interpretation of the conf-file ist correct, in Ubuntu the connection is not encryted. Now as soon as i boot Ubuntu,  the keyboard seems to lose its encryption-key. As a result of this, I cannot use the keyboard in Windows until i reestablish the connection.
Is there a way to secure the connection in Ubuntu either? I could use an unsecure connection in Windows, but i don't want anybody to spy on what i'm typing.

---

### Post by BatteryCell on 2006-03-01
mtron:  Thats probably the thing, I dont have the same kinda mouse...I guess Ill just play around till i figure out which buttons are which...

Rangar: This happens to me too, when you boot into windows, go to the connect bluetooth devices thing and connect your devices without passkeys and enable them to be connected when seen (so that if u hit a button windows will start using the devices)...and bluetooth doesnt have very far range so I wouldn't worry too much bout that.

---

### Post by mtron on 2006-03-02
[QUOTE=rangar]
Is there a way to secure the connection in Ubuntu either? I could use an unsecure connection in Windows, but i don't want anybody to spy on what i'm typing.[/QUOTE]

sure there is. I just don't use win any more so i was not aware of this issue, but as batterycell added, the range  is very limited, so a keyboard isn't a big security leak (an un-secured mobile connection is much more dangerous! )

but in theory you can use a secure connection (with a ping) like i use it with my samsung e720 (connected to the same transreciever).

I just didn't try it with the keyboard till now, but i will do it tonight and come back with an update on this.   (i'm currently @ work)

---

### Post by rangar on 2006-03-02
@BatteryCell
I cannot measure the range, but i read in an established german computer magazine called "c't" that often the range is (up to 10 times) higher than proclaimed. I can only hope that nobody *wants* to hack my bluetooth device. :) 

@mtron
This would be very nice. I'm shunning to boot Ubuntu as i dislike reestablishing the connection each and every time.

---

### Post by mtron on 2006-03-29
i didn't have the time till now, sorry. And i won't do it for 5.10 any more. I'm planning to upgrade, so i will  update you  on dapper asap. 

Sb. asked me via email howto restart the bluetooth subsystem without rebooting. No surprise, debian ( & ubuntu) has a init.d script:

sudo /etc/init.d/bluez-utils restart

should do it.

cheers mh

---

### Post by m.musashi on 2006-04-05
I had my bluetooth mouse working beautifully on Dapper flight 3 (or maybe 4) but I decided to do a clean install of flight 5 (it's what I had) and update. I reset everthing the same but now it won't work. It will work if I run the hcitool scan and hidd connect in a terminal so I know it works but the commands I added to the /etc/default/bluez-utils aren't working. Any thoughts? Here is the section from the file:
```
############ HIDD
#
# To have Bluetooth mouse and keyboard support, get the
# Linux 2.6.6 patch or better from bluez.org, and set 
# HIDD_ENABLED to 1.
HIDD_ENABLED=1
HIDD_OPTIONS="-i 00:0E:A1:XX:XX:XX --server"
# to make hidd always use a particular interface, use something
# like this, substituting the bdaddr of the interface:
# HIDD_OPTIONS="-i AA:BB:CC:DD:EE:FF --server"
#
# remove '--master' if you're having trouble working with Ericsson
# T630 phones with hidd operational at the same time.
```
Thanks.

EDIT: one more thing, the sudo /etc/init.d/bluez-utils restart also has no effect. Only the hcitoo and hidd commands in a terminal will get it to work.

---

### Post by mtron on 2006-04-10
[QUOTE=m.musashi]the sudo /etc/init.d/bluez-utils restart also has no effect.[/QUOTE]

did ya look into the init.d script? any changes to the 5.10 version attached? anyway, file a bug report for this. Man i am really curious for the new ubuntu, but both, my server and the workstation are needed badly, so i have to wait till the release ](*,)

---

### Post by m.musashi on 2006-04-10
[QUOTE=mtron]did ya look into the init.d script? any changes to the 5.10 version attached? anyway, file a bug report for this. Man i am really curious for the new ubuntu, but both, my server and the workstation are needed badly, so i have to wait till the release ](*,)[/QUOTE]
There is a lot of code there I don't get. Anyway to compare two files without doing it manually? I attached my init.d script in case you are curious.

What gets me is this worked fine before I reinstalled. I can't see that flight 4 to flight 5 would have been that different. If anything, it should have been better. I guess new bugs can pop up.

---

### Post by m.musashi on 2006-04-10
[QUOTE=m.musashi]I attached my init.d script in case you are curious.[/QUOTE]
Oops, didn't attach. I'll try again.

---

### Post by loserbaby on 2006-04-11
OK, SuSe 9.2 has been my only truly successfull linux on my laptop so far... As I burn my breezy badger .iso . Has anybody messed with the MS 7 button mouse and a billionton PCMCIA bluetooth adapter? I'll be reading-

---

### Post by lynng on 2006-04-12
[quote=m.musashi]There is a lot of code there I don't get. Anyway to compare two files without doing it manually?[/quote]

From CLI there's cmp and diff to show differences between files.

---

### Post by mtron on 2006-04-12
I'm currently at work, so i can't check.. but beside the Terminal diff, there is also a KDE gui available i think it's called "kdiff3".

but back to the bluez init.d script. can another drapper user confirm that it's not restarting the subsystem, and did sb file a bug report for this?

@looserbaby: give us some more info, what did ya try from this thread? usually you can do it similar to the method described in this thread (xorg file)

```
Section "InputDevice"
 	 Identifier	"Configured Mouse"
 	 Driver		"mouse"
 	 Option		"CorePointer"
	 Option		"Device" 			 "/dev/input/mice"
	 Option		"Protocol"			 "ExplorerPS/2"
	 Option	 	"Buttons" 			 "7"
 	 Option	   	"ZAxisMapping"			 "6 7"
EndSection
```

---

### Post by m.musashi on 2006-04-12
[QUOTE=mtron]but back to the bluez init.d script. can another drapper user confirm that it's not restarting the subsystem, and did sb file a bug report for this?[/QUOTE]
Just to clarify, I did have this working in dapper so I don't think it's a for sure bug. I could have messed something up. However, it worked on an earlier flight and then when I did a clean install of flight 5 and updated (presumably to flight 6) and then tried to get it to work it didn't. So it's also possible something in dapper broke on the later flight. I have not filed a bug report. If someone else can confim a problem that would be good. I'm not savy enough with linux yet to have some confidence it's not my fault (most everything else is:) )

---

### Post by roderikk on 2006-04-14
Hi,

I've installed the logitech mx 5000 succesfully on dapper, however, now it seems that sometimes when I move my mouse it slows down. When I look at the CPU usage of that period it seems to use 100%!

Has this something to do with bluetooth or more with dapper/ubuntu?

---

### Post by mtron on 2006-04-14
when the cpu usage is at 100%, open a terminal, write "top" and it will display all running processes, with the highest cpu usage downwards.

Notice the pid number on the left with the command "kill 1234" you can kill the process running with the pid 1234. 

Can you report if it has something todo with the bluetoot subsystem, and if you're running flight6, can you check the init.d script above?

---

### Post by mtron on 2006-05-10
dapper install

did a new install with dapper beta. shiny & beautiful release! 

the bluetooth setup is accordingly to breezy. The bugs with the init.d scripts are gone, the bluetooth system is working reliable and stable.

to setup the MS InelliMouse and Optical Desktop fpr BT, plug in the USB dongle and run 

$ lsusb

```
Bus 004 Device 002: ID 045e:007e Microsoft Corp. Wireless Transceiver for Bluetooth
```

if your output is similar to this, install the bluez-utils and configure the hcid.conf file:

$ sudo gedit /etc/bluetooth/hcid.conf

to the following values

```
#
# HCI daemon configuration file.
#

# HCId options
options {
	# Automatically initialize new devices
	autoinit yes;

	# Security Manager mode
	#   none - Security manager disabled
	#   auto - Use local PIN for incoming connections
	#   user - Always ask user for a PIN
	#
	security auto;

	# Pairing mode
	#   none  - Pairing disabled
	#   multi - Allow pairing with already paired devices
	#   once  - Pair once and deny successive attempts
	pairing multi;

	# PIN helper
	pin_helper /usr/bin/pinwrapper;

	# D-Bus PIN helper
	#dbus_pin_helper;
}

# Default settings for HCI devices
device {
	# Local device name
	#   %d - device id
	#   %h - host name
	name "%h-%d";

	# Local device class
	class 0x3e0100;

	# Default packet type
	#pkt_type DH1,DM1,HV1;

	# Inquiry and Page scan
	iscan enable; pscan enable;

	# Default link mode
	#   none   - no specific policy 
	#   accept - always accept incoming connections
	#   master - become master on incoming connections,
	#            deny role switch on outgoing connections
	lm accept;

	# Default link policy
	#   none    - no specific policy
	#   rswitch - allow role switch
	#   hold    - allow hold mode
	#   sniff   - allow sniff mode
	#   park    - allow park mode
	lp rswitch,hold,sniff,park;

	# Authentication and Encryption (Security Mode 3)
	#auth enable;
	#encrypt enable;
}
```

next is /etc/default/bluez-utils, you need now the hardware addresses of the 2 devices. open a terminal and press the "connect" button, run "hcitool scan", and copy them in the file below...

```
# Defaults for bluez-utils

# This file supersedes /etc/default/bluez-pan.  If
# that exists on your system, you should use this
# file instead and remove the old one.  Until you
# do so, the contents of this file will be ignored.

############ HIDD
#
# To have Bluetooth mouse and keyboard support, get the
# Linux 2.6.6 patch or better from bluez.org, and set 
# HIDD_ENABLED to 1.
HIDD_ENABLED=1
HIDD_OPTIONS="--server --search"
HIDD_OPTIONS="--connect 00:50:F2:7F:36:19 --server"
HIDD_OPTIONS="--connect 00:50:F2:80:45:29 --server"
...
```

ok. restart the subsystem with "sudo /etc/init.d/bluez-utils restart", and connect the devices (i needed to do this only for the first time manually, from a reboot on, it connects them automatically)

$ sudo hidd --connect 00:50:F2:7F:36:19
$ sudo hidd --connect 00:50:F2:80:45:29

and the devices work. you can check active bt connection with the command "hcitool con" 

last step to activate the side buttons (forward & backward) of the mouse:

first, edit xorg.conf Input devices (adjust the "XkbModel" and the "XkbLayout" to your needs, the mouse part needs no editing by you) 

```
Section "InputDevice"
   	Identifier     "Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105" // change me!
	Option		"XkbLayout"	"de"     // change me!
	Option		"XkbVariant"	"nodeadkeys"
EndSection

Section "InputDevice"
 	 Identifier     "Configured Mouse"
 	 Driver		"mouse"
	 Option		"CorePointer"
	 Option		"Device" 			 "/dev/input/mice"
	 Option		"Protocol"			 "ExplorerPS/2"
	 Option	 	"Buttons" 			 "7"
	 Option	   	"ZAxisMapping"			 "4 5"
EndSection
```

second: 

$ sudo gedit /etc/X11/Xsession.d/57xmodmap"
```
xmodmap -e "pointer = 1 2 3 4 5 8 9 6 7 10 11"
```

save, press CTRL + ALT + Backspace, and login to gnome. now the buttons work as expected :) 

Todo:
- use a secure connection with pin for the keyboard
- map the multimedia keyboard buttons to functions in xorg

---

### Post by x64Jimbo on 2006-06-16
AHHH!! Thank you mtron! I have been scouring the entire internet looking for this information! 'Hallelujah' as they say. It's late right now but you can bet i'm bookmarking this thread for messing around with bluetooth tomorrow afternoon/evening. Did you ever get the keyboard to connect securely to the desktop? I'm not too concerned about my mouse strokes being monitored, but transmission of my credit card numbers, SSN, etc over any wireless band is bad news to me, and if I can encrypt it, I'd feel a lot better.

---

### Post by x64Jimbo on 2006-06-16
Ok so I tried out the stuff you said, and unfortunately it caused my system to hang when I start X. So I reversed all the changes. I'm puzzled as to why this would work for you and not for me since we're using all the same software.
A couple things I noted while doing your steps:
I had no file called /etc/X11/Xsession.d/57xmodmap. Is this GNOME specific? I'm running KDE. I made the file myself but I didn't know if that was OK.
My xorg.conf didn't have the Option "nodeadkeys" so I had to add that too. Any reason? 
I didn't see a reason to change my keyboard layout to German since I type in English. Is that a hack/workaround?

---

### Post by mtron on 2006-06-17
hi! 
 i think your problerm is related to the xorg.conf file. please post it here and i will have a look. is the bt- subsystem working? can you connect the devices manually and do they display with "hcitool con" (terminal)?

let's break it down one by one. first: 

xorg:
Option		"XkbModel"	"pc105" // change me!
Option		"XkbLayout"	"de"     // change me!
Option		"XkbVariant"	"nodeadkeys"

are all options for german speaking users. sorry should have made this more clear. if you use the english version

Option		"XkbModel"	"pc104" //(or if you have only 102 buttons, then use this)
Option		"XkbLayout"	"en"

and leave the "nodeadkeys" Option, you don't need it, cause we german speaking people have some strange extra letters, like äöü € and so on... 

second:57xmodmap. 
It's ok when this file doesn't exist by default. these are some special rules to translate the side buttons from the mouse to functions in xorg. i can't answer your question if this is gnome specific. Never worked with kde, but what i understand how xorg works it should be ok for both, gnome & kde.

---

### Post by x64Jimbo on 2006-07-05
Thanks for the help... I went back and tried everything you said, and it worked flawlessly this time! Thanks a million!
Be sure to let me know as soon as you figure out how to make the keyboard traffic encrypted... cause until then, i have to keep this wired keyboard around for entering my passwords ;)
Sincerely, 
~Jimbo

---

### Post by engrocha on 2006-07-07
i'm sorry for my question. i am a newbee but please believe i have searched a lot and tried but i have a problem.

i can get my microsoft intellimouse for Bt with "hcitool scan"
then i try 

engrocha@notebux:~$ sudo hidd --connect XX:XX:XX:XX:XX 
password:

i enter the pass and again i get 

engrocha@notebux:~$

however the mouse still doesent work. i've tried everything but still i can't make my mt mouse to work. any ideas?




edit: i found it! it seems that some changes i made in order to make my tochpad scrool to function bay changing some lens in /etc/x11/xorg.cong made both my usb an BT ouse not to work. as i changed it back to it's original they both started working. now i only have to figure out how to make my touchpad scrrol to work again.

---

### Post by tones111 on 2006-07-17
Thanks for the great guide.  This thread helped me get my Microsoft bluetooth keyboard and mouse working with bluez-utils.  I've been searching anywhere and can't find any up to date documentation on how to get encryption working for the keyboard.  Enabling auth and/or encrypt break my setup.  Is there any way to enable encryption for only the keyboard?  The bluetooth setup in windows was simple and painless... any luck that linux will see similar ease of use in the future?  Thanks again for the great info, any help is appreciated.

---

### Post by howardf42 on 2006-07-22
I'm a fairly new Ubuntu user and have been trying to get Dapper working little by little, or as we say here in Mexico "poco a poco."

My most nagging problem at this time is trying to get my Logitech V270 Bluetooth mouse working on my Dell Inspiron 6000 laptop with built in Bluetooth.  

I've read through this thread in detail and have edited the necessary files as described herein, but no joy yet.  When I try to restart bluez-utils or run hidd connect I get the error message: "Can't get device information: Host is down"

I don't know where to go from here.  Any help would be much appreciated.

---

### Post by x64Jimbo on 2006-07-22
Try pressing the "pairing" button/switch on the mouse right before running the command.

---

### Post by dragonflyFZX on 2006-07-25
hi,

i have got a strange problem.  My bluetooth mouse used to work using this how-to.  However, it stopped working (after an update???).  That is, i have to manually pair it each time it goes to sleep.  Furthermore, it does not connect at startup.  Furthermore, only pressing the connect button on the mouse does also not work.

I am using KDE, and i noticed that the KBluetoothD icon in the panel is grey when i boot.  I remember it was always blue at the time the mouse was still working.  Maybe this has to do with it???  Is there a way i can reset everything and try all over again?  

D

---

### Post by mtron on 2006-07-27
the kbluetooth pannel plugin uses the same bt stack, we configured the bluetooth subsystem manually. so if there is no active connection  between the transreciever & a client the plugin will be greyed out. anyway:

if you're running dapper the problem isn't caused by an update. mine is working ok. check the batteries! it sounds like there is something wrong with the client if the HCI tool doesn't recognize it during a scan.

---

### Post by x64Jimbo on 2006-07-27
Any word on keyboard encryption? ;)

---

### Post by mtg17 on 2006-07-27
I just got a new laptop with Bluetooth built in. If I get the IntelliMouse Bluetooth would I be able to use it without the USB receiver?

---

### Post by x64Jimbo on 2006-07-28
In theory, that's the idea. Pretty much the only limiting factor there is whether the built-in bluetooth gets recognized by Linux (it probably will, but you gotta be prepared for the worst when you're working with experimental stuff.)

---

### Post by dragonflyFZX on 2006-07-28
> **mtron said:**
> the kbluetooth pannel plugin uses the same bt stack, we configured the bluetooth subsystem manually. so if there is no active connection  between the transreciever & a client the plugin will be greyed out. anyway:

if you're running dapper the problem isn't caused by an update. mine is working ok. check the batteries! it sounds like there is something wrong with the client if the HCI tool doesn't recognize it during a scan.

I find it strange that in this forum, the answer to the problem is often: replace the hardware.  What is the point in choosing a free distro when you need to replace expensive hardware all the time :p 

No, serious, its not the batteries.  The mouse in question is a brand new toshiba optical wireless bt which works seamlessly in XP (ie. connect automatically, wake from sleep,...).  Besides, i have got another bt mouse with a rechargable battery that is giving me exactly the same issues on dapper.

The other mouse used to function using the steps outlined in this thread (ie. connect automatically, wake from sleep).  It doesn't anymore, so it has to do with some changed settings.

The thing is not that the client does not get recognised doing a scan.  I can get it to work with for instance the hidd --search.  The problem is to get it connect automatically at boot (or to wake it from sleep, because repairing all the time is really anoying)

The fact that i mentioned the kbluetooth panel was because i thought it might give someone some ideas.  As i said, i remember it was always bleu (even before ever having connected any bluetooth device).  Now it says the bluetooth adapter has been found, but then turns grey.

Someone please help.  I dont like the idea of having to reinstall from scratch just to get the bluetooth working as it was=P~

---

### Post by x64Jimbo on 2006-07-28
There's always a possibility that the toshiba mouse was made specifically for Windows with a special driver necessary to get it to wake up from sleep mode or autoconnect. Did you need to install any software with it when you got it working in windows, or did windows just pick it up as a generic HID?

---

### Post by dragonflyFZX on 2006-07-31
> **x64Jimbo said:**
> There's always a possibility that the toshiba mouse was made specifically for Windows with a special driver necessary to get it to wake up from sleep mode or autoconnect. Did you need to install any software with it when you got it working in windows, or did windows just pick it up as a generic HID?

Nope, works just like that in windows.  Besides, as i already explained, i have another bluetooth mouse which used to work but not anymore.  It is thus mouse independent.

---

### Post by dragonflyFZX on 2006-08-07
ok,
i am getting somewhere.  If i move the mouse, it gets connected as i can tell from the kbluetooth icon in the menubar.  But moving it does not move the pointer.  Also, the device name stays the same as the address.  Where do i tell kubuntu that it is a mouse???  ](*,)

---

### Post by x64Jimbo on 2006-08-07
I was running into all the same issues you are when I first started trying this. I couldn't figure out what the issue was. So, I just went through and followed all of the directions again, and then it worked. I think I must have missed something the first time. Try that.

---

### Post by FrankL on 2006-08-19
I'm trying to install my logitech V270 in Ubuntu, but without any succes. Hopefully you guys can help me.

When I try to run to bluez-patch, I get:

frank@frank-laptop:~/Downloads$ sh patch-2.6.17-mh5
diff: linux-2.6.17/drivers/bluetooth/bfusb.c: No such file or directory
diff: linux-2.6.17-mh5/drivers/bluetooth/bfusb.c: No such file or directory
patch-2.6.17-mh5: line 2: ---: command not found
patch-2.6.17-mh5: line 3: +++: command not found
patch-2.6.17-mh5: line 4: @@: command not found
patch-2.6.17-mh5: line 5: bluez-firmware-1.2: command not found
patch-2.6.17-mh5: line 6: bluez-firmware-1.2: command not found
patch-2.6.17-mh5: line 7: bluez-firmware-1.2: command not found
patch-2.6.17-mh5: line 8: syntax error near unexpected token `('
patch-2.6.17-mh5: line 8: `- *  Copyright (C) 2003  Marcel Holtmann <marcel@holtmann.org>'

So no luck. I do have the 2.6 kernel though, only not .17:

frank@frank-laptop:~/Downloads$ uname -r
2.6.15-26-686

And if I just try to find the mouse it says the device does not exist:

frank@frank-laptop:~/Downloads$ hcitool scan
Device is not available: No such device

What am I doing wrong? Thanks a lot in advance!

        Frank

---

### Post by Jonathan Métillon on 2006-08-21
> **Burkey said:**
> It should just start working at that, since I want it to just work every time I plug the thing in I have edited /etc/default/bluez-utils on the lines ```
HIDD_ENABLED=1
HIDD_OPTIONS="-i XX:XX:XX:XX:XX:XX --server"
```

Thank you for this info Burkey, I've been able to connect my [Sony Vaio VGP-BMS30 Bluetooth mouse.]("http://vaio.sony-europe.com/view/ShowProduct.action?product=VGP-BMS30&site=ite_en_GB")

And I followed you instruction to have it connected at boot, it does not work. Of course I don't forget to power on my mouse and press the CONNECT button.

Here is the content of my /etc/default/bluez-utils file:

```

############ HIDD
#
# To have Bluetooth mouse and keyboard support, get the
# Linux 2.6.6 patch or better from bluez.org, and set 
# HIDD_ENABLED to 1.
HIDD_ENABLED=1
HIDD_OPTIONS="--master --server"
# to make hidd always use a particular interface, use something
# like this, substituting the bdaddr of the interface:
HIDD_OPTIONS="-i 00:16:38:D1:E1:FD --server"
#
# remove '--master' if you're having trouble working with Ericsson
# T630 phones with hidd operational at the same time.

```

Is there something wrong?

---

### Post by Jonathan Métillon on 2006-08-21
Also I noticed that each time the computer goes to power saving mode (I mean screensaver, not hibernate), the bluetooth device must be deactivated because when it wakes up, the mouse is no more usable and I've got to connect again using hidd.

Is there a way to prevent the Bluetooth device to be deactivated when the computer goes to power saving mode?

---

### Post by howardf42 on 2006-08-26
> **Burkey said:**
> Did you just pair or did you add the pairing command to the bluez script that I mentioned above?  My laptop can suspend and come back fine with working bluetooth mouse, I also have the mouse working after bootup without ever touching the console with that.

I have not been able to get my Bluetooth mouse working at startup.  I've made all the recommended changes, but it won't start.  When I run ```
sudo hidd --connect 00:07:61:4D:43:89
``` I get this error message: > Can't get device information: Operation already in progress  After several hours the hidd --connect will work.  Also, after the screensaver starts or the laptop has gone to sleep mode, I have to run hidd --connect again.

Any or all help is appreciated.

---

### Post by FrankL on 2006-08-29
Okay, I succeeded in getting hcitool to find my bluetooth mouse:


frank@frank-laptop:~$ sudo hcitool scan
Scanning ...
        XX:XX:XX:XX:XX:XX       Bluetooth Travel Mouse
        XX:XX:XX:XX:XX:XX       Wanadoo_3c51

Don't know what the other wanadoo thing is, probably not mine :)

But now I try to connect to the mouse with the following command:

frank@frank-laptop:~$ sudo hidd -connect XX:XX:XX:XX:XX:XX
Can't get device information: Host is down

with the X-es being the number shown by hcitool for the bluetooth travel mouse. This number is equal to the number shown on the mouse, so is correct.

Any idea why hcitool can find it, but hidd cannot? Has it to do with the fact I got a built-in bluetooth adapter (Toshiba Tecra M7 with built-in bluetooth)? Any other suggestions?

Thanks a lot in advance,

Frank

---

### Post by tsiMental on 2006-08-30
Try the approach that I describe [here]("http://www.ubuntuforums.org/showthread.php?p=1440347#post1440347").

Hope you find your solution.

Regards,
Håvar Nielsen

---

### Post by FrankL on 2006-08-31
Thanks, TsiMental, that works flawlessly!

As a matter of fact I just turned on my laptop, vaguely remembering I tried your method yesterday. After the computer booted, I removed my mouse from its little bag, turned it on and to my amasement it worked instantly!! Whooohoooo :) I like it :)

Just to add to possibly help others. I added "toshset -bluetooth on" (for toshiba laptops) to my \etc\rc.local to enable my bluetooth each time I start. My laptop just keeps forgetting I want it to be on :) That, combined with TsiMentals guide did the trick.

---

### Post by nrwilk on 2006-09-02
> **tsiMental said:**
> Try the approach that I describe [here]("http://www.ubuntuforums.org/showthread.php?p=1440347#post1440347").

Hope you find your solution.

I love you.  This works very well.  Finally!

:grin: =D> \\:D/

---

### Post by Flooghans on 2006-09-02
I am unable to get my mouse to stay connected after boot up.

First, my hardware:  Acer 5672 WMLI laptop with built-in bluetooth, a logitech V270 bt mouse.

The behavior I'm experiencing is very strange.  During logging in (after I have entered my password, but before the regular desktop shows up) the mouse appears to get connected.  If I keep the mouse moving, it will not disconnect.  However, the moment I stop moving the mouse, it gets disconnected.  Pressing the reset/connect button the mouse has no effect.

If I go into a console and ```
sudo hidd --search
``` while pressing the  reset/connect button on the mouse, it gets connected and stays there.  This is a major nuisance, however, and XP has no trouble connecting at all (no, I did not install custom drivers).

Its clear that ubuntu is able to connect to the mouse, but I'm hoping someone can help me figure out how to connect it automatically.

Edit:  I tried the /etc/rc.local tactic and editing my /etc/bluetooth/hcid.conf and /etc/default/bluez-utils, neither fixed the problem.

---

### Post by nrwilk on 2006-09-02
@flooghans:

I have a v270 and I was having the ***exact*** same problem.  I'll bet we can resolve the issue for you. :)

Can you please post the output of these commands:

```
cat /etc/rc.local
```
```
cat /etc/bluetooth/hcid.conf
```
```
cat /etc/default/bluez-utils
```

I'll compare the output to the files I use, and offer suggestions as to how you can edit your stuff.  Maybe if you try the same setup I have, you can get it to work.

nrwilk

---

### Post by Flooghans on 2006-09-04
> **nrwilk said:**
> @flooghans:

I have a v270 and I was having the ***exact*** same problem.  I'll bet we can resolve the issue for you. :)

Can you please post the output of these commands:

```
cat /etc/rc.local
```
```
cat /etc/bluetooth/hcid.conf
```
```
cat /etc/default/bluez-utils
```

I'll compare the output to the files I use, and offer suggestions as to how you can edit your stuff.  Maybe if you try the same setup I have, you can get it to work.

nrwilk

I was @ home for the weekend, first chance to try this out.  Ok here we go:

```
cat /etc/rc.local
```

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

# Bluetooth -- [www.ubuntuforums.org/showthread.php?p=1440347#post1440347](www.ubuntuforums.org/showthread.php?p=1440347#post1440347)
/usr/bin/hidd --server

exit 0

```
cat /etc/bluetooth/hcid.conf
```

#
# HCI daemon configuration file.
#

# HCId options
options {
        # Automatically initialize new devices
        autoinit yes;

        # Security Manager mode
        #   none - Security manager disabled
        #   auto - Use local PIN for incoming connections
        #   user - Always ask user for a PIN
        #
        security auto;

        # Pairing mode
        #   none  - Pairing disabled
        #   multi - Allow pairing with already paired devices
        #   once  - Pair once and deny successive attempts
        pairing multi;

        # PIN helper
        pin_helper /usr/bin/pinwrapper;

        # D-Bus PIN helper
        #dbus_pin_helper;
}

# Default settings for HCI devices
device {
        # Local device name
        #   %d - device id
        #   %h - host name
        name "%h-%d";

        # Local device class
        class 0x3e0100;

        # Default packet type
        #pkt_type DH1,DM1,HV1;

        # Inquiry and Page scan
        iscan enable; pscan enable;

        # Default link mode
        #   none   - no specific policy
        #   accept - always accept incoming connections
        #   master - become master on incoming connections,
        #            deny role switch on outgoing connections
        lm accept;

        # Default link policy
        #   none    - no specific policy
        #   rswitch - allow role switch
        #   hold    - allow hold mode
        #   sniff   - allow sniff mode
        #   park    - allow park mode
        lp rswitch,hold,sniff,park;

        # Authentication and Encryption (Security Mode 3)
        #auth enable;
        #encrypt enable;
}

```
cat /etc/default/bluez-utils
```

# Defaults for bluez-utils

# This file supersedes /etc/default/bluez-pan.  If
# that exists on your system, you should use this
# file instead and remove the old one.  Until you
# do so, the contents of this file will be ignored.

############ HIDD
#
# To have Bluetooth mouse and keyboard support, get the
# Linux 2.6.6 patch or better from bluez.org, and set
# HIDD_ENABLED to 1.
#HIDD_ENABLED=0
#HIDD_OPTIONS="--master --server"
HIDD_ENABLED=1
HIDD_OPTIONS="--master --server --search"
HIDD_OPTIONS="--connect 00:07:XX:XX:XX:XX --server"
# to make hidd always use a particular interface, use something
# like this, substituting the bdaddr of the interface:
# HIDD_OPTIONS="-i AA:BB:CC:DD:EE:FF --server"
#
# remove '--master' if you're having trouble working with Ericsson
# T630 phones with hidd operational at the same time.

############ COMPATIBILITY WITH OLD BLUEZ-PAN
# Compatibility: if old PAN config exists, use it
# rather than this file.
if test -f /etc/default/bluez-pan; then
    . /etc/default/bluez-pan
    return
fi
############

############ DUND
#
# Run dund -- this allows ppp logins. 1 for enabled, 0 for disabled.
DUND_ENABLED=0

# Arguments to dund: defaults to acting as a server
DUND_OPTIONS="--listen --persist"

# Run dund --help to see the full array of options.
# Here are some examples:
#
# Connect to any nearby host offering access
# DUND_OPTIONS="--search"
#
# Connect to host 00:11:22:33:44:55
# DUND_OPTIONS="--connect 00:11:22:33:44:55"
#
# Listen on channel 3
# DUND_OPTIONS="--listen --channel 3"

# Special consideration is needed for certain devices. Microsoft
# users see the --msdun option.  Ericsson P800 users will need to
# listen on channel 3 and also run 'sdptool add --channel=3 SP'

############ PAND
#
# Run pand -- ethernet: creates new network interfaces bnep<N>
# that can be configured in /etc/network/interfaces
# set to 1 for enabled, 0 for disabled
PAND_ENABLED=0

# Arguments to pand
# Read the PAN howto for ways to set this up
# [http://bluez.sourceforge.net/contrib/HOWTO-PAN](http://bluez.sourceforge.net/contrib/HOWTO-PAN)
PAND_OPTIONS=""

# example pand lines
#
# Act as the controller of an ad-hoc network
# PAND_OPTIONS="--listen --role GN"
#
# Act as a network access point: routes to other networks
# PAND_OPTIONS="--listen --role NAP"
#
# Act as a client of an ad-hoc controller with number 00:11:22:33:44:55
# PAND_OPTIONS="--role PANU --connect 00:11:22:33:44:55"
#
# Connect to any nearby network controller (access point or ad-hoc)
# PAND_OPTIONS="--role PANU --search"


Let me know what you think.  =)

---

### Post by cdseaman on 2006-09-04
Hi, I have an MX1000 from Logitech that I'm trying to set up in Ubuntu.  The problem is that it won't pair with the laptop I"m using (an LG T1-7001A9).  The laptop sees the mouse and I can get it's hardware address but I believe it may need a key to enable security.  The problem is that when you press "connect" on the mouse I believe it creates that key, which of course you can't read.  Anyone have any exprience running one of these under ubuntu.  Logitech doesn't seem interested in helping me at this stage.

Thanks!
Conrad Seaman

---

### Post by bryan4134 on 2006-09-05
Hey - many thanks for this post - you have just saved me hours of trying to figure out my bluetooth mouse!!!  Followed your instructions and it worked first time.

Thanks again.

---

### Post by nrwilk on 2006-09-05
@ Flooghans -

The only difference I see between your files and mine is in /etc/default/bluez-utils.

Yours:
```
HIDD_ENABLED=1
HIDD_OPTIONS="--master --server --search"
HIDD_OPTIONS="--connect 00:07:XX:XX:XX:XX --server"
```
Mine:
```
HIDD_ENABLED=1
HIDD_OPTIONS="-i 00:00:00:00:00:00 --server"
```

So, delete the line in the middle, and change the argument on the last  line to -i instead of --connect.

Then restart and see if the mouse is detected.

With this setup my v270 is detected flawlessly anytime I turn it on.  Even if the computer is already on and I turn the mouse on.  It detcts it right away.

I hope this works for you!

nrwilk

---

### Post by Flooghans on 2006-09-06
@nrwilk

Tried that before.  I did again too, just in case.  No change.  Is there anything else you tried that might have fixed it?

---

### Post by nrwilk on 2006-09-15
> **Flooghans said:**
> @nrwilk

Tried that before.  I did again too, just in case.  No change.  Is there anything else you tried that might have fixed it?
Ok, so I just stumbled upon some more information.  I booted into Windows for the first time in a very long time (I was trying a fix for sound support on my laptop which required me to boot into Windows and turn the sound all the way up there - It did not work ](*,) ).  While I was there I was surprised to find that my mouse didn't work because I hadn't set it up yet.  So, I set it up in Windows.  After that, when I was back in ubuntu I could not get the mouse to work whatsoever.  KBluetoothD showed that the mouse was connected, but it must have only been seeing the mouse, because the mouse acted like it was not connected to anything.

So, I booted back into windows and disabled the mouse there, turned the mouse off, and rebooted once again.  The mouse was not automatically detected, but after putting it in locate mode and then issuing a "sudo hidd --search", it worked.  and now it works automatically again, both after turning the mouse off while the system is running, and after booting the system up initially.

So, if you dual boot with windows, and you have the mouse set up there, I'd try going into Windows and disabling the mouse there and trying it again in ubuntu.

Hope this helps! :D 

nrwilk

---

### Post by mtron on 2006-09-15
had the same experience :( 

windows seems to initalize something in the devices that "locks" them for ubuntu. i installed xp in a vmware server, as soon as i installed the windows bluetooth utils, the mouse was working for vmware, but not for ubuntu any more, i had to do a reboot to make it working again.

didn't trace down the bug till now, but there is deffinatly something wrong.

---

### Post by roderikk on 2006-09-15
My experience was such, that I needed to download newer firmware for my Logitech MX1000 mouse in order to make it run smoothly. Of course this could only be done in Windows....

---

### Post by Jonathan Métillon on 2006-10-24
Hi,

My mouse (Sony Vaio VGP-BMS30) is recognized and connected properly using *hidd --connect*.

It used to work very well. But since a few weeks, maybe because of an update, I can't move the cursor anymore! I mean, every buttons work: left, right, center and even Z axis. But the cursor just stands still when I move the mouse.

What's going on? How can I fix this?

---

### Post by loko on 2006-10-26
in edgy i cannot find /etc/default/bluez-utils anymore, while in dapper i did.

so where can i now add (in edgy):

```
HIDD_ENABLED=1
HIDD_OPTIONS="-i XX:XX:XX:XX:XX:XX --server"
```

Or is there now another way in edgy?

EDIT: bluez-utils is installed and also any bluetooth-related stuff, but i cannot find the /etc/default/bluez-utils file anymore

---

### Post by roderikk on 2006-10-26
I believe it is now called /etc/default/bluetooth . Good luck!

---

### Post by loko on 2006-10-26
thanks,

this is the right file.

But it dont't work.

/etc/defaults/bluetooth looks like this:

```
BLUETOOTH_ENABLED=1

############ HIDD
#
# To have Bluetooth mouse and keyboard support, get the
# Linux 2.6.6 patch or better from bluez.org, and set 
# HIDD_ENABLED to 1.
HIDD_ENABLED=1
#HIDD_OPTIONS="--master --server"
# to make hidd always use a particular interface, use something
# like this, substituting the bdaddr of the interface:
HIDD_OPTIONS="-i 00:07:61:4B:11:1D --server"
#
# remove '--master' if you're having trouble working with Ericsson
# T630 phones with hidd operational at the same time.
```

i have enabled all the important settings to get my mouse to work.

while in dapper it worked with these settings, in edgy it doesn't.

My mouse is working if i do "hidd --connect xxx", so what can i do?

---

### Post by rangar on 2006-10-27
I happened to observe a really strange keyboard behavior. Using my MS Bluetooth Keyboard, i could work with the Acronis True Image 9 boot cd (which indeed is based on Linux). Also, i was able to install the brand new Ubuntu 6.10 without any problem. But as soon as i had to login into the fresh installed system, the keyboard didn't work. Why is this so?

Last time i tried to get the keyboard working, i couldn't use it in Windows XP any longer. Maybe it's because i use the encryption feature of the keyboard. Dual booting is terrible: Once the keyboard works in Windows, it doesn't in Ubuntu and vice versa.

---

### Post by roderikk on 2006-10-27
Hi,

I added this line:

HIDD_OPTIONS="--connect 00:07:61:39:2F:C4 --connect 00:07:61:3E:C7:3C --server"

To connect my bluetooth keyboard and mouse and it seems to work (most of the times). Hope this helps.

---

### Post by rangar on 2006-10-27
What does this setting do? And does it really work with activated encryption? I can use my keyboard with both systems if i disable the encryption, but i'm not willing to do that (because i regularly use my pc for homebanking).

---

### Post by roderikk on 2006-10-27
It forces connection to both devices at startup. I have no experience with encryption so I really can't help you with that.

---

### Post by loko on 2006-10-28
> **roderikk said:**
> Hi,

I added this line:

HIDD_OPTIONS="--connect 00:07:61:39:2F:C4 --connect 00:07:61:3E:C7:3C --server"

To connect my bluetooth keyboard and mouse and it seems to work (most of the times). Hope this helps.

thank you roderikk,

this works for me

---

### Post by guyg on 2006-11-26
> **Burkey said:**
> Did you just pair or did you add the pairing command to the bluez script that I mentioned above?  My laptop can suspend and come back fine with working bluetooth mouse, I also have the mouse working after bootup without ever touching the console with that.

I added the command to the file but still no luck: When I close and re-open my mouse (I have a MoGo Mouse), I need to re-pair it (hehe :) or it doesn't work.

Guy

---

### Post by chaeron on 2006-12-04
I have the same problem as guyg.  Using Edgy and a Logitech v270 bluetooth mouse on a recent LG T1-Express laptop with builtin bluetooth.

If I hit the reset button on the mouse and issue a:

   sudo hidd --search

if finds my mouse and connects fine.

But a reboot doesn't automagically reconnect.

---

### Post by roderikk on 2006-12-05
It is strange, because I also sometimes have the same problem that it doesn't connect. But this only happens very spordically. Just in case however I've got a normal keyboard lying around to switch to a virtual terminal and issue a sudo --hidd search...

---

### Post by lamborghiniwang on 2006-12-05
> **chaeron said:**
> I have the same problem as guyg.  Using Edgy and a Logitech v270 bluetooth mouse on a recent LG T1-Express laptop with builtin bluetooth.

If I hit the reset button on the mouse and issue a:

   sudo hidd --search

if finds my mouse and connects fine.

But a reboot doesn't automagically reconnect.

Same problem here with IOGear mini bluetooth mouse. After I added the following line into /etc/default/bluetooth
```

HIDD_OPTIONS="-connect 00:0A:94:C1:A4:56  --server"

```
I get an error msg says:
```

root@Enzo:/etc/default# /etc/init.d/bluetooth start
 * Starting Bluetooth services                                                  Can't get device information: Host is down

```
But the mouse works after I click the reconnect button and type
```

hidd --search

```

---

### Post by grblmpfh on 2006-12-06
Yesterday i was reading this thread and tried every hint mentioned. It just drove me nuts... Then i found that "hidd" is not comming up if HIDD_OPTIONS="--connect <mouseadress>" is set. So i tried starting hidd as server (with default options) and did "hidd --connect <mouseadress>" manually => Mouse (V270) working fine!

So the problem lies in the startup of hidd (at least on my notebook). It first has to start as server and then the connects have to be made. 

I changed my /etc/init.d/bluetooth a little and the mouse is now working perfectly...

Greets
Chris

---

### Post by furriner on 2006-12-13
tadeusz@media:~$ sudo hidd --connect 00:50:F2:E7:C3:D2
Password:
Can't get device information: Host is down
tadeusz@media:~$ hcitool scan
Scanning ...
        00:50:F2:E7:C3:D2       Microsoft Mouse
tadeusz@media:~$ sudo hidd --connect 00:50:F2:E7:C3:D2
tadeusz@media:~$ cd /etc/default


Can anyone suggest why I get host is down message, and why my Bluetooth microsoft mouse does not automatically connect at startup?

---

### Post by x64Jimbo on 2006-12-13
are you putting the mouse in pairing mode first?

---

### Post by furriner on 2006-12-14
> **x64Jimbo said:**
> are you putting the mouse in pairing mode first?

I can't click the little button on the mouse every time it boots, it's not reasonable. I've tried setting options in /etc/default/bluetooth  to no avail.

Help? Why doesn't it work?

---

### Post by x64Jimbo on 2006-12-14
You've tried setting which options? Please post your configs.

---

### Post by angelofhope on 2007-01-24
> **lamborghiniwang said:**
> Same problem here with IOGear mini bluetooth mouse. After I added the following line into /etc/default/bluetooth
```

HIDD_OPTIONS="-connect 00:0A:94:C1:A4:56  --server"

```
I get an error msg says:
```

root@Enzo:/etc/default# /etc/init.d/bluetooth start
 * Starting Bluetooth services                                                  Can't get device information: Host is down

```
But the mouse works after I click the reconnect button and type
```

hidd --search

```

I was strugling myself with getting the bluetooth mouse to work on startup. I edited /etc/default/bluetooth to include 
HIDD_OPTIONS="--connect 00:16:38:xx:xx:xx --master --server"

And after searching for a while I found I just had to do the following once, to really make it work:

bluez-pin in 00:16:38:xx:xx:xx

I hope this can help people in the future, cause I'm a totaly new to this myself...

---

### Post by Jonathan Métillon on 2007-01-24
Hi angelofhope, and everyone,

I don't really get it: bluez-pin, which I had to install, is just a tool to ask for the PIN for my device. But I am already able to connect my mouse without a PIN.

By the way I tried it. When it asked me for a PIN, I typed nothing and just clicked OK. Then rebooted and still, the mouse is not connected at boot.

When I log in my GNOME session I have to open a terminal and issue the *hidd -connect* command to get my mouse to work. it's very boring.

Maybe I'm supposed to press the *connect* button sometime when the computer is starting?

Note: I have the HIDD_ENABLED and HIDD_OPTIONS lines in my */etc/default/bluetooth* config file.

---

### Post by roderikk on 2007-01-25
Have you tried putting that line in your startup script list?

System -> Preferences -> Sessions -> Start Up programs

(this is not necessary for me but it might help?)

---

### Post by Jonathan Métillon on 2007-01-25
> **roderikk said:**
> Have you tried putting that line in your startup script list?

Do you mean, the  *bluez-pin in ...* line?

If so, again, I don't know how it could help: my device works without a PIN. Did I miss something about bluez-pin?

---

### Post by roderikk on 2007-01-31
I was actually refering to the hidd --connect.

I usually run it as a sudo hidd --search though... maybe you can try that?

---

### Post by dw09577 on 2007-02-05
> **Burkey said:**
> I am by no means an expert on this but I do have it working well on mine.. I am using a Planex bluetooth mouse and usb adapter.

First make sure you have all the bluez stuff installed.

Do a ```
hcitool scan
```

To get the MAC addresses of all available devices, if this does not work then you may need to manually load the bluetooth modules, for me they auto-load on insert of the bluetooth device, you can see if the device is detected by checking the kernel messages.

Once you have that do a ```
sudo hidd --connect XX:XX:XX:XX:XX:XX
``` but substituting the MAC address of you're mouse.

It should just start working at that, since I want it to just work every time I plug the thing in I have edited /etc/default/bluez-utils on the lines ```
HIDD_ENABLED=1
HIDD_OPTIONS="-i XX:XX:XX:XX:XX:XX --server"
```

I am sure I left some stuff out, like that the mouse sometimes may not show up on a scan, in which case move it to ensure it is not asleep or press the little connect button on it.

Hope it works as well for you as it does for me

SWEET.  This worked with my off-brand USB-BT dongle and my MoGo PC Card mouse.  Thanks!  I would recommend the instructions to be as follows:
[LIST=1]
[*](press 'connect' button on mouse)
[*]sudo hcitool scan
[*](copy MAC address of mouse)
[*]sudo gedit /etc/default/bluez-utils
[*](add two lines listed above, but pasting your MAC over the XX:XX:XX...)
[*](save and close)
[*]sudo hidd --connect (paste MAC address)
[/LIST]

---

### Post by stuffelse on 2007-02-09
> **dw09577 said:**
> SWEET.  This worked with my off-brand USB-BT dongle and my MoGo PC Card mouse.  Thanks!  I would recommend the instructions to be as follows:
[LIST=1]
[*](press 'connect' button on mouse)
[*]sudo hcitool scan
[*](copy MAC address of mouse)
[*]sudo gedit /etc/default/bluez-utils
[*](add two lines listed above, but pasting your MAC over the XX:XX:XX...)
[*](save and close)
[*]sudo hidd --connect (paste MAC address)
[/LIST]

Alright, I had my Logitech V270 working on my last installation of Dapper AND Edgy, but couldn't get it this time...
I have tried EVERY SINGLE THING in this thread, until the very last thing(Quoted directions), and for some reason, it works all of a sudden!

the true test will be whether i have to link it manually EVERY time I want to use it.

---

### Post by 4FtHawaiian on 2007-02-20
Just wanted to say "Thanks, HEAPS" for this post. I've been using ubuntu for.. about 15 hours now? So far, thanks to these forums, I have my iBook G4 up and running, along with my 5G iPod (using Amarok). Not to mention, my Airport wireless and -- thanks to this post! -- my Logitech Travel BT mouse working flawlessly.. Edgy is really a beautiful OS, and I'm extremely impressed with the community as a whole.


Now, to see if I can get my SE phone working over bluetooth :)

---

### Post by roderikk on 2007-02-20
> **4FtHawaiian said:**
> Just wanted to say "Thanks, HEAPS" for this post. I've been using ubuntu for.. about 15 hours now? So far, thanks to these forums, I have my iBook G4 up and running, along with my 5G iPod (using Amarok). Not to mention, my Airport wireless and -- thanks to this post! -- my Logitech Travel BT mouse working flawlessly.. Edgy is really a beautiful OS, and I'm extremely impressed with the community as a whole.


Now, to see if I can get my SE phone working over bluetooth :)
And it is reactions like these that makes helping people all the more worth while!

Good luck with getting your phone to work and of course getting to grips with your new OS :-).

---

### Post by Amedee on 2007-02-20
Sorry for hijacking this thread, but could I please get some attention for this bug?
[https://bugs.launchpad.net/ubuntu/+source/bluez-utils/+bug/32415](https://bugs.launchpad.net/ubuntu/+source/bluez-utils/+bug/32415)

Logitech Bluetooth Desktop MX5000: keyboard + mouse + usb dongle.
Same problem in Dapper/Edgy/Feisty

* The keyboard works in grub.
* The keyboard & mouse work for a few seconds when gdm comes up.
* After a few seconds, keyboard and mouse freeze.
* Unplug the dongle & plug it back in.
* Keyboard and mouse work again after a second.
* Try to connect with a bluetooth phone (Nokia 6680): no bluetooth device
* sudo hid2hci
* Succesfull bluetooth connection between the pc and the phone (I was even able to send files)
* As soon as I have entered hid2hci, keyboard and mouse stop working
* Unplug the dongle & plug it back in.
* After a second, keyboard and mouse work again.
* As soon as the dongle is unplugged, the bluetooth connection with the phone is broken
* The only way to connect again with the phone, is hid2hci (and loose the keyboard&mouse again)

I would like to hear some fresh ideas, because I don't see it any more... :( :( :(

---

### Post by Amedee on 2007-03-05
*bump*

I'm sorry if I'm rude, but it's really frustrating to see that a bug remains unfixed for more than a year.

---

### Post by stuffelse on 2007-03-05
care to elaborate on that? having trouble with a bluetooth mouse? what setup are you using? what have you tried so far?

---

### Post by x64Jimbo on 2007-03-09
> **stuffelse said:**
> care to elaborate on that? having trouble with a bluetooth mouse? what setup are you using? what have you tried so far?
The setup is listed very specifically in the post. However, it's not nice to hijack threads. Please post your problem in a separate thread for your specific hardware.

---

### Post by Amedee on 2007-03-15
> **x64Jimbo said:**
> The setup is listed very specifically in the post. However, it's not nice to hijack threads. Please post your problem in a separate thread for your specific hardware.

That's always a problem: either I'm accused of hijacking a thread, or I'm accused of creating duplicate threads. The latter is usually less nice than the former.
My problem seemed to be (almost?) the same as everything else in the thread, that's why I used the existing thread.

---

### Post by stuffelse on 2007-03-15
well, if i'm hijacking i apologize, but I personally think this thread has been fairly on topic.

anyway, amedee, why don't you just start a new thread with an excessively detailed description

---

### Post by szxuzhou on 2007-03-16
Hi guys,
I have a Lenovo thinkpad T41p and Logitech V270 bluetooth. This thread is quite useful for me. I just post my code here. Its hopeful to be of any help with you.
```
HIDD_ENABLED=1
HIDD_OPTIONS="--server --search"
HIDD_OPTIONS="--connect 00:07:61:67:XX:XX --server"
```

Good luck!

---

### Post by Amedee on 2007-03-21
> **stuffelse said:**
> well, if i'm hijacking i apologize, but I personally think this thread has been fairly on topic.

anyway, amedee, why don't you just start a new thread with an excessively detailed description

I did, but except for over 60 people reading it, there haven't been any replies so far...

---

### Post by jshayden on 2007-03-21
so this thread enabled me to get my mouse working.  however, i cannot communicate with any other bluetooth devices now; even if the mouse is turned off.

any ideas?

thanks,
josh

---

### Post by maidhc on 2007-04-02
Just to add my tale of woe:

I'm once again trying to migrate away from windows and have installed 6.06 on a Dell Latitude x300 with the Truemobile (Broadcom) 350 bluetooth card.

I have done everything as above, and my logitech v270 works perfect*sometimes*, bust mostly is is very slow, laggy, and jumpy so as to be unusable. 

Any suggestions are very very welcome.

---

### Post by lightenup on 2007-04-21
I have run into the exact same problem with Edgy Eft and Feisty Fawn but NOT on Dapper Drake! Today I decided to install Feisty Fawn and make my mouse work after a reboot! Finally Success! 

Some background information: I have a Compaq nc6000 with a built in bluetooth receiver. I am using a Logitech v270 bluetooth mouse and a fresh install of Ubuntu 7.04. 

The first thing we need to do is modify the following line in /etc/default/bluez-utils

From:
HIDD_ENABLED=0

To:
HIDD_ENABLED=1

I did not add or remove anything else in this file! 


Next, we need to modify the /etc/init.d/bluetooth file look for the section start_hid():

From:

[ "$VERBOSE" != no ] && log_success_msg "Starting $HIDD_NAME..."
fi
}

To:

[ "$VERBOSE" != no ] && log_success_msg "Starting $HIDD_NAME..."
sudo hciconfig hci0 down
sudo hciconfig hci0 up
fi
}

Next we need to pair the device:
For my Logitech v270 I had to power off the mouse and then power it back on. Next, press and release the reset button. At this point you should see the green LED blinking on the bottom of the mouse. Back on the command line, enter in the following command:

sudo hidd --search

At this point your mouse should be working, now give the box a reboot and hopefully it will continue to work!

---

### Post by roderikk on 2007-05-28
Hi, after struggling for a while by reconnecting my bluetooth keyboard and mouse after every setup I found this site:

[https://help.ubuntu.com/community/BluetoothSetup](https://help.ubuntu.com/community/BluetoothSetup)

And that solved all my woes!

---

### Post by drapaki on 2007-09-13
trying to get my mogo bluetooth mouse working.. i don't see what is wrong here:

```
$ sudo hidd --search
Searching ...
$ sudo hcitool scan
Device is not available: No such device

```

so it doesn't pick anything up w/ the first command and the second command yields and even more concerning error.

what is going on?

---

### Post by stuffelse on 2007-09-13
did you set the mouse to visible? (hit the button on the bottom) also, you did install the necessary utilities, right? ( [https://help.ubuntu.com/community/BluetoothSetup](https://help.ubuntu.com/community/BluetoothSetup) )

---

### Post by drapaki on 2007-09-13
i did... is there a 'device manager' type place where i can even check whether i have a bluetooth capability?  I know i have the light.. but i never used it when i had XP on this machine...

---

### Post by BigDaddy-CF- on 2007-10-06
Sweetness thnx just the fix I was looking for. Props to you sir it works with my Interlink ExpressCard Media Remote for Bluetooth model VP6600R like a charm. In case it matters DELL XPS 1710. Now I can truly use all of this machine's abilities in Ubuntu. This was the last piece of the puzzle. Now if we can just get my college to switch to open source OS's and tools, and get gaming really hopping on Linux I would never have to use a microsft product again:)

---

### Post by tungsai on 2007-11-02
Hey, All!

I'm trying to get the Logitech M-RBB93 to sync with my IBM Thinkpad X60s. It worked in winders. "hcitool scan" works fine (I'm su'ed). It shows the MAC, and "Bluetooth Travel Mouse". So, it can SEE the mouse.

I turn the mouse on, hold the RESET button for a second or two, and the little LED by the "ON" indicator is blinking. So, I run "hidd -connect 00:xx:xx:xx:xx:xx" (Replacing the X's with of course the true address given by the hcitool scan).

The result? It tries for about 10-20 seconds, and then says "Can't get device information: Host is down".

Now, I did right-click up on the bluetooth icon in the taskbar and make sure that "Serial service" is running... didn't know if that was necessary or not.

Aargh......:confused::confused::confused:

---

### Post by indigomm on 2007-11-08
I've just been having a lot of the problems reported in this thread with my mouse (a Logitech model). It used to work fine, and then suddenly stopped connecting. If I pressed the reset button on the bottom and did a search, it was finding the mouse but then giving "Can't get device information: Host is down". Searching around I came across this thread, but I had already tried everything in it.

I finally tracked this down to something very simple - not enough battery power. With low battery, all the lights were on and the mouse responded to a scan - but just wouldn't connect. So worth trying a fresh set of batteries if you are having problems.

---

### Post by snovak on 2007-12-18
works perfectly.. thank you for such a straight forward explanation.

---

### Post by kismeras on 2008-01-31
Hey Everyone, 

I am new to Linux. I am running Ubuntu 7.10 on an Acer Aspire 5672 laptop. It has built in Bluetooth. I have a Manhattan mini bluetooth mouse that i can not get to connect at all. Here is what happens when i try :

Kismeras@Acer:~$ hcitool scan
Scanning ...
        00:1B:xx:xx:xx:xx      n/a
Kismeras@Acer:~$ sudo hidd --connect 00:1B:xx:xx:xx:xx
[sudo] password forKismeras:
Can't get device information: Host is down

Any help would be greatly appreciated. Thanks.

---

### Post by mtron on 2008-01-31
more info please! 

post your /etc/bluetooth/hcid.conf and check that 
Autostart=true
is set in the "input.service" configuration file in the same directory.

a short google search led me to the[ gentoo wiki page]("http://gentoo-wiki.com/HARDWARE_Acer_Aspire_5672_WLMi") about your laptop. This has some very useful info about your hardware, and it tells you that bluetooth, wlan & sound are supported by the kernel since 2.6.20 (for the intel w-lan chipset). So you shouldn't have any general driver problems and you Troubles are related to your local configuration.

---

### Post by kismeras on 2008-01-31
How do i do that? I am very new to Linux/Ubuntu. I don't know how to get to my

/etc/bluetooth/hcid.conf

Thanks.

---

### Post by kismeras on 2008-01-31
Hey Mtron, 

Thanks for the replies. I looked at that wiki site you inked to, but i don't really understand it.  I'm not familiar with command lines and such. I try to read tutorials and how to's and copy the commands and paste them. I tried the command that was in the bluetooth section, but it said " bash: emerge: command not found ". I have downloaded an ubuntu desktop student manual. Hopefully i can learn more after reading it. Until then any more help that you or anyone else can give is much appreciated. Thanks.

---

### Post by mtron on 2008-01-31
Apps - Accessoires - Terminal
(copy & Paste

```
gedit /etc/bluetooth/hcid.conf
```

just to explain what we are doing:

gedit is a text editor that opens the file hcid.conf which lives his stuble days in the directory /etc/bluetooth (you will come back to the /etc dir quite some times in future). In this dir most debian & ubuntu programs store there system wide settings.

if you want to be able to make permanent changes to the configuration file, you need to use "sudo" . this sudo allows you to do stuff a normal user isn't (like opening & using the package manager)

```
sudo gedit /etc/bluetooth/hcid.conf
```

opens the text editor as root and allows you to save changes to the file.  But be careful and think twice before you click on "Save".

Always make backups of the configuration files you are about to change.
e.g

```
sudo cp /etc/bluetooth/hcid.conf /etc/bluetooth/hcid.conf.backup
```

would create such a backup. To resore the original file from the backup you would do then:

```
sudo cp /etc/bluetooth/hcid.conf.backup /etc/bluetooth/hcid.conf
```

but such stuff is not part of this thread, please open a new one for such problems!

---

### Post by kismeras on 2008-01-31
Ok, i did it and this is what i get :

#
# HCI daemon configuration file.
#

# HCId options
options {
	# Automatically initialize new devices
	autoinit yes;

	# Security Manager mode
	#   none - Security manager disabled
	#   auto - Use local PIN for incoming connections
	#   user - Always ask user for a PIN
	#
	security user;

	# Pairing mode
	#   none  - Pairing disabled
	#   multi - Allow pairing with already paired devices
	#   once  - Pair once and deny successive attempts
	pairing multi;

	# Default PIN code for incoming connections
	passkey "1234";
}

# Default settings for HCI devices
device {
	# Local device name
	#   %d - device id
	#   %h - host name
	name "%h-%d";

	# Local device class
	class 0x000100;

	# Default packet type
	#pkt_type DH1,DM1,HV1;

	# Inquiry and Page scan
	iscan enable; pscan enable;
	discovto 0;

	# Default link mode
	#   none   - no specific policy 
	#   accept - always accept incoming connections
	#   master - become master on incoming connections,
	#            deny role switch on outgoing connections
	lm accept;

	# Default link policy
	#   none    - no specific policy
	#   rswitch - allow role switch
	#   hold    - allow hold mode
	#   sniff   - allow sniff mode
	#   park    - allow park mode
	lp rswitch,hold,sniff,park;
}


One day i hope to understand what this all means. Thanks.

*EDIT* - I see where it says pairing is disabled, but i don't know how to enable it.

---

### Post by mtron on 2008-01-31
change 

```
	# Security Manager mode
	#   none - Security manager disabled
	#   auto - Use local PIN for incoming connections
	#   user - Always ask user for a PIN
	#
	security user;
```

to
```

	# Security Manager mode
	#   none - Security manager disabled
	#   auto - Use local PIN for incoming connections
	#   user - Always ask user for a PIN
	#
	security auto;
```

save this file, close gedit and back in the terminal you can restart the bluetooth subsystem very easy:
```
sudo /etc/init.d/bluetooth restart
```

now the mouse might connect ;) give it another try.

---

### Post by kismeras on 2008-01-31
OK, that got me a little further. However, when i go to the bluetooth icon and click on browse device i see bt-mouse. YAY.  Problem is when i click connect i get the following popup error message :

"obex://[00:15:xx:xx:xx:xx]"
is not a valid location. 

Any ideas?

*********   SUCCESS   **************

WoooHoooooo

after your helping me and trying this:

sudo hidd --connect XX:XX:XX:XX:XX:XX

from the first page of this thread, it's working. 

Thanks you so much for all of your help and to everyone else who has and continues to help us noobs out. 

Thank you.:guitar:

---

### Post by mtron on 2008-01-31
nice, keep on having fun with ubuntu. :)

---

### Post by kismeras on 2008-01-31
I will. Thanks again for all of your help.

---

### Post by kismeras on 2008-01-31
OK, so i got it working. The i left the house for a few and came back. The screen was off so i moved the mouse around to wake it up....nothing. I used the touchpad and it came back on. It seems that the mouse doesn't stay connected. I had to go back to the terminal and run the

```
sudo hidd --connect XX:XX:XX:XX:XX:XX
```

command to get it working again. Any way i can save myself that step by making it just work? Thanks.

---

### Post by dalidowicz on 2008-02-08
Hey everyone,

I've been tinkering around trying to get my Bluetooth Mogo Mouse working with Ubuntu, and the following link did the trick:

[https://help.ubuntu.com/community/BluetoothSetup](https://help.ubuntu.com/community/BluetoothSetup)

Give it a try if you've been frustrated by everything else.

Cheers,
Matt

---

### Post by miketet on 2008-05-19
> **Burkey said:**
> I am by no means an expert on this but I do have it working well on mine.. I am using a Planex bluetooth mouse and usb adapter.

First make sure you have all the bluez stuff installed.

Do a ```
hcitool scan
```

To get the MAC addresses of all available devices, if this does not work then you may need to manually load the bluetooth modules, for me they auto-load on insert of the bluetooth device, you can see if the device is detected by checking the kernel messages.

Once you have that do a ```
sudo hidd --connect XX:XX:XX:XX:XX:XX
``` but substituting the MAC address of you're mouse.

It should just start working at that, since I want it to just work every time I plug the thing in I have edited /etc/default/bluez-utils on the lines ```
HIDD_ENABLED=1
HIDD_OPTIONS="-i XX:XX:XX:XX:XX:XX --server"
```

I am sure I left some stuff out, like that the mouse sometimes may not show up on a scan, in which case move it to ensure it is not asleep or press the little connect button on it.

Hope it works as well for you as it does for me

Many thanks! I used he above process on ubuntu 8.0.4 with my Microsoft Bluetooth Notebook Mouse 5000, and it worked like a charm. The only difference was the filename to edit, which was /etc/default/bluetooth. Once done, the mouse started working, and kept working, even after a restart or resume from suspend mode.

---

### Post by BlackRaven on 2008-05-20
Thanks guys, that was a really easy fix. =D>
Got my Logitech bluetooth mouse to work in no time.

---

### Post by pbjoiner on 2008-05-22
Thank you so much. You've saved me from the touchpad.

I really think that Bluez really ought to handle this sort of thing a little more GUIly or automatically.

For those interested, I'm running my Microsoft Presenter Mouse 8000 and *all* the buttons work. The forward and back buttons work. Even the volume buttons work in "remote control" mode. my dongle is a Kensington Bluetooth Micro adapter.

---

### Post by rootneg on 2008-05-28
> **pbjoiner said:**
> 
For those interested, I'm running my Microsoft Presenter Mouse 8000 and *all* the buttons work. The forward and back buttons work. Even the volume buttons work in "remote control" mode. my dongle is a Kensington Bluetooth Micro adapter.


I have the same mouse and I still have problems with it "falling asleep" and losing connection.

my /etc/conf.d/bluetooth (equiv to /etc/default/bluetooth)
```

# Bluetooth configuraton file

# Start of hcid (allowed values are "true" and "false")
HCID_ENABLE=true

# Config file for hcid
HCID_CONFIG="/etc/bluetooth/hcid.conf"

# Start sdpd (allowed values are "true" and "false")
SDPD_ENABLE=true

# Start hidd (allowed values are "true" and "false")
HIDD_ENABLE=true

# Arguments to hidd
HIDD_OPTIONS="-i 00:12:5A:66:AA:B0 --server"

# Run hid2hci (allowed values are "true" and "false")
HID2HCI_ENABLE=true

# Bind rfcomm devices (allowed values are "true" and "false")
RFCOMM_ENABLE=true

# Config file for rfcomm
RFCOMM_CONFIG="/etc/bluetooth/rfcomm.conf"

# Start dund (allowed values are "true" and "false")
# If you want to use dund, you must install: net-dialup/ppp .
DUND_ENABLE=false

# Arguments to dund
DUND_OPTIONS="--listen --persist"

# Start pand (allowed values are "true" and "false")
PAND_ENABLE=false

# Arguments to pand
PAND_OPTIONS="--listen --role NAP"

```

and my /etc/bluetooth/hcid.conf
```

#
# HCI daemon configuration file.
#

# HCId options
options {
        # Automatically initialize new devices
        autoinit yes;

        # Security Manager mode
        #   none - Security manager disabled
        #   auto - Use local PIN for incoming connections
        #   user - Always ask user for a PIN
        #
        security auto;

        # Pairing mode
        #   none  - Pairing disabled
        #   multi - Allow pairing with already paired devices
        #   once  - Pair once and deny successive attempts
        pairing multi;

        # PIN helper
        pin_helper /usr/bin/bluepin;

        # D-Bus PIN helper
        #dbus_pin_helper;
}

# Default settings for HCI devices
device {
        # Local device name
        #   %d - device id
        #   %h - host name
        name "BlueZ %h (%d)";

        # Local device class
        #class 0x3e0100;
        class 0x000100;
        
        # Default packet type
        #pkt_type DH1,DM1,HV1;

        # Inquiry/Page scan and discoverable timeout
        iscan enable;
        pscan enable;
        discovto 0;

        # Default link mode
        #   none   - no specific policy 
        #   accept - always accept incoming connections
        #   master - become master on incoming connections,
        #            deny role switch on outgoing connections
        lm accept;

        # Default link policy
        #   none    - no specific policy
        #   rswitch - allow role switch
        #   hold    - allow hold mode
        #   sniff   - allow sniff mode
        #   park    - allow park mode
        lp rswitch,hold,sniff,park;

        # Authentication and Encryption (Security Mode 3)
        auth enable;
        encrypt enable;
}

```

And how did you get the presenter mode buttons working? I have the top buttons working, but only the volume up/down works in presenter mode.


Any ideas?

---

