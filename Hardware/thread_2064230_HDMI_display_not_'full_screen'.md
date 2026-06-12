---
title: "HDMI display not 'full screen'"
date: 2012-09-28
forum: Hardware
---

### Post by tornadof3 on 2012-09-28
Hello

So I just installed Xubuntu 12.04 on an Acer Revo70 nettop box to use as new computer. It is outputing via HDMI to a nice 24 inch monitor; the picture is nice but alas there is a 1 inch (ish) border around the display that is not being used. The picture that is displayed is perfect.

I installed the ATI drivers via the 'additional drivers' menu, which is when this first happened. with the standard drivers it was full screen correctly; alas I do not know what to do. Any advice?

Thanks

---

### Post by tornadof3 on 2012-09-30
For anyone else who has this problem, here is an easy solution:

launch the ATI Catalyst Control Config program (in the settings menu or aticonfig from command prompt) and:

Display Manager -> [select your screen] -> "Adjustments" tab -> set 'scaling options' overscan to 0%

---

### Post by effyeah on 2012-10-29
> **tornadof3 said:**
> For anyone else who has this problem, here is an easy solution:

launch the ATI Catalyst Control Config program (in the settings menu or aticonfig from command prompt) and:

Display Manager -> [select your screen] -> "Adjustments" tab -> set 'scaling options' overscan to 0%

Hello,

I have this exact same issue! Except for me, under the CCC, there is no Adjustments Tab. I'm using the latest version of fglrx. It is an HTPC that runs xbmc-standalone (no separate desktop environment.   To get to CCC, I use xfce, but again, there is no adjustments tab. I've tried dozens of command line options to try to fix this using ati/amdconfig, to no avail. Finally I found a script online that fixes the issue temporarily from within an X session. I added the script as a bash script to xmbc's program launcher and it fills the screen every time I run it: 

```
#!/bin/bash
#
# Suggest you put this script into you home directory, eg 
# mkdir -p ~/bin
# gedit ~/bin/atiscan
# copy paste this in
# chmod +x ~/bin/atiscan


# CONFIG STUFF YOU WILL EDIT
# You can let the script query you for this stuff, though once you have run it once, 
# suggest you edit the script and hard code the settings
DISPLAY_TYPE='dfp1'
WIDTH=1920	
HEIGHT=1080

# SCRIPT STARTS

if [ "" == "$WIDTH" ]
then
	echo "please enter your display width (eg 1280, 1920 etc)"
	read WIDTH
fi
if [ "" == "$WIDTH" ] 
then
	echo "empty widt, dying"
	exit 1
fi
if [ "" == "$HEIGHT" ]
then
	echo "please enter your display width (eg 1280, 1920 etc)"
	read HEIGHT
fi
if [ "" == "$HEIGHT" ] 
then
	echo "empty height, dying"
	exit 1
fi

# DISPLAY TYPE
if [ "" == "$DISPLAY_TYPE" ] 
then
	echo "First we need to check which type of display it is"
	types="crt1 lvds tv cv tmds1 crt2 tmds2 tmds2i dfp1 dfp2 dfp3 dfp4 dfp5 dfp6"
	for t in $types
	do
		aticonfig --query-dispattrib=$t,positionX  
	done
	echo"

	The one that didnt error is the right one

	If you are running more than one monitor/display then take your pick!

	"
	echo "Please enter the one you want to set to $WIDTH x $HEIGHT"
	read DISPLAY_TYPE	
fi


if [ "" == "$DISPLAY_TYPE" ] 
then
	echo "empty display type, dying"
	exit 1
fi


#POSITION
aticonfig --set-dispattrib=$DISPLAY_TYPE,positionX:0
aticonfig --set-dispattrib=$DISPLAY_TYPE,positionY:0
aticonfig --set-dispattrib=$DISPLAY_TYPE,sizeX:$WIDTH
aticonfig --set-dispattrib=$DISPLAY_TYPE,sizeY:$HEIGHT
```

