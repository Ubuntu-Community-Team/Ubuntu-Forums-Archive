---
title: "Mouse will sometimes only move up and down"
date: 2006-12-08
forum: Hardware &amp; Laptops
---

### Post by authortitle on 2006-12-08
Hi all,

Let me prefix my request for help by saying that I am running Ubuntu on my laptop, which can be a bit wierd (sometimes won't power on for days at a time before randomly working again etc.), but it's been good for the past few weeks. I've only had Ubuntu on it for a few days, initally (netboot installed) Hoary -> Dapper -> Breezy and now on Edgy.

The problem I am having is that sometimes (not all the time, making it even harder to debug) my mouse pointer will only move up and down in X. It moves up and down when I move left and right, does nothing when I move it up and down, and clicking any button causes it to jump right slightly. The mouse is a Logitech Cordless USB one, it came with my desktop and has no other branding info on it but it's probably the cheapest one they do. 

The reason for me using a USB mouse is that my trackpad was being strange, so I messed around with the internal connector and somehow managed to scrape all the contact off the connector :-? lol.

This happens maybe just over half the time I boot, the rest of the time it works fine, with the exception that I normally have to unplug and replug in the USB "dongle" if it is left plugged in when I reboot, otherwise it doesn't see the mouse. Obviously, the wierd thing is that it doesn't always happen, maybe pointing to a hardware issue, but this has _never_ happened in Windows so it can't just be that.

I'm not really sure where to start... I've played with xorg.conf settings to no avail, I've tried playing with modprobe/removing usbhid etc, but I don't know where to start with a tool like xmodmap and I don't know of any command-line based tools to test my mouse outside of X (other than cat /dev/input/mice which just shows either spaces or )'s when I move it).

If anyone has any ideas of how I can start trying to diagnose this, it'd be much appreciated!

Thanks
Tom

---

### Post by anti_microsoft on 2006-12-08
Mine does this as well at times (on desktop). Is it an optical mouse? I have found that mine loses track of where it is at on my mousepad, if I pick it up and put it back down all is fine.

---

### Post by authortitle on 2006-12-08
Thanks for the reply, anti_ms, but it's nothing like that. It works flawlessly under Windows, but the axis/button mapping appears to sometimes be messed up in Linux. Left/right causes it to move up down, up/down causes it to do nothing, clicking any mouse button causes it to nudge left a big, holding a mouse button and moving up/down (I think?) causes it move left/right. Most bizarre, I'm sure some xmodmap trickery or similar could sort it if someone can advise me on how to go about doing so..

---

### Post by authortitle on 2006-12-19
For anyone who may encounter the same issue - "sudo modprobe -r usbmouse" sorted it temporarily, adding "usbmouse" to /etc/modules.d/blacklist has sorted it permanently :) Wierd but fixed anyway!

---

