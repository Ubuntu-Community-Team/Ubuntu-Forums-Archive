---
title: "ubuntu not liking optical mouse or what"
date: 2005-12-07
forum: Installation &amp; Upgrades
---

### Post by ernie on 2005-12-07
i just got the live cd and tried too run it on my pc. once it loaded i realized that the mouse was not working at all it is an optical mouse the laser was not even on does ubuntu have a problem with them or something 
 is there a way to fix this still using the live cd

---

### Post by matthewstory on 2005-12-07
What's the make of the mouse? Is it USB or PS2?  Answering these questions would help.  If you could also post your attached devices section of your xorg.conf file here that would also help:

sudo gedit /etc/X11/xorg.conf

regards,
matt

---

### Post by ernie on 2005-12-07
it is a ps2 and it is made by micro innovations

---

### Post by ernie on 2005-12-08
i would post that xorg thing but i do not know how to also not being able to use a mouse dosent help so show me how to and also will i be able to find this file if i only use the live cd

---

### Post by Steve Hawkins on 2006-01-02
I have the same kind of optical mouse. It works on 2 other computers, one running SuSE 9.3 and one running W98. dmesg shows that ubuntu thinks I have a ps2 mouse. As far as I know this Micro Innovations optical mouse is built to look like a wheeled PS2 mouse. I have a removable HD on this computer. I can remove it and slide one in that has W98 on it and this mouse works fine. The laser light on the mouse goes out at exactly the same point in the boot sequence every time. Just before ubuntu sets the clock. :confused:

From /etc/X11/xorg.conf

Section "InputDevice"
            Identifier    "Configured Mouse"
            Driver        "mouse"
            Option        "CorePointer"
            Option        "Device"
            Option        "Protocol"       "ImPS/2"
            Option        "Emulate3Buttons"    "true"
            Option        "ZAxisMapping"        "4 5"
EndSection

---

### Post by Steve Hawkins on 2006-01-03
Continued search of other Linux forums reveals that several others are having this same problem.  So far no solutions.

---

### Post by supenguin on 2006-01-03
I've got a Logitech optical wheel mouse that always fails to work on startup.  However, if I unplug it and then plug it back in, it will start working.

---

### Post by Steve Hawkins on 2006-01-03
supenguin,

I just tried that on mine and it did not make any difference.  I have noticed, however that the mouse buttons always work.  It's just that the power to the laser is off.  It gets turned off during boot.

Does anyone know of keyboard, key stroke sequences, that I can use to get at the admin menu items without the mouse?

---

### Post by Steve Hawkins on 2006-01-03
I found the key strokes needed.  (alt space) F1 will bring open the Applications menu that is at the top.  You can then navigate by using the arrow keys and the tab key.

That is momentarily hold down the "alt" key and the "space bar" and while they are down tap the "F1" key.

---

### Post by ysse on 2006-01-03
Alt-F1 will get you to the menus on the top panel.

Start a terminal and type dmesg, and maybe you'll see some error messages.

---

### Post by Steve Hawkins on 2006-01-03
ysse,

Thanks.  I have been over the dmesg output and find nothing that offers any solid clues.  It puzzles me that the mouse buttons work, but the laser is powered off.  If I shut the computer all the way down, then power it back up, when it comes up the mouse laser light is on.  It goes off during the boot just before the "real time clock" message appears on the screen.

Looking around the internet, I think a lot of folks are having this, or very similar problems, but only with laser mice.

---

### Post by Steve Hawkins on 2006-01-03
ysse,

Thanks.  I have been over the dmesg output and find nothing that offers any solid clues.  It puzzles me that the mouse buttons work, but the laser is powered off.  If I shut the computer all the way down, then power it back up, when it comes up the mouse laser light is on.  It goes off during the boot just before the "real time clock" message appears on the screen.

Looking around the internet, I think a lot of folks are having this, or very similar problems, but it seem only with optical mice.

---

### Post by Steve Hawkins on 2006-01-04
During the night I tried the optical mouse on several other computers.  It works fine on all of them expect those running ubuntu.  I tried several other mice on the ubuntu boxes and it seems to like all but the optica mice.  Arrrrrrrrrgh!

---

### Post by Steve Hawkins on 2006-01-05
After spending way too many hours working on this, I decided that it was not worth $19 dollars (What a new Logitech mouse cost).  I bought one and everything works great.  I suspect that there is some thing about the other mouse that ubuntu can't recognize.  I have shifted it to another computer where it works great.

---

