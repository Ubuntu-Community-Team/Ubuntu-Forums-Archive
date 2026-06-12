---
title: "Samsung R20"
date: 2008-05-17
forum: Hardware
---

### Post by GuitarMatt on 2008-05-17
Hi

Ok, i`m looking for a little help, i`m pretty new to Linux and i`ve tried everything to run / install Ubunto on a Samgung R20 laptop. 

I power up the machine with the CD in the drive and select my language. I`m presented with the setup options menu where i have tried to run fro the CD in both normal and "graphics Safe Mode" but always with the same result.

It spends a little time loading things from the CD with and seems to be going fine, then the loading bar completes and the following information flashes up:

*Starting deferred ececution scheduler atd                  [ok]
*Starting periodic command scheduler crond                  [ok]
*checking battery state...                                  [ok]
*Running local boot scripts (/etc/rc.local)                 [ok]

This text flashes 3 time and then... nothing...

I am able to type at this point but it seems to respond to nothing. bizzarly the power button still shuts the laptop down but past that i cant get it to do anything.

I have tried both the amd64 and i386 cd`s and they both produce the same result (I have an Intel core 2 Duo incase anyone can help me on this too.

Basicly i really want to get Ubuntu install but i`m having a nightmare

Any help is appreciated

Matt

---

### Post by GuitarMatt on 2008-05-18
I`ve still had no response on this, can someone please help me, i`ve been tryin to get this working for days and I just dont know where i`m going wrong!

---

### Post by Nikos.Alexandris on 2008-06-07
Matt,

sorry for giving a reply so late.

All you need is to install the ATI (graphic card) driver first and then you will be able to login to the graphical environment (which is Gnome by default).

Briefly the steps (please search the net for more details on how to mount a device for example).

1. Get the latest driver from [https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8-5-x86.x86_64.run](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8-5-x86.x86_64.run) and save it to a flash stick

(or maybe the previous one which is 8.4 if you want to taste 3D effects -- with 8.5 I can't get the 3D's working currently).

2. Try to boot with your Live-CD (prefer 64 for more performance, though you will have other problems with Java apps)

3. mount your usb flash-stick

4. run the ati-installer (the one downloaded) - you might need to be root

5. If you installation ends with no errors juts type "startx" and you should be able to login.


Cheers,

Nikos

---

### Post by GuitarMatt on 2008-06-07
Hi Nikos

Thanks for your reply, Ok... so i installed Ubuntu to my hard drive which i letting me boot in recovery mode. my knoledge of linux commands is very small. I moved the driver you suggested over to my linux partition using fs-driver ([http://www.fs-driver.org/](http://www.fs-driver.org/)) but i still cant get it to run. i`m trying: sudo exec /path/filename.run 
It tells me sudo exec isn`t a valid command (or something like that) as i`m already logged inm as root i tried without sudo and its saying the file doesnt exist (which again i know isn`t true because dir shows the file)

please excuse my ignorance, is there something i`m doing wroing??

---

### Post by Nikos.Alexandris on 2008-06-07
Matt,

no worries. Take it step-by-step:

If you already logged-in in your linux system and you copied the driver in your linux partition then you have to navigate to the directory wherever you have put this file  with:

cd /wherever/you/have/saved

and run it as follows:

sudo sh ./ati-driver-installer-8-5-x86.x86_64.run

That should install the driver (of course you need to hit a couple of times the "Yes" or similar button). Then just:

startx

or try rebooting (normally, not in recovery mode) and you should be set to go.

---

### Post by GuitarMatt on 2008-06-07
ok... the driver seemed to install properly but after typing startx i just got a blank screen. i restarted and tried to boot normally and again i got a blank screen. feel like i`m so close but its just not happening. is there anything else i can try?

thaks again for your help

---

### Post by Nikos.Alexandris on 2008-06-07
Matt,

you are ALMOST there. Just follow the steps in section "Finishing the Install: Configuration" at [http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide#Specific_Issues](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide#Specific_Issues)

In case it doesn't work again try "sudo dpkg-reconfigure xserver-xorg"

Good Luck ;-)

---

### Post by GuitarMatt on 2008-06-07
Really sorry to keep bothering you! Your the only person to have replied and I`m never going to work this out on my own.

i followed the wiki and edited the xorg.conf file:

Section "Device"
	[...]
	Driver		"fglrx"
	[...]
EndSection

i`m assuming (from the error i got saying the line is missing an "Identifier") the [...] are meant to be replaced with driver / hardware specifics. any idea exactly what i should be putting in this section

i also tried the command u gave me (sudo dpkg-reconfigure xserver-xorg) which told me there are no dectable screens. i`m guessing this is to do with the missing identifier in xorg.conf but again i`m probably wrong.

---

### Post by Nikos.Alexandris on 2008-06-07
Matt,

no need for sorriez. If I count the times I say Sorry in various mailing lists... ;-) Common, this is why the forum is for. And if I can help you we are fine - it's my pleasure. If not, then I'll have to learn more!

So,

all you need is to configure the xorg.conf file.


1. the "[...]" should not be on you xorg.conf -- Edit again the file and remove those. 

This section should look like (maybe the "PCI" bla bla line can/should be different):

Section "Device"
	Identifier  "aticonfig-Device[1]"
	Driver      "fglrx"
	BusID       "PCI:1:5:0"
	Screen      1
EndSection

2. Did you try the command "sudo aticonfig --initial -f" ?

---

### Post by Nikos.Alexandris on 2008-06-07
Maybe this is effective:

sudo dpkg-reconfigure -phigh linux-restricted-modules-`uname -r`

BTW, the place where I get most useful information is:
[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

If you are connected in the internet (another command line task!) you could try to get the driver which is in the Ubuntu repositories (different than the proprietary driver 8.5). Steps described in the above mentioned web-page.

I am sure that finally you'll get it work, since we own the same machine.

Another web-page is in Ubuntu's documentation pages:
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

I know it is hard in the beginning but its a process from which you'll learn a lot.

---

### Post by GuitarMatt on 2008-06-07
I`ve read through ttp://wiki.cchtml.com/index.php/Ubu...allation_Guide and a few other wikis on the subject and they seem to miss things out that to the layman make it near impossible. 

installing the linux restricted drives module was the first thing i tried but i`ve been unable to get an internet connection from the command line(from efnet and wireless) again because of my poor knowledge of linux.

I tried changing xorg.conf to read:

Section "Device"
Identifier "aticonfig-Device[1]"
Driver "fglrx"
BusID "PCI:1:5:0"
Screen 1
EndSection

and when i typed startx it came back with 

fatel server error:
Caught Signal 11. Server Aborting

I also noticed some information at the top, i cant remember exactly what it said but it was to do with the PCI:1:5:0 I didn`t know what to put in place of this so i removed the line alltogether but the result (fatel server error) was the same

Any more ideas??

---

### Post by Nikos.Alexandris on 2008-06-07
Post the results of

1. lspci

2. cat /etc/X11/xorg.xonf


or/and try again the same like before from the start:

1. Boot in recovery mode.

2. Install the ati driver

3. sudo dpkg-reconfigure xserver-xorg

Here you probably need to select "fglrx" as far as I remember.

4. startx

[It is "interesting" that you mentioned (after step 3) the message "no detectable screens". Normally this shouldn't be a problem.]

---

### Post by GuitarMatt on 2008-06-07
Ok... lots to type up...

lspci brings up a whole page of information so i`m just going to show you what i think are the important bits

00.00.0 Host Bridge: ATI Tech Inc Unknown Device 7930
00.01.0 Host PCI: ATI Tech Inc Unknown Device 7932
00.05.0 Host PCI: ATI Tech Inc Unknown Device 7935
00.06.0 Host PCI: ATI Tech Inc Unknown Device 7936
00.07.0 Host PCI: ATI Tech Inc Unknown Device 7937
00.12.0 SATA Controller: ATI Tech Inc SB600 Non-Raid-5 SATA
(some lines missing - i think these are all usb related)
00.14.0 SMBus: ATI Tech Inc SBx00 SMBus Controller
01.05.0 VGA Compatible Controller: ATI Tech Inc Radeon Xpress 1250

The last line looks promising right?? thats my graphics card

Tried installing the driver again and using sudo dpkg-reconfigure xserver-xorg but again when i did startx it just came back no screen detected. this also seemed to undo all the changed i made to xorg.conf bit annoying but i had a backup. 

the cat /etc/X11/xorg.conf command just reads out whats in the xorg.conf file (which is how i noticed the changes had been over written)

Dont know if any of this is usefull if theres anythi ng else u want me to look up let me know

---

### Post by Nikos.Alexandris on 2008-06-07
> **GuitarMatt said:**
> Ok... lots to type up...
[...]
01.05.0 VGA Compatible Controller: ATI Tech Inc Radeon Xpress 1250

The last line looks promising right?? thats my graphics card
[...]
the cat /etc/X11/xorg.conf command just reads out whats in the xorg.conf file (which is how i noticed the changes had been over written)
[...]


So the last line of "lspci" is ok.

1. Try the "sudo aticonfig --initial" before startx

2. Post the whole xorg.conf # don't worry, its not dangerous or so.

---

### Post by Nikos.Alexandris on 2008-06-07
For example, my xorg.conf (the "interesting lines") are:

```
Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option      "TexturedVideo"
	Option		"DRI"			"true"
#	Option		"GARTSize" "64"
	Option		"ColorTiling"		"on"
	Option		"EnablePageFlip"	"true"
	Option		"AccelMethod" 		"EXA"
	Option		"XAANoOffscreenPixmaps"
	Option      "UseFastTLS"		"2"
	BusID       "PCI:1:5:0"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection
```

---

### Post by GuitarMatt on 2008-06-07
heres the xorg fil, i`ll try the --initial command now and let u know how it goes.

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
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
EndSection

---

### Post by Nikos.Alexandris on 2008-06-07
Silly idea or maybe not (since we have the same laptop): copy paste or adjust your xorg.cong to look like mine (at least the last sections about the device, monitor and screen)!

---

### Post by GuitarMatt on 2008-06-07
thats exactly what i was doin when u said that lol

---

### Post by rmls on 2008-09-04
Hi Guys

Just a quick note of thanks to both you guys, I was trying to install Hardy on a R20 using Wubi (I'm a newbie) last night and having the same ATI issue. Found your posts and followed the instructions and as of 15 mins ago I have a shiny working (appears to be fully!) Wubi based Hardy install. 

Gheers guys.

---

### Post by jamie-e89 on 2008-09-08
hi there people,, i have a samsung r40 and experiencing the same probs, was wondering if this would work for me?,,
thanks jamie

---

### Post by jason.eb on 2009-02-15
Hi Recently did a fresh install of ubuntu 8.10 interpid ibex on relatives
samsung r20 laptop worked without a hitch. hope this helps.

---

