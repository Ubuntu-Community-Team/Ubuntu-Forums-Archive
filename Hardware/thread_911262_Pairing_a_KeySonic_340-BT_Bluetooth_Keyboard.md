---
title: "Pairing a KeySonic 340-BT Bluetooth Keyboard"
date: 2008-09-05
forum: Hardware
---

### Post by guardian_de on 2008-09-05
Hi,

I have a KeySonic 340-BT Bluetooth keyboard which I'm not able to pair with Ubuntu Hardy.

To connect the keyboard I'm turning it on and put it into pairing mode. Then I run the following command which basically has no effect:

```
# sudo hidd --search
Searching ...
	Connecting to device 00:18:00:00:66:89
```

My older Think Outside (Anycom) keyboard works flawlessy and the KeySonic one works out of the box with OS X.

Any hints? Thanks.

---

### Post by guardian_de on 2008-09-05
Maybe some more information: After starting the hidd the connection indicator on the keyboard still signals that it is in pairing mode.

hidd says that the keyboard is connected - whatever that means:

```
# hidd --show
00:18:00:00:66:89 PSTC Bluetooth Keyboard [0dc6:3752] connected
```

---

### Post by alfonso78 on 2008-10-24
> **guardian_de said:**
> Maybe some more information: After starting the hidd the connection indicator on the keyboard still signals that it is in pairing mode.

hidd says that the keyboard is connected - whatever that means:

```
# hidd --show
00:18:00:00:66:89 PSTC Bluetooth Keyboard [0dc6:3752] connected
```

Hi, I have exactly the same problem.
In fact, I found several references in internet about it...

Did you manage to fix it?

thank you,

alfonso

---

### Post by guardian_de on 2008-10-25
Unfortunately not - I still use that ugly wired keyboard with a built-in hub and an USB mouse. Maybe 8.10 fixes it.

---

### Post by guardian_de on 2008-11-01
The answer is Intrepid Ibex. Just left click the Bluetooth icon in the top panel, choose "Setup device...", press "Forward", select the keyboard from the list and enter the code and press return. That's it.

Ubuntu and Linux developers - thank you very much.

---

### Post by alfonso78 on 2008-11-01
> **guardian_de said:**
> The answer is Intrepid Ibex. Just left click the Bluetooth icon in the top panel, choose "Setup device...", press "Forward", select the keyboard from the list and enter the code and press return. That's it.

Ubuntu and Linux developers - thank you very much.

Hi!

you mean that with ubuntu 8.10 it works out of the box?

very very nice. :)

