---
title: "T60 Feisty undock/dock"
date: 2007-05-08
forum: Hardware &amp; Laptops
---

### Post by sagyvolkov on 2007-05-08
Hi Everyone,

I'm not looking for anything fancy with my T60 and port replicator, no twin view, big desktop or any of those.
I just want to be able to undock/dock and actually have X move the screen from the laptop LCD to my external monitor and back when i undock/dock from my port replicator (not a docking station).

Is that possible?
I'm also running Beryl 2.0.2, but i'll sacrifice that if needed to get this thing working.

I've tried to find answers on google, but could see anything that is working.

I'd really appreciate help on this.

Thanks.

---

### Post by jjordan on 2007-05-08
Are you trying to make this automatic so that you do not need to use the function key?

-j

---

### Post by sagyvolkov on 2007-05-08
well, if place the laptop in the port replicator while the lid is open, the screen stays on the laptop LCD.
If the laptop was booted while connected to the port replicator, then the external monitor is working. If i hibernate the laptop at this stage and take it of port replicator, when i resume power, the screen is black once X starts, since i assume it still sends all info the the xterernal monitor which not connected now. so i have a blank screen that i can't do nothing with unless i connect an external monitor to it, shutdown and then boot again so i can work with the laptop LCD monitor.

So i'm not looking for something fancy to do this automatically (though it would be nice), just basically something to get the Fn+F7 key work (or bind it to any other key, don't really care), something that will xorg, change default screen and now use this one.

Is that possible?

Thanks

---

### Post by jjordan on 2007-05-08
Hmmm, sounds like you need the driver for the "special keys".  Ubuntu includes tpb which allows you to use IBMs special keys but I didn't see anything for Lenova.  Have you looked for general Linux guidence for your laptop.  The T60 is very popular and pretty well supported. 

Check out this Link:
[http://www.thinkwiki.org/wiki/Category:T60](http://www.thinkwiki.org/wiki/Category:T60)

If your external monitor is a diffrent resolution than the T60's display you may need to make a script to adjust the resolution when you switch.

-j

---

### Post by sagyvolkov on 2007-05-08
I've searched for information.
[http://www.linux.org.mt/node/82#AEN53]("http://www.linux.org.mt/node/82#AEN53")
Clearly specify that Fn+F7 is not working. 
I don't really care what key does it, all i need is to know how to tell the video card to actually change outout to and from the LCD laptop. 
You have any idea on that?

---

### Post by sagyvolkov on 2007-05-10
Anyone have an idea how to get this to work?
Is there anybody out there?

---

### Post by jjordan on 2007-05-10
Your xorg.conf file must have two screen sections, changing the default screen changes which screen the video output is displayed on.  It is possible to write a script that will change these back and forth but that would mean you had to restart xwindows each time, hence the need for the "driver" for the special keys, it is not just a conduit to the keys, it provides the background functionality to control the hardware.  

Do you have the ATI video "card" or the Intel?

When you undock, and end up with a blank screen, ctrl+alt+bkspc will restart xwindows and takes much less time than rebooting.  Not a perfect solution.

Sorry, if my suggestions are not helpful to you.  This a very poplular laptop for Linux and while what you want to do is a bit unusual it should not be a problem.  Most people set up twinview or ximerama when using an external monitor.  Those options also have some issues.  I use twinview so when I undock, the second xwindows session is still running, waste of memory but the only time I have a problem is when some modal program is running and then I have to explicitly kill it form the session on the laptop screen.

-j

---

### Post by Jingo on 2007-05-10
I have been waiting for a solution to this for 2 years now... I am on a T42 and port replicator.

I think we have to wait for the Radeon driver to support Randr 1.2. Alex Deucher and some other guys are working on this.
With any luck, this should hit Feisty+1.

Xorg's mailinglists are informative.
[http://lists.freedesktop.org/archives/xorg/](http://lists.freedesktop.org/archives/xorg/)
[http://lists.freedesktop.org/archives/xorg-commit/](http://lists.freedesktop.org/archives/xorg-commit/)
[http://lists.freedesktop.org/archives/xorg-driver-ati/](http://lists.freedesktop.org/archives/xorg-driver-ati/)

---

### Post by sagyvolkov on 2007-05-12
Thanks jjrodan and jingo for you replies and explanation.

> **jjordan said:**
> Your xorg.conf file must have two screen sections, changing the default screen changes which screen the video output is displayed on.  It is possible to write a script that will change these back and forth but that would mean you had to restart xwindows each time, hence the need for the "driver" for the special keys, it is not just a conduit to the keys, it provides the background functionality to control the hardware.  

Do you have the ATI video "card" or the Intel?

I have an ATI card.
So let me get this straight, twinview will show whatever i see on the laptop LCD also on the external monitor?

---

### Post by aitvo on 2007-05-12
I wrote this script to fix this very issue, though an another notebook with the ATI card.

[http://www.fewt.com/quickswitch.shtml](http://www.fewt.com/quickswitch.shtml)

It assumes you are using FGLRX. Just edit the script and tell it what resolutions you want on each display.

---

### Post by sagyvolkov on 2007-05-16
Thanks aitvo, i'll try your script today.

---

### Post by sagyvolkov on 2007-05-16
Why is "aticonfig --query-monitor" not showing any monitor connected if run gnome+Beryl?
Any thoughts? (i get the correct output when running just a gnome session).

Thanks.

---

### Post by aitvo on 2007-05-16
> **sagyvolkov said:**
> Why is "aticonfig --query-monitor" not showing any monitor connected if run gnome+Beryl?
Any thoughts? (i get the correct output when running just a gnome session).

Thanks.

Honestly, I'm not sure, as I don't use XGL or Beryl on my notebook with the ATI card.

---

### Post by sagyvolkov on 2007-05-21
Well, i forgot about beryl for now.
Your scripts works great on gnome. 
Thanks for your help aitvo!!!

---

