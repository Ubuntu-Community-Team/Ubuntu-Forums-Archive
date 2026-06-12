---
title: "Digital camera not detected by gnome"
date: 2005-10-22
forum: Hardware &amp; Laptops
---

### Post by weijie90 on 2005-10-22
hi
i plugged in my Brica Digiart520 camera to the usb drive, and hit the camera's power button.
nothing happened in gnome, but it was detected in lsusb.
i ran: sudo mount -t auto /dev/sda1 /mnt/digicam
and it worked.

how do i make Breezy detect my digicam automatically, and place an icon on the desktop? it does that with my mp3 player. thanks!

---

### Post by weijie90 on 2005-10-24
please help

---

### Post by ZephyrXero on 2005-10-25
I'm having a similar problem. Only thing is that it worked perfectly fine with Hoary :( Did they not include the auto mounting camera program by default this time???

My camera is a Kodak DC4800

---

### Post by Mozzer on 2005-10-26
I just plugged in my Kodak EasyShare CX7525. On Windows it recommends you use the official software but you don't have to - you can just use it as a removable drive through My Computer. However, Ubuntu makes no indication that a camera is present.

When I ran lsusb I got this line:

```
Bus 006 Device 002: ID 040a:0586 Kodak Co
```

But I don't really know how this helps.

Mozzer

EDIT - I have found information in other threads about using some command line software called gphoto2 but this doesn't help either as my camera is not supported. However it looks like the DC4800 will work so try it.

---

### Post by jdtanner on 2005-10-26
Quite honestly, it appears that loads of people are having problems with USB devices, floppy disks, and cd-rom drives not mounting automatically when they are inserted/loaded with their relevant media. There are lots of mentions of this on Bugzilla, but noone seems to have managed to pin down what is causing the problem.

This is going to sound a lot worse that it is inteded to, but surely this is one of the main reasons why people want to use Ubuntu...it just works! However, for quite a few people it just doesn't :-(

As I've said before, I'd love to be able to jump in and fix this myself but I honestly wouldn't know where to start. 

Cheers,
JohnT

---

### Post by Vulcan on 2005-11-07
About this, I don't know if it's working or not? I mean, my camera is blinking its ready light, and I don't know how to actually see my pictures... my camera is Kodak Easyshare C330.

---

### Post by Mustard on 2005-11-07
[QUOTE=Vulcan]About this, I don't know if it's working or not? I mean, my camera is blinking its ready light, and I don't know how to actually see my pictures... my camera is Kodak Easyshare C330.[/QUOTE]

My Kodak Easyshare CX7300 is working ok, on breezy.  It should detect it, after you have connected it up and turned on the camera power, then load up a dialogue asking you to import pictures.

I do have issues with my USB drive not being detected at startup, but I can unplug it and plug it in again and it detects it then.

---

### Post by Vulcan on 2005-11-07
Well, for some reason it's not coming up.

---

### Post by jvictor on 2005-11-07
PPL plz try GTKAM, it has v less hassles.. when u set up the camera, check if ur model is listed , if not give the camera as PTP class camera

---

### Post by Vulcan on 2005-11-08
Can you tell me how to do that? I'm a newbie to Linux. >_>

When I try to run gphotocoll, I get:> Postgres database not available!

---

### Post by Mustard on 2005-11-08
[QUOTE=Vulcan]Can you tell me how to do that? I'm a newbie to Linux.[/QUOTE]

Make sure universe repository is enabled and use this command to install.

```
sudo apt-get install gtkam
```

---

### Post by ZephyrXero on 2005-11-10
gtkam is working for me...but it's not nearly as nice as the camera software that came with Hoary by default :(

---

### Post by michael_salcher on 2005-11-10
[QUOTE=jvictor]PPL plz try GTKAM, it has v less hassles.. when u set up the camera, check if ur model is listed , if not give the camera as PTP class camera[/QUOTE]

you should be able to find gtkam in synaptic.

---

### Post by cokehabit on 2006-06-26
to mount cameras automagically and to choose the programs just go to ```
gnome-volume-properties
```

---

