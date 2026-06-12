---
title: "Wow! WACOM Graphire Tablet works!!!"
date: 2005-06-01
forum: Hardware &amp; Laptops
---

### Post by PryGuy on 2005-06-01
Hello all!
I have discovered that my WACOM Graphire Tablet works under Ubuntu! It's amazing, I don't have to install any drivers, it was detected right after I plugged it into the USB port!!! And they say that Windows supports devices great! Pardon me but the WACOM hardware doesn't work under WindowsXP without drivers... Bravo, Ubuntu!!!

And the question is, I couldn't get the pressure sensitive features in Gimp. =( Guess that Gimp thinks that I'm using a mouse not a tablet. So, what do I do to make it work like a tablet not like a mouse?

Thanks in advance!

---

### Post by jaykleg on 2005-06-01
You might try [http://linuxwacom.sourceforge.net/](http://linuxwacom.sourceforge.net/). The Wacom Web site mentioned that location in their support system.

My wife's Graphire tablet worked in Windows XP without additional drivers, but only as a mouse. Loading the proprietary drivers was necessary to get the thing to work as a real graphics tablet in GIMP.

If you find a solution please post. Spouse would like to try an Ubuntu install on her main workstation and wants to know if her Graphire and GIMP will work for her in that OS.

---

### Post by jonatin on 2005-07-25
[QUOTE=jaykleg]You might try [http://linuxwacom.sourceforge.net/]("http://linuxwacom.sourceforge.net/"). The Wacom Web site mentioned that location in their support system.

My wife's Graphire tablet worked in Windows XP without additional drivers, but only as a mouse. Loading the proprietary drivers was necessary to get the thing to work as a real graphics tablet in GIMP.

If you find a solution please post. Spouse would like to try an Ubuntu install on her main workstation and wants to know if her Graphire and GIMP will work for her in that OS.[/QUOTE]

My wacom tablet works flawlessly in winxp without drivers (SP2)... pressure and everything in photoshop.  The driver didn't do anything but let me customize buttons and set the mouse acceleration to ungodly high levels.  Weird.
 
 Unfortunately, ubuntu doesn't handle it so well.

Linuxwacom works, but not like the 'official' drivers.  I've had problems on every machine I've tried, PPC, old x86 and new P4.  The pen works well enough after going through and setting up the xorg.conf, etc... but having the tablet plugged into a hub bounces it around between events (event3, event4... I even found it on event6 once) so I have to re-edit xorg.conf and ctrl-alt-bksp X.  The simple solution was to move it off the hub, and now it 'hardly ever' switches, but it still does it occasionally.  ](*,)

And the cursor 'dances' or some people say it 'wobbles' around between 2-3 pixels.  The screensaver never comes on, thats for sure.  Nothing I've seen fixes this... it's not a showstopper, just distracting and annoying.

---

### Post by jaykleg on 2005-07-25
Cursort wobbling or jumping would definitely be a show-stopper for my wife. I asked her about it. She just looked at me like -- "Are you crazy?" Heh.

 :smile:

---

### Post by egymonk on 2005-08-04
[QUOTE=jonatin]
And the cursor 'dances' or some people say it 'wobbles' around between 2-3 pixels.  The screensaver never comes on, thats for sure.  Nothing I've seen fixes this... it's not a showstopper, just distracting and annoying.[/QUOTE]

Wacom Xorg driver option 
            Option "Suppress" "4"
might solve your problem. (You can even increase the number up to 6.)
regards,
1 MonK

---

