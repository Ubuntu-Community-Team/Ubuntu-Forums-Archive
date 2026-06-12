---
title: "HDMI not working on Ubuntu Server"
date: 2013-03-14
forum: Hardware
---

### Post by Sarge888 on 2013-03-14
Im having an issue trying to get my display to show the console of Ubuntu Server after it boots on my server box. I have it connected to one of my monitors by HDMI and m,y monitor just goes blank saying no signal after the grub screen.
HDMI/monitor will show the initial bootup and even the grub selection screen. but after selecting ubuntu server from the list the screen shows some text(handing off control to Ubuntu im guessing) then nothing, screen goes to sleep. Now im not runniong any GUI so i dont understand why a simple console wont be shown. Im hoping someone could help me fix this as id like to be able to watch the start-up every now and again to diagnose issues with Ubuntu's start-up if and when needed. as well as having direct control if my ssh crashes.
Heres some info that may help you guys help me lol.
Output of "xrandr" is
"Cant open display"

The built in videocard is a GMA 3650 if im reading this spec sheet right.


So any help would be great, thanks.

---

### Post by diebels on 2013-04-28
Is your server an Intel Atom? You could try video=LVDS-1:d on the grub kernel command line in case it has this output and is defaulting to it. Does it have VGA?

---

### Post by Sarge888 on 2013-04-29
yes it is an Atom processor. I will have to try this when im finished with some uploading i am doing. and yes the server does have a VGA port however i do not own any VGA cables anymore(lost them in a recent move). soi couldnt just use a VGA or else i would have lol. i dont plan to buy one anytime soon.

thx for the suggestion, hopefully it works and fixes this issue/glitch/feature lol.

---

