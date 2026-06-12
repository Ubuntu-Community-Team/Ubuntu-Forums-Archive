---
title: "Microsoft USB Optical Mouse Issues"
date: 2005-12-06
forum: General Help
---

### Post by sdelic on 2005-12-06
Greetings!

I've looked long and hard through the forums and wiki and can't find a solution to my problem. My current xorg.conf is:

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "ZAxisMapping"          "4 5"

This is the external mouse I'm using on my Laptop which is an Avertec 3150. I upgraded from Horay and started having this problem after upgrading to Breezy. 

What happens is at very random times the mouse cursor will go to the left side of the screen and I can not move it horizontally across the screen. I can move it up and down but not across therefore rendering the mouse useless. The touchpad continues to work as normal. Any ideas? I've tried messing around with different xorg.conf's but so far no luck! Thanks!

This is running Gnome. I tried running XFCE for a few days and the same problem happened! If I restart the X server (ctrl-alt-backspace) thie problem corrects itself.

---

### Post by cilynx on 2005-12-06
In my experience, this is a problem with the hardware of the MS optical mouse.  All of our lab computers (running XP Pro) at school have MS optical mice and they occasionally peg to one side of the screen or just freak out in general.  Smacking them around a bit generally helps.  My best advice is to get a different mouse.  Any generic mouse will do.  I love my Logitec MX 700.

---

### Post by magnusbb on 2005-12-06
No, it's not a problem with your hardware - it's a problem with the protocol you're using, because it's wrong.

You want to use the ExplorerPS/2 protocol. Here's my section:

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option          "Buttons"               "7"
        Option          "ZAxisMapping"          "6 7"
        Option          "Resolution"            "100"
EndSection

I would also search the forums for the guide that gets the most out of your mouse, for example by using it thumb buttons in Firefox and Nautilus.

---

### Post by Joey French on 2005-12-06
Man, I scrapped my MS wireless optical mouse for this very reason. Randomly jumping to the top right corner, never figured out what the problem was...

---

