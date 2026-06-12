---
title: "Blue Tooth adapter configuration"
date: 2007-10-28
forum: Hardware &amp; Laptops
---

### Post by hitekwaiter on 2007-10-28
I think I"ve installed all Bluetooth applications from the repositories, but I still cannot pair a device. Specifically, I'm running Gutsy and have a treo phone that I know has a blank passcode. When I try to connect to my Gutsy laptop, i can see that the device exists, but a passcode option comes up.  I have no idea what to type into my phone for a passcode.
One other thing, if you are familiar with Bluetooth, most bluetooth utilities have an application that alows you to browse the nearby devices. I can't find anything like that for Ubuntu.

As I said, Ive been out to the repositories and installed anything associated with Bluetooth. 
1. I need to know how to set the passcode for my Ubuntu laptop.
2. I need to know how to connect to other surrounding devices from my laptop.


Thanks in advance.:confused:

---

### Post by bubbalouie on 2007-10-28
The default bluetooth passkey is **1234**. To check use:

>  nano /etc/bluetooth/hcid.conf 

I use the kbluetooth tool from my system tray to connect to a phone etc for file transfers (syncing is still a no go for me), it should work under gnome if you install all of the right components, but I am not certain as I run kubuntu.

Mice and keyboards work a treat too BTW, it just takes a few minutes to get it cranking (it is best to edit a few files as this works 100% of the time).

Good Luck

---

### Post by MickS on 2007-10-28
> **bubbalouie said:**
> The default bluetooth passkey is **1234**. To check use:



I use the kbluetooth tool from my system tray to connect to a phone etc for file transfers (syncing is still a no go for me), it should work under gnome if you install all of the right components, but I am not certain as I run kubuntu.

Mice and keyboards work a treat too BTW, it just takes a few minutes to get it cranking (it is best to edit a few files as this works 100% of the time).

Good Luck

Please tell us what files to edit and how, I can't get it to work either, I'm using Kubuntu on Gutsy as well.
TIA
Mick

---

### Post by bubbalouie on 2007-10-28
This is an edited version of the following HOWTO [link]("http://ubuntuforums.org/showthread.php?p=2017615"), please note I can not guarantee this will work for your system, you should always backup any files before changing them.

I have a bluetooth Logitech DiNovo keyboard and MX1000 mouse, as well as a bluetooth travel mouse and I use Kubuntu with a VAIO laptop. This tutorial should help you getting your keyboard and mouse up and running (and automatically reconnecting after you reboot, idle, or whatever).

This tutorial is an adapted version of this forum thread by naag.

[SIZE="6"]Getting Started[/SIZE]

We need the MAC address (e.g. 00:00:00:00:00) of the mouse and keyboard. I shall use KEYBOARD_ADDR and MOUSE_ADDR where you should find the addresses for the keyboard and mouse respectively. Press the button on the mouse that makes it visible to be found by the computer. Do the same for the keyboard. Now open a terminal window and run the following command:

```
 user@computer:~$ hcitool scan
 Scanning ...
         KEYBOARD_ADDR       Microsoft Wireless Keyboard
         MOUSE_ADDR          Microsoft Mouse
 user@computer:~$
```

[SIZE="6"]Adding the Keyboard and Mouse[/SIZE]

Now we need to add the keyboard and mouse to the bluetooth configuration files. Run the following command to pop up kate:

```

 user@computer:~$ sudo kate /etc/bluetooth/hcid.conf
```

You may be asked for your password, this is because we used sudo.

At the end of the file, add the following (replacing KEYBOARD_ADDR and MOUSE_ADDR for the keyboard and mouse MAC addresses as found earlier):

```

device 00:07:61:33:EE:EE {
	name "Logitech diNovo Keyboard";
	auth enable;
	encrypt enable;
}
 
device 00:07:61:33:EE:EE {
	name "Logitech Mediapad";
	auth enable;
	encrypt enable;
}

device 00:07:61:33:EE:EE {
	name "Logitech MX1000 mouse"
}

device 00:07:61:3f:EE:EE {
	name "Bluetooth travel mouse"
}
```

Now you need to restart the bluetooth subsystem so that it refreshes it's configuration file.

```
 user@computer:~$ sudo /etc/init.d/bluetooth restart
  * Restarting Bluetooth services... [ ok ]
```

[SIZE="6"]Pairing the Devices[/SIZE]

You now need to pair the devices with the computer. Do not press any buttons on the keyboard as we'll need to use it to enter a passcode so we can pair. Run the following command:

```

 user@computer:~$ sudo hidd --search
 Searching ...
         Connecting to device MOUSE_ADDR
         Connecting to device KEYBOARD_ADDR
 user@computer:~$
```

They could pair with the computer in any order, you will need to remember which one is the keyboard. As soon as Connecting to device KEYBOARD_ADDR appears you must enter a PIN code into the keyboard. It must consist of numbers not using the numpad, I can't remember how many you can use, but somewhere between 4 and 8 should be fine. Type this number in to the keyboard and press Return. I did not need to perform this step, however some devices may require it.

A window should pop up on your computer asking you for the number you just entered on the keyboard. Again I did not need to perform this step, however some devices may require it.

[SIZE="6"]Connecting at Boot[/SIZE]

