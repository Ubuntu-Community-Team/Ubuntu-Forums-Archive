---
title: "&quot;Play For Sure&quot; MP3 Players"
date: 2006-02-15
forum: Hardware &amp; Laptops
---

### Post by sethrd on 2006-02-15
I have an MP3 player (Philips GoGear) that, under windows, only seems to be able to sync using Windows Media Player. I've yet to find another program that allows me to put files on it. My question is, are there any programs out there for linux that allow me to sync? I've used Ubuntu before, but quickly got rid of it due to mouse issues. If you own a Dell laptop, you know what I'm talking about. I've done some research into it, and it seems there are some fixes for it now, but before I make the switch again, I neede to find some software for my MP3 player.


So, anyone have any ideas?

---

### Post by austin on 2006-02-17
are you sure this player doesn't simply behave as "removable media" via usb? If so, you can simply use nautilus to work on the files (like any other directory). You can try with a ubuntui live-cd, just connect usb and watch out for icons on your desktop.

---

### Post by sethrd on 2006-02-22
Yeah, I'm sure it doesn't. I've tried. Anyone else?

---

### Post by t2000kw on 2007-11-21
This is a very late reply on the mouse issue for those who read the thread later on.

I have an old Dell Inspiron 7000 that had some mouse issues. Seems as if I would be typing into an email or word processor and the insertion point (text cursor) would jump (usually upwards) and allow text to be inserted somewhere else where I didn't intend it to be.

Syndaemon simply disables the touchpad for a certain amount of time (you can configure this or accept the default) so that if you are typing and bump against the touchpad, you won't end up typing some of your paragraph in the middle of a paragraph above. It made the most difference for me. 


For Syndaemon to work, you'll need to add this to your /etc/x11/xorg.conf file (in recent version of Ubuntu).

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
        Option          "SHMConfig"             "on"
EndSection

For more information, type these words into Google and read on . . .

disable touchpad typing ubuntu

---

### Post by Sastraxi on 2007-11-21
They're called "mtp" devices in the "FOSS" world, and they are supported by a few programs. I think amarok works? Maybe rhythmbox?

Edit: erm, yeah. Mtp. That's what I meant! :D

---

### Post by EXCiD3 on 2007-11-21
My Creative Zen Xtra is a Plays for Sure device however I was able to sync it using an app in the repositories. I think the app only works for Zen's but it should easily be usable using MTP (micro$haft's proprietary transfer protocol). I'm not sure what applications use it, but MTP is the protocol you will have to use to sync. Have you tried Amarok? I think i lucked out as im pretty sure my zen xtra shows up as a usb drive...but its been ages since ive synced it.

Let me go play with it a bit and I'll see what i can find out. I'm at home right now with my parent's dialup :( so once i get back i to college i can try out some more stuff and let you know.

---

