---
title: "Touchpad of Doom"
date: 2005-07-22
forum: Hardware &amp; Laptops
---

### Post by LodeRunner on 2005-07-22
In short: I can't disable it, I can't turn off tap click, and I can't get syndaemon to work.

Without syndaemon (and with tap click turned on) typing becomes an exercise in frustration.  If one of my thumbs brushes the touchpad, my cursor suddenly hops to whereever the mouse is.  Sometimes I change windows entirely.  What I've tried so far:


Syndaemon (this is supposed to automatically disable the touchpad when you type):
"Can't access shared memory area. SHMConfig disabled?"

I've added  Option "SHMConfig" "on", but the error persists.  From another thread I got the idea to change "Protocol" to "alps".  This lets Syndaemon run, and when run in a terminal it does indeed display "disable" when I type and "enable" two seconds after I stop typing.  

Despite this, my touchpad does not actually disable.


Tap Click:

added Option 		"MaxTapTime"	 "0" to xorg.conf.
Does nothing.  Tap clicking works as normal. 


Disable touchpad (DIE DIE DIE MOTHER****ER--DIE AND BURN IN HELL):

I tried the script from [this thread](http://www.ubuntuforums.org/showthread.php?t=43753) , but it doesn't work.  

Adding Option "TouchpadOff" "1" does nothing.
Removing the touchpad entirely from xorg.conf causes X to crap itself on boot.

I guess there's always ```
Option     "Ducktape"      "on" 
``` but I am trying to avoid this at all costs.   I'm a still very much a Linux newbie, so I'm really at a loss for what to try next.  Any suggestions would be appreciated.

Oh yeah--the laptop is a Dell Inspiron 6000D.

---

### Post by kiddo on 2005-07-22
> Option     "Ducktape"      "on"

LOL I was about to suggest ductaping a paperboard on it ;) (sorry, useless post, can't really help you)

---

### Post by LodeRunner on 2005-07-25
I don't usually bump, but this is really driving me insane.  I just lost a multi-page email because my thumb brushed the touchpad.  It's amazingly frustrating.  Ubuntu detected and automatically set up my touchpad and even turned on tapclick, yet I cannot disable any of it.  It's almost as if it's ignoring xorg.conf altogether.

I am supposed to be editting /etc/X11/xorg.conf, right?

I don't know if devs read this but IMO, tapclick should NOT be turned on by default unless syndaemon can be configured and turned on by default.  If I wasn't so dead-set on having a linux laptop, I would've gone back to XP by now.

Update:  I just uninstalled the driver (xorg-driver-synaptics) and it STILL WORKS PERFECTLY.  This is getting almost surreal.  It_just_won't_die.  

I'm thinking maybe normal methods only deal it subdual damage. Does anybody have some holy water they could lend me?

---

### Post by rhystic on 2005-08-20
To get syndaemon to work i needed to put the following in /etc/X11/xorg.conf:

Option          "SHMConfig"             "true" 

Notice the "true" ...  it wouldn't work for me if i  used "on" as you have posted above.

Also to disable the tap click on your touchpad put the following: 

Option        "MaxTapTime"              "0"

These two options should solve all your problems... they did on my lappy   :)

---