In order to get your mouse and keyboard to connect at boot time do the following:

```
 user@computer:~$ sudo kate /etc/default/bluetooth
```

Find the line with the following:

```
 HIDD_ENABLED=0
```
 
Change it to:

Code:

```
 HIDD_ENABLED=1
```

Now reboot and hopefully they'll automatically connect (give them a few seconds to connect after you move the mouse/press a key).

Sometmies a device may not connect due to new batteries or some other malfunction, the following command should force a reconnect:

```
user@computer~:$ sudo hidd --search
```

[SIZE="6"]Enabling Extra Mouse Buttons[/SIZE]

Finally, in order to enable the back and forwards buttons on my MX1000 mouse I altered my xorg.conf file as follows:

> user@computer~: sudo kate/etc/X11/xorg.conf

Find the section that for the 'Configured Mouse' and replace it with the following:

```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ExplorerPS/2"
	Option		"Emulate3Buttons"	"false"
	Option		"Buttons" "7"
	Option		"ButtonMapping" "1 2 3 6 7"
	Option		"ZAxisMapping" "4 5"
EndSection
```

Now save the file and close kate. Your extra buttons should now work when you restart X (ctrl+alt+backspace). You will find a tool in the KDE menu system group group called kbluetooth, this will provide a facility for connecting to devices such as phones for sending files.

[SIZE="6"]Reference Files[/SIZE]

For reference (with some address changes etc) here is what my */etc/bluetooth/hcid.conf* looks like:

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


device 00:07:61:33:EE:EE {
	name "Logitech diNovo Keyboard";
	auth enable;
	encrypt enable;
}

device 00:07:61:33:EE:EE {
	name "Logitech Mediapad";
	auth enable;
	encrypt enable;
}

device 00:07:61:33:EE:EE {
	name "Logitech MX1000 mouse"
}

device 00:07:61:3f:EE:EE {
	name "Bluetooth travel mouse"
}

```

And my */etc/default/bluetooth* file:

```
 # Defaults for bluez-utils

# This file supersedes /etc/default/bluez-pan.  If
# that exists on your system, you should use this
# file instead and remove the old one.  Until you
# do so, the contents of this file will be ignored.

# start bluetooth on boot?
# compatibility note: If this variable is not found bluetooth will
# start
BLUETOOTH_ENABLED=1

############ HIDD
#
# To have Bluetooth mouse and keyboard support, get the
# Linux 2.6.6 patch or better from bluez.org, and set 
# HIDD_ENABLED to 1.
HIDD_ENABLED=1
HIDD_OPTIONS="--master --server"
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
# http://bluez.sourceforge.net/contrib/HOWTO-PAN
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

############ SDPTOOL
# this variable controls the options passed to sdptool on boot, useful if you
# need to setup sdpd on boot.
# options are ;-separated, i.e. for every ; an sdptool instance will be
# launched
#
# examples:
# SDPTOOL_OPTIONS="add --channel=3 SP" # ericsson P800 serial profile
# SDPTOOL_OPTIONS="add --channel=8 OPUSH ; add --channel=9 FTRN" # motorola
#                                             # object push and file transfer
SDPTOOL_OPTIONS=""
 
```

---

### Post by MickS on 2007-10-28
Thanks for that lot, I should have been more clear though because my problem is sending stuff from my phone to the PC, photos in particular.
Thanks for your trouble.
Mick

---

### Post by bubbalouie on 2007-10-28
Ah, apologies for that, you should be able to left click the tray icon for kbluetooth, it will pop up a konqueror window which will pause for a while as it searches (make certain the phone is discoverable), an icon for your phone should appear. Double click the icon, you may then be asked for a pin (on the phone or the PC, I can't remember which is first as mine remembers the phone from the previous session). Pick a pin(this could also be in the next step, as I have said, my phone and laptop remember each other), you should then be greeted with a nice little file transfer icon and maybe some other icons (depending on the phones feature set), the rest should hopefully just work like a file browser (a slow one mind you). Failing that, you may need to look for any differences between my sample files and your own files.

Good Luck :)

Ryan

---

### Post by hitekwaiter on 2007-10-28
OKay, thanks for all the replies. Thanks to you, I was able to pair my laptop and treo phone, but I should have explained further. I'm trying to do something that I have done with my windows laptop many times, that is I'm trying to use the dial up networking feature on the phone to connect the laptop to the internet. 

If I"m somewhere where there is no internet connnection, I want to use the internet connection on my phone...Does this make sense?

Now that I have them paired,  how do I go about doing this?:)

---

### Post by bubbalouie on 2007-10-28
That I am unsure of, all I can suggest is kppp may be a starting point, go to connect to, then configure-> modems-> new, then if you scroll down far enough under modem device you will see */dev/rfcomm#* one of these should represent the serial port profile on a GPRS/EDGE/EVDO bluetooth phone. 

After which you just need to issue a few AT commands to specify your APN server etc. However, I've never done this, so all of the above is speculation. I find my phone (fairly basic by modern standards [although, so to is the iPhone, that thing will never make sense to me]) has adequate email and web browsing for my essential needs whilst traveling.

The following may also help you, though I can't be sure sorry:

[http://ubuntuforums.org/showthread.php?t=464613](http://ubuntuforums.org/showthread.php?t=464613)

---