Unfortunately, every time I turn off the projector or let the surround sound go to sleep (it's also an HDMI switch), it reverts to the underscanned image. WHY THE HELL IS OVERSCAN COMPENSATION ENABLED BY DEFAULT! WHO'S BRIGHT IDEA WAS THAT? lol.

Anyway, I can post any information that is relevent if it is helpful, just let me know what is needed...
Thanks in advance!

---

### Post by zippoxer on 2012-11-26
> **effyeah said:**
> Hello,

I have this exact same issue! Except for me, under the CCC, there is no Adjustments Tab. I'm using the latest version of fglrx. It is an HTPC that runs xbmc-standalone (no separate desktop environment.   To get to CCC, I use xfce, but again, there is no adjustments tab. I've tried dozens of command line options to try to fix this using ati/amdconfig, to no avail. Finally I found a script online that fixes the issue temporarily from within an X session. I added the script as a bash script to xmbc's program launcher and it fills the screen every time I run it: 

```
#!/bin/bash
#
# Suggest you put this script into you home directory, eg 
# mkdir -p ~/bin
# gedit ~/bin/atiscan
# copy paste this in
# chmod +x ~/bin/atiscan


# CONFIG STUFF YOU WILL EDIT
# You can let the script query you for this stuff, though once you have run it once, 
# suggest you edit the script and hard code the settings
DISPLAY_TYPE='dfp1'
WIDTH=1920	
HEIGHT=1080

# SCRIPT STARTS

if [ "" == "$WIDTH" ]
then
	echo "please enter your display width (eg 1280, 1920 etc)"
	read WIDTH
fi
if [ "" == "$WIDTH" ] 
then
	echo "empty widt, dying"
	exit 1
fi
if [ "" == "$HEIGHT" ]
then
	echo "please enter your display width (eg 1280, 1920 etc)"
	read HEIGHT
fi
if [ "" == "$HEIGHT" ] 
then
	echo "empty height, dying"
	exit 1
fi

# DISPLAY TYPE
if [ "" == "$DISPLAY_TYPE" ] 
then
	echo "First we need to check which type of display it is"
	types="crt1 lvds tv cv tmds1 crt2 tmds2 tmds2i dfp1 dfp2 dfp3 dfp4 dfp5 dfp6"
	for t in $types
	do
		aticonfig --query-dispattrib=$t,positionX  
	done
	echo"

	The one that didnt error is the right one

	If you are running more than one monitor/display then take your pick!

	"
	echo "Please enter the one you want to set to $WIDTH x $HEIGHT"
	read DISPLAY_TYPE	
fi


if [ "" == "$DISPLAY_TYPE" ] 
then
	echo "empty display type, dying"
	exit 1
fi


#POSITION
aticonfig --set-dispattrib=$DISPLAY_TYPE,positionX:0
aticonfig --set-dispattrib=$DISPLAY_TYPE,positionY:0
aticonfig --set-dispattrib=$DISPLAY_TYPE,sizeX:$WIDTH
aticonfig --set-dispattrib=$DISPLAY_TYPE,sizeY:$HEIGHT
```

Unfortunately, every time I turn off the projector or let the surround sound go to sleep (it's also an HDMI switch), it reverts to the underscanned image. WHY THE HELL IS OVERSCAN COMPENSATION ENABLED BY DEFAULT! WHO'S BRIGHT IDEA WAS THAT? lol.

Anyway, I can post any information that is relevent if it is helpful, just let me know what is needed...
Thanks in advance!

Exactly what I ask myself. Why enable something by default when 99.9% of the users will disable it anyway??

Thanks for the solution!

---

### Post by effyeah on 2012-11-26
Well, I upgraded to Ubuntu 12.10, and now my Radeon HD 4290 that's onboard in my motherboard doesn't work with xorg 1.13 since they've dropped support for <=5000 series GPUs in the main fglrx package.

So frustrating... I guess this is no longer an issue for me anyways

---

