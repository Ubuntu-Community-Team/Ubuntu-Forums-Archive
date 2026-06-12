---
title: "laptop touchpad"
date: 2005-08-24
forum: Hardware &amp; Laptops
---

### Post by Nopposan on 2005-08-24
I'd like to get the touchpad of my Compaq Presario 705 working fully; the centrally located directional scroll button behaves as though it's the right-click button.

How do I begin to try and fix this?  Or should I just tolerate it?  It's not critical.

---

### Post by locutus42 on 2005-08-25
[QUOTE=Nopposan]I'd like to get the touchpad of my Compaq Presario 705 working fully; the centrally located directional scroll button behaves as though it's the right-click button.

How do I begin to try and fix this?  Or should I just tolerate it?  It's not critical.[/QUOTE]

first thing to do is to find out what make/model of touchpad it is. For instance, the Compaq R4000 uses a Synaptics Touchpad. I searched the web for info on this and added options based on what others posted as various parameters.

BTW, IIRC the touchpad worked fine with the Ubuntu LiveCD but after installation, it didn't. So, I booted off the LiveCD, copied the section from the /etc/X11/xorg.conf for the touchpad onto a USB drive, and then booted back to the installed system and pasted that into the xorg.conf file.... It gave me a starting point.

---

### Post by Nopposan on 2005-08-25
How do I find out what touchpad the Presario 705.  Maybe I should just Google it?  Isn't there a way to check up on it in the device manager or systems management?  I was looking through the device manager and I don't see anything called "touchpad."  That doesn't mean it's not there though -- 'could be called gobblediegook XYZ for all I know.

---

### Post by fredricsolstad on 2005-08-28
[QUOTE=Nopposan]How do I find out what touchpad the Presario 705.  Maybe I should just Google it?  Isn't there a way to check up on it in the device manager or systems management?  I was looking through the device manager and I don't see anything called "touchpad."  That doesn't mean it's not there though -- 'could be called gobblediegook XYZ for all I know.[/QUOTE]

Hi, I did some googeling and found that the touchpad itself is a synaptics PS/2 touchpad, so for the touchpad itself you can use the standard driver. For the small scroll-thingie though I'm not sure. 

Hope that this is to some help on your quest

Cheers!

---

### Post by nic2 on 2005-08-28
[https://wiki.ubuntu.com/SynapticsTouchpadHowto?highlight=%28synaptics%29%7C%28touchpad%29](https://wiki.ubuntu.com/SynapticsTouchpadHowto?highlight=%28synaptics%29%7C%28touchpad%29)

---

### Post by Nopposan on 2005-08-30
Thanks, Nic2.  However, I'm not sure this is helpful; not yet anyhow. The link you sent me to gives these instructions:

"The Synaptics Touchpad driver is already installed in Warty, but it seems it's not activated.

To actually use the Synaptics driver, you have to edit the XF86config-4 file located in /etc/X11/"

I don't seem to have any such file in the /etc/X11 folder.  I do have a file called "Xwrapperconfig.exe."  'Close as I can get.

'Totally clueless over here.

---

### Post by Nopposan on 2005-08-30
'Could be nic2 and I are using different kernels.  I've got an AMD Duron processor.  When I go to /etc/X11 I find that there's a folder called "xorg.conf"  I think that's my counter part to the "XF86config-4"

Here's something interesting; I don't find anything for a synaptics touchpad, but I find this:

"Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection"

How about that?  What do you think is going on here?

---

### Post by nic2 on 2005-09-01
[Assuming that the Synaptics TouchPad driver for X.Org server is installed]

In the xorg.conf file you have to set some options, follow the steps below to set these options:

Open Terminal and type:

	[COLOR=Blue]sudo gedit /etc/X11/xorg.conf[/COLOR]

The xorg.conf file will open.  Scroll down to the following section: 

[COLOR=Blue]Section "InputDevice"
        Identifier                "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option		"HorizScrollDelta"	"0"
EndSection
[/COLOR]
Now add the following to this section:
[COLOR=Blue]
	Option     	"TapButton1"     	"1"
	Option     	"TapButton2"     	"1"
	Option     	"TapButton3"     	"1"
[/COLOR]
Save the document, exit the Terminal and reboot.

---

### Post by Nopposan on 2005-09-01
O.K.  Thanks again Nic2;  I checked on whether the synaptics driver was installed, and  according to the package manager it is.  However, as I mentioned earlier, there is no module or identifier for "synaptics touchpad" in the xorg.conf file.  What I decided to try is substituting the code you recommended for the mouse stuff that I mentioned; we don't have a mouse and the touchpad is functioning so it must be that Ubuntu "thinks" the touchpad is a mouse.

I'm going to reboot now.  If you don't hear back from me then I've done something horribly wrong to this poor little laptop.

-- Jonathon

---

### Post by Nopposan on 2005-09-02
Hello!  Boy oh boy oh boy.  I made a mess of things, Nic2.  But I'm back.

What I did was add the Load "Synaptics Touchpad" line here.
Section "Module"
	Load	"Synaptics Touchpad"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"type1"
	Load	"vbe"
EndSection

Then I substituted this for the mouse stuff (see previous post for the mouse stuff).
Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents" "true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
	Option		"TapButton1"		"1"
	Option		"TapButton2"		"1"
	Option		"TapButton3"		"1"
EndSection

It did not work at all.  The X window system wouldn't start on reboot and I had a scare.  Luckily, I discovered with the help of my Linux fanatic friend that Linux is usually preconfigured to automatically save a copy of the original system file whenever it's been edited.  This rescue copy had a "~" suffix.  My friend didn't tell me what the rescue copy would look like, but I took a chance and typed
# cp xorg.conf~ xorg.conf
# reboot

And voilla, I'm writing back to you.  'Still don't know how to implement the synaptics touchpad driver, but whew!

I suppose there might be something with adding modules?  Maybe just adding that first line to the xorg.conf wasn't enough?  'Sorry, still very new at all this.  I should probably read the HowTo Ubuntu on the Wiki or something, but the X window system and the package management makes most things so easy that it's easy to put off the digin-get-your-hands-dirty stuff.  Still, I definitely feel good that I fixed the problem I caused.

Here's a big "THANK YOU" to whomever set things up with that automatic rescue copy trick!

---

### Post by nic2 on 2005-09-03
Try editing the following entry in the xorg.conf file:  

Option           "Emulate3Buttons"	         "no"

Ps. I did a google search and it would appear that the centrally located directional scroll button does not function properly under Linux.

---

