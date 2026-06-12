---
title: "Trouble with tablet"
date: 2007-03-19
forum: Hardware &amp; Laptops
---

### Post by D.C. on 2007-03-19
Hi

I have 6.10 Edgy on a tc1100 tablet pc, 2.6.17.11 kernel.

I followed the instructions on this page to get the tablet working:
[https://help.ubuntu.com/community/Wacom](https://help.ubuntu.com/community/Wacom)
code:
sudo apt-get install xserver-xorg-input-wacom wacom-tools
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
sudo gedit /etc/X11/xorg.conf

and changed all /dev/wacom occurences into /dev/input/wacom.

The instant I clicked "Save" on gedit, the tablet's stylus started working, perfectly, cursor, click, everything. I figured I should restart X (sudo /etc/init.d/gdm restart) to see if everything was alright... and it wasn't, the stylus stopped working.

For some reason, /dev/input/wacom disappeared. I've tried removing and re-installing xserver-xorg-input-wacom and wacom-tools, but no success. I also updated the /usr/bin/dexconf script.

Since /dev/input/wacom doesn't exist anymore, my Xorg.0.log shows (obviously hehe):
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
        No such file or directory.
Error opening /dev/input/wacom : No such file or directory
(6 times)

What happened? What can I do to get my stylus to work again?
Thanks in advance

---

### Post by MontanaMax on 2007-03-19
I have a tc1100 with Kubuntu edgy, but haven't tried turning on the stylus yet. I've been reading about this for a while however, and I think the info in here might help you find which input device the tablet is mapping to currently.

[http://wiki.linuxquestions.org/wiki/Tc1100](http://wiki.linuxquestions.org/wiki/Tc1100)

[https://help.ubuntu.com/community/WacomTroubleshooting](https://help.ubuntu.com/community/WacomTroubleshooting)

[http://math.bu.edu/people/kayeats/computers/tc1100.html](http://math.bu.edu/people/kayeats/computers/tc1100.html)

Now that I'm taking a couple weeks off from school I'm going to do a good backup and take a crack and making this work myself. If I find any magic tricks I'll be sure to let you know.

Good luck,

---

### Post by MontanaMax on 2007-03-19
OK - I got this to work with a couple changes from the normal wacom instructions.

All of my tablet 'InputDevice" sections of my xorg.conf file point to the path "/dev/wacom" - not "/dev/input/wacom"

From what I can see, the extra input path is only for USB wacom tablets, and the TC1100 doesn't use a USB interface to get to the stylus.

I also have the following option at the bottom of each of the tablet  InputDevice sections

Option        "ForceDevice"   "ISDV4"

Then I had to activate the stylus at a firmware level by running the following command:

```
echo "1" > /dev/wacom
```

Then a <ctrl-atl-backspace> to restart X and everything was working just fine.

Let me know if this works for you and then I'll write it up for the wiki.

Below are the full wacom input device sections from my config:

```
Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection


```

---

### Post by MontanaMax on 2007-03-19
Now I'm getting really excited - the screen rotation works great too!! Just follow the instructions here (AFTER the NVIDIA proprietary drivers are installed) ...

[http://wiki.linuxquestions.org/wiki/Tc1100](http://wiki.linuxquestions.org/wiki/Tc1100)

...without worrying about the kernel patch - Kubuntu 6.10 is already patched for this and ready to go once Wacom is installed.

Once I threw the commands to rotate the screen and wacom perspective into a pair of shell scripts, the screen rotates back and forth like a dream!

---

### Post by Mr.Clark on 2007-04-19
> **MontanaMax said:**
> Now I'm getting really excited - the screen rotation works great too!! Just follow the instructions here (AFTER the NVIDIA proprietary drivers are installed) ...

[http://wiki.linuxquestions.org/wiki/Tc1100](http://wiki.linuxquestions.org/wiki/Tc1100)

...without worrying about the kernel patch - Kubuntu 6.10 is already patched for this and ready to go once Wacom is installed.

Once I threw the commands to rotate the screen and wacom perspective into a pair of shell scripts, the screen rotates back and forth like a dream!

This is brilliant!

I've got Ubuntu 7.04 installed on my TC1100 and (very nearly almost) everything is working brilliantly! (Vista just crapped out and whined, but Fawn is amazing, especially with Beryl!)

My niggle here is this:

I've got the script for rotating the screen and switching it back, that works (although it does pop up a box asking for permission to run every time... it's a .sh file... any way around this?), but what would really make this better is for it to detect when I've moved the screen and run those scripts silently when I do... is there any way to pull this off?

---

### Post by MontanaMax on 2007-04-21
I'm sure there is - somehow - because in Window$ it does receive a signal from the hardware when the keyboard rotates from the screen. 

However I'm not skilled enough in the realm of hardware interrupts or whatever they call that black magic to figure out how to trap for that condition and trigger something on it.

Perhaps if we all pooled together and bought one of these tablets for somebody in the FOSS community who could look into this... I know I'd pitch in 50 bucks to get someone who has that skill set focused on making this thing sing and dance even better with Ubuntu.

---

### Post by jharbert on 2007-04-22
Check this [howto]("http://ubuntuforums.org/showthread.php?t=371510") out.  The script handles automatic rotation.

---

### Post by ishtob on 2007-05-29
I cant figure out what i am doing wrong, i cant get teh right click to work.

i installed feisty on my tc1100 and supposably i had to modify a file named dexconf instead of xorg.conf but either one made any diffrence, the pen's right click button still remains functionless.

and have anyone figured out a way to activate that internet card without having to compile a new kernel?

---

### Post by MontanaMax on 2007-06-04
The wireless card and pen clicks worked by default for me with Kubuntu 7.04 - no special configurations at all. I was pretty impressed as I could never get the right click to work in Windoze at all.

---