since I would rather not install that where I want to use the BT keyboard (I'm running a smaller debian distribution on an embedded computer), could you please be so kind to try to help me out with my problem?

can you post the output of the command (to get which release of BlueZ you have):

```
dpkg -l | grep -i blu
```

also, can you please post the content of all files in /etc/bluetooth/ ?

```
ls -l /etc/bluetooth/
```

and depending on the output of ls:

```
cat /etc/bluetooth/main.conf
```

```
cat /etc/bluetooth/input.conf
```

and finally 
```
cat /etc/X11/xorg.conf
```

thanks a lot, your help would really make a difference!

cheers,

alfonso

---

### Post by guardian_de on 2008-11-02
Here you go:

```
root@lemac:~# dpkg -l | grep -i blu
ii  bluetooth                                 4.12-0ubuntu5                         Bluetooth support
ii  bluez                                     4.12-0ubuntu5                         Bluetooth tools and daemons
ii  bluez-alsa                                4.12-0ubuntu5                         Bluetooth audio support
ii  bluez-cups                                4.12-0ubuntu5                         Bluetooth printer driver for CUPS
ii  bluez-gnome                               1.8-0ubuntu1                          Bluetooth utilities for GNOME
ii  bluez-gstreamer                           4.12-0ubuntu5                         Bluetooth gstreamer support
ii  bluez-utils                               4.12-0ubuntu5                         Transitional package
ii  libbluetooth3                             4.12-0ubuntu5                         Library to use the BlueZ Linux Bluetooth sta
ii  liblua5.1-0                               5.1.3-1                               Simple, extensible, embeddable programming l

```

```
root@lemac:~# for i in /etc/bluetooth/* ; do echo ; echo $i ; echo ; cat $i ; done

/etc/bluetooth/audio.conf

# Configuration file for the audio service

# This section contains options which are not specific to any
# particular interface
[General]

# Switch to master role for incoming connections (defaults to true)
#Master=true

# If we want to disable support for specific services
# Defaults to supporting all implemented services
#Disable=Control,Source

# SCO routing. Either PCM or HCI (in which case audio is routed to/from ALSA)
# Defaults to HCI
#SCORouting=PCM

# Headset interface specific options (i.e. options which affect how the audio
# service interacts with remote headset devices)
[Headset]

# Set to true to support HFP (in addition to HSP only which is the default)
# Defaults to false
HFP=false

# Just an example of potential config options for the other interfaces
#[A2DP]
#SBCSources=1
#MPEG12Sources=0

/etc/bluetooth/input.conf

# Configuration file for the input service

# This section contains options which are not specific to any
# particular interface
[General]

# Set idle timeout (in minutes) before the connection will
# be disconnect (defaults to 0 for no timeout)
#IdleTimeout=30

/etc/bluetooth/main.conf

[General]

# List of plugins that should not be loaded on bluetoothd startup
#DisablePlugins = network,input

# Default adaper name
# %h - substituted for hostname
# %d - substituted for adapter id
Name = %h-%d

# Default device class. Only the major and minor device class bits are
# considered
Class = 0x000100

# How long to stay in discoverable mode before going back to non-discoverable
# The value is in seconds. Default is 180, i.e. 3 minutes.
# 0 = disable timer, i.e. stay discoverable forever
DiscoverableTimeout = 0

# Use some other page timeout than the controller default one
# (16384 = 10 seconds)
PageTimeout = 8192

# Behaviour for Adapter.SetProperty("mode", "off")
# Possible values: "DevDown", "NoScan" (default)
OffMode = NoScan

# Discover scheduler interval used in Adapter.DiscoverDevices
# The value is in seconds. Defaults is 0 to use controller scheduler
DiscoverSchedulerInterval = 0

/etc/bluetooth/network.conf

# Configuration file for the network service

# This section contains options which are not specific to any
# particular interface
[General]

# Disable link encryption: default=false
#DisableSecurity=true

[PANU Role]

# Network interface name for PANU for connections. default:bnep%d
# (up to 16 characters)
#Interface=

# PAN user connection interface up script. default:none
Script=avahi-autoipd

[GN Role]

# Network Interface name for Group Network server. default:pan0
#Interface=

# Group Network connection interface up script. default:none
Script=avahi-autoipd

[NAP Role]

# Network Interface name for Network Access Point server. default:pan1
#Interface=

# Network Access Point connection interface up script. default:none
Script=dhclient

/etc/bluetooth/rfcomm.conf

#
# RFCOMM configuration file.
#

#rfcomm0 {
#	# Automatically bind the device at startup
#	bind no;
#
#	# Bluetooth address of the device
#	device 11:22:33:44:55:66;
#
#	# RFCOMM channel for the connection
#	channel	1;
#
#	# Description of the connection
#	comment "Example Bluetooth device";
#}

```

And finally

```
root@lemac:~# cat /etc/X11/xorg.conf 
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

```

Hope this helps!

PS: It worked out the box on my ThinkPad T60, but on my Mac Mini it initially didn't work (pairing failed) but in the end after removing and readding the device several times and maybe related to an intermediate kernel update it worked too.

---

### Post by alfonso78 on 2008-11-02
> **guardian_de said:**
> Here you go:

Hope this helps!

PS: It worked out the box on my ThinkPad T60, but on my Mac Mini it initially didn't work (pairing failed) but in the end after removing and readding the device several times and maybe related to an intermediate kernel update it worked too.

Thanks,

you've been very kind in taking your time to do this, but all files seem untouched.

I downloaded the ubuntu 8.10 live cd but it didn't work for me. I perform scan, I see the keyboard, but I don't get the PIN request message.

Anyway, it's a good point that BlueZ 4.x works with "our" keyboard. It will just required some more time to figure it out.

cheers,

---

### Post by alfonso78 on 2008-11-03
> **guardian_de said:**
> Here you go:

Hope this helps!

PS: It worked out the box on my ThinkPad T60, but on my Mac Mini it initially didn't work (pairing failed) but in the end after removing and readding the device several times and maybe related to an intermediate kernel update it worked too.

Hi,

just in case you're still "out there" willing to help me...

Finally I tried a couple of time with ubuntu 8.10 and I managed to get the pairing done, but that still seems not enough for me...

So if you could be so kind, I have a couple of more questions for you:

after successful pairing, if you type on your keyboard, does that 2nd led (with the flash icon) light up? Mine does, but on Windows it never lights up (1st hint that something is wrong).

Also, if from a console you type 

```
voyage:~/bluez-4.17/test# hcitool con
Connections:
voyage:~/bluez-4.17/test#

```

do you get any output under connections?

I'm almost sure pairing works for me, since exactly after I type the same PIN on the keyboard and press enter, the pairing led stops flashing.

But still one little thing is missing. GRRRRRRRRRRRR

In case you really really feel in a "giving" mood, I have one more question. if you run hcidump (you prob need to compile it from [http://bluez.sf.net/download/](http://bluez.sf.net/download/)), do you see anything when you press keys on your keyboard? It's a BT "sniffer", and I see many packets during pairing, but nothing after pairing when I press the buttons.

I just have the feeling after pairing I should do something like authorizing or something...

Well, thanks,

alfonso

---

### Post by guardian_de on 2008-11-04
Hi Alfonso,

just a quick answer since I'm in a hurry: The flash indicator only blinks after the keyboard has been switched on. When the handshake is finished it doesn't light up in reaction to keypresses anymore.

And yes, the hcitool output shows the connection to the keyboard.

Sorry I don't have better answers for you. Did you try deleting the device from the Bluetooth manager or directly from /var/lib/bluetooth and pair again?

---

### Post by alfonso78 on 2008-11-04
> **guardian_de said:**
> Hi Alfonso,

just a quick answer since I'm in a hurry: The flash indicator only blinks after the keyboard has been switched on. When the handshake is finished it doesn't light up in reaction to keypresses anymore.

And yes, the hcitool output shows the connection to the keyboard.

Sorry I don't have better answers for you. Did you try deleting the device from the Bluetooth manager or directly from /var/lib/bluetooth and pair again?

Hi guardian,

I tried several time to remove the whole folder /var/lib/bluetooth without success.

Not really sure what else to do.

thank you,

alfonso

---

### Post by guardian_de on 2008-11-05
Hi,

can you please post the contents from the device directory under /var/lib/bluetooth?

---

### Post by alfonso78 on 2008-11-05
> **guardian_de said:**
> Hi,

can you please post the contents from the device directory under /var/lib/bluetooth?

Hi,

here you go.

Thank you,

```

voyage:/var/lib/bluetooth# for i in /var/lib/bluetooth/00\:1B\:DC\:0F\:74\:09/* ; do echo ; echo $i ; echo ; strings $i ; done

/var/lib/bluetooth/00:1B:DC:0F:74:09/classes

00:1E:37:FC:F7:99 0x1c010c
00:18:00:00:78:86 0x002540
00:12:D2:6F:7C:37 0x50020c

/var/lib/bluetooth/00:1B:DC:0F:74:09/did

00:18:00:00:78:86 0002 0DC6 3752 0100

/var/lib/bluetooth/00:1B:DC:0F:74:09/features

00:18:00:00:78:86 FFFF8FFE9BF90080

/var/lib/bluetooth/00:1B:DC:0F:74:09/lastseen

00:1E:37:FC:F7:99 2008-11-04 19:42:08 GMT
00:18:00:00:78:86 2008-11-04 19:42:06 GMT
00:12:D2:6F:7C:37 2008-11-04 19:42:04 GMT

/var/lib/bluetooth/00:1B:DC:0F:74:09/lastused

00:18:00:00:78:86 2008-11-04 19:42:23 GMT

/var/lib/bluetooth/00:1B:DC:0F:74:09/linkkeys

00:18:00:00:78:86 A72CF309308CEF56DC3C58C243F23EA4 0 6

/var/lib/bluetooth/00:1B:DC:0F:74:09/manufacturers

00:18:00:00:78:86 10 3 65440

/var/lib/bluetooth/00:1B:DC:0F:74:09/names

00:12:D2:6F:7C:37 NOKIAN80
00:18:00:00:78:86 BTKB-7886
00:1E:37:FC:F7:99 LAPTOP

/var/lib/bluetooth/00:1B:DC:0F:74:09/profiles

00:18:00:00:78:86 00001124-0000-1000-8000-00805f9b34fb 00001200-0000-1000-8000-00805f9b34fb

/var/lib/bluetooth/00:1B:DC:0F:74:09/sdp

00:18:00:00:78:86#00010001 35770900000A000100010900013503191200090004350D35061901000900013503190001090006350909656E09006A090100090009350835061912000901000901012512426C7565746F6F7468204B6579626F617264090200090100090201090DC60902020937520902030901000902042801090205090002
00:18:00:00:78:86#00010000 3601C10900000A000100000900013503191124090004350D35061901000900113503190011090006350909656E09006A0901000900093508350619112409010009000D350F350D350619010009001335031900110901002512426C7565746F6F7468204B6579626F6172640901012512426C7565746F6F7468204B6579626F617264090102250450535443090200090110090201090100090202084009020308210902042801090205280109020635E235E0082225DC05010906A1010507850119E029E715002501750195088102950175088101950575010508850119012905910295017503910395067508150025E70507190029E7810005060920150025FF750895018547B122050685FF9501750209240926810275068101C0050C0901A1018503050C150025010A23020A8A010A21020A24020A25020A26020A27020A2A0209B509B609B709CD09E209E909EA7501950F8102750195018101C005010902A1010901A10085020509190129031500250195037501810295017505810305010930093109381581257F750895038106C0C0090207350835060904090901000902082800090209280109020A280109020B09010009020C091F4009020D280009020E2801
voyage:/var/lib/bluetooth#

```

---

### Post by guardian_de on 2008-11-06
Hi Alfonso,

I hoped to spot some significant differences, but other than that your device type is different (BTKB-7886) I cannot see any. But wait... you are missing the config file. Maybe that is related to your problems.

Sorry that I cant help you better (and cant access the apostrophe on my German keyboard with American mapping ;))

```
/var/lib/bluetooth/00:16:CB:10:0C:4F/classes

00:18:00:00:66:89 0x002540

/var/lib/bluetooth/00:16:CB:10:0C:4F/config

class 0x0a0104
onmode connectable
mode connectable

/var/lib/bluetooth/00:16:CB:10:0C:4F/did

00:18:00:00:66:89 0002 0DC6 3752 0100

/var/lib/bluetooth/00:16:CB:10:0C:4F/features

00:18:00:00:66:89 FFFF8FFE9BF90080

/var/lib/bluetooth/00:16:CB:10:0C:4F/lastseen

00:18:00:00:66:89 2008-11-01 13:15:58 GMT

/var/lib/bluetooth/00:16:CB:10:0C:4F/lastused

00:18:00:00:66:89 2008-11-06 16:54:10 GMT

/var/lib/bluetooth/00:16:CB:10:0C:4F/linkkeys

00:18:00:00:66:89 805139F7841FBE9F9E1B593C8797248E 0 4

/var/lib/bluetooth/00:16:CB:10:0C:4F/manufacturers

00:18:00:00:66:89 10 3 65440

/var/lib/bluetooth/00:16:CB:10:0C:4F/names

00:18:00:00:66:89 BTKB-6689

/var/lib/bluetooth/00:16:CB:10:0C:4F/profiles

00:18:00:00:66:89 00001124-0000-1000-8000-00805f9b34fb 00001200-0000-1000-8000-00805f9b34fb

/var/lib/bluetooth/00:16:CB:10:0C:4F/sdp

00:18:00:00:66:89#00010001 35770900000A000100010900013503191200090004350D35061901000900013503190001090006350909656E09006A090100090009350835061912000901000901012512426C7565746F6F7468204B6579626F617264090200090100090201090DC60902020937520902030901000902042801090205090002
00:18:00:00:66:89#00010000 3601C10900000A000100000900013503191124090004350D35061901000900113503190011090006350909656E09006A0901000900093508350619112409010009000D350F350D350619010009001335031900110901002512426C7565746F6F7468204B6579626F6172640901012512426C7565746F6F7468204B6579626F617264090102250450535443090200090110090201090100090202084009020308210902042801090205280109020635E235E0082225DC05010906A1010507850119E029E715002501750195088102950175088101950575010508850119012905910295017503910395067508150025E70507190029E7810005060920150025FF750895018547B122050685FF9501750209240926810275068101C0050C0901A1018503050C150025010A23020A8A010A21020A24020A25020A26020A27020A2A0209B509B609B709CD09E209E909EA7501950F8102750195018101C005010902A1010901A10085020509190129031500250195037501810295017505810305010930093109381581257F750895038106C0C0090207350835060904090901000902082800090209280109020A280109020B09010009020C091F4009020D280009020E2801

/var/lib/bluetooth/00:16:CB:10:0C:4F/trusts

00:18:00:00:66:89 [all]

```

---

### Post by dynnamitt on 2009-02-13
Any luck lately guys ? ? ?

I'm also the UNLUCKY owner of a keysonic 340BT ...

Worked like a dream ONCE .. and then never again (ubuntu8.10)

? ? ?

---

### Post by iosonogio on 2011-09-18
Hi , same here !

I own a 340-BT which used to work like a charm. Then after not using it for some months, it stopped working... no apparent reason!

I tried re-pairing, no success.

I tried pairing on a Windows 7 bluetooth notebook, no success!

When I type the pass key (1234 or any random) and press ENTER, nothing actually happens, the pairing led keeps on flashing... and it wont pair in the end!

Any help?

---

