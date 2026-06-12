---
title: "Disable touchpad"
date: 2010-12-12
forum: Hardware
---

### Post by kpgalligan on 2010-12-12
I have a new HP laptop. Dm4, I believe.  I've found HP touchpads to be universally horrible because I always touch them while typing or whatever.  I use a mouse anyway.  I'd like to disable the touchpad 

JUST HAPPENED AGAIN!!!

Anyway, I'd like to disable the touchpad completely, or at least when the mouse is plugged in.  My other HP actually has a little button that turns it off.  This one does not.  I've disabled it in System > Preferences > Pointing Devices.  It seems to be disabled for a little while, but then comes back on.  That panel still says its disabled, but its still working.

Anything else to try?  I really, really hate this touchpad.

Thanks in advance.

---

### Post by kpgalligan on 2010-12-12
A little update.  In that panel, I re-enabled it, but clicked "Disable while any other devices are connected".  Clicked OK.  Pulled out my usb mouse, put it back in, but the touchpad was still on.  Opened up the panel again, and that check is not checked.  I re-check, then close.  Open panel, and its unchecked.

---

### Post by StephenDavison on 2010-12-13
In disabling the touchpad, were you using the "Disable touchpad while typing" option?  That's the option I see in the Gnome desktop preferences, and it has worked well for my netbook.

---

### Post by kpgalligan on 2010-12-13
I've tried the "while typing" bit, but it never seemed to matter.  I think it pauses briefly, but I would still get crappy behavior if I stopped typing for a second, then brushed it before I was able to actually click a button.

I'm thinking there's some really simple, obvious way to have the touchpad simply not doing anything, but so far I haven't found it.

---

### Post by kpgalligan on 2010-12-16
Got it!!! I think, anyway.

synclient TouchpadOff=1 would keep turning back on after a while.  It turns out, the "disable while typing" was interfering with that.  I unchecked the "disable while typing", and now it seems to stay off.

---

### Post by Aaron Whisman on 2010-12-16
Yeees, and if I remember, most recent HP laptops can disable the touchpad with Fn+F5. This might not be the case with your super new HP laptop, however.

---

### Post by kpgalligan on 2010-12-16
This new keyboard kind of sucks, actually.  It feels nice, but they have made some questionable key choices.  Firmly in the "entertainment" field, and not programming/work.  Nothing on here that I see to disable the pad physically.  The function keys have been repurposed for play controls.  You need to also press "fn" to use them.

Funny story, though. I bought one of these for someone else. Then this morning my laptop died.  It was also an HP.  A couple years old.  I had put in an SSD a couple months ago, and that seemed fine.  So, I bought another dm4.  4gigs, i5 proc, $650.  Good deal.  Anyway, I swapped the hard drive, and it booted up.  Zero problems.  Ubuntu/linux has come a long way on the laptop.  Thought I was going to kill the whole day installing and whatnot.

---

### Post by wilee-nilee on 2010-12-16
> **Aaron Whisman said:**
> Yeees, and if I remember, most recent HP laptops can disable the touchpad with Fn+F5. This might not be the case with your super new HP laptop, however.

probably correct with my acer aspire it is fn-f7

---

### Post by kpgalligan on 2010-12-16
fn+f5 is actually "f5".  Otherwise, its rewind.  f7 is stop.  Similar situation with the other buttons.

---

### Post by Aaron Whisman on 2010-12-16
Oh man, the new keyboards do sound odd.

---

### Post by kpgalligan on 2010-12-16
It is.  Price is hard to ignore, though, and besides the temporary touchpad stuff, I can say it works quite well with ubuntu 10.10.  Swapping the hard drive and doing ZERO config was pretty awesome.

---

### Post by Aaron Whisman on 2010-12-16
That's great to hear, I own an HP Elitebook that has satisfied me for quite some time, but is quite small. What exactly is that price that's hard to ignore? I might upgrade soon.

---

### Post by kpgalligan on 2010-12-16
[http://www.bestbuy.com/site/HP+-+Pavilion+Laptop+/+Intel%26%23174;+Core%26%23153;+i5+Processor+/+14%22+Display+/+4GB+Memory+/+500GB+Hard+Drive+-+Brushed+Aluminum/1260528.p?id=1218243761774&skuId=1260528](http://www.bestbuy.com/site/HP+-+Pavilion+Laptop+/+Intel%26%23174;+Core%26%23153;+i5+Processor+/+14%22+Display+/+4GB+Memory+/+500GB+Hard+Drive+-+Brushed+Aluminum/1260528.p?id=1218243761774&skuId=1260528)

HP - Pavilion Laptop / Intel® Core™ i5 Processor / 14" Display / 4GB Memory / 500GB Hard Drive

There's probably something about it I don't know, but I was blinded by the i5 proc.  The screen is much brighter than my old one, although the resolution kind of sucks.  I'm used to 1650x1050.  I use an external monitor on the side most of the time, though, so its not a huge deal.

Can't say much about the drive.  I never turned it on.  Put my SSD in there.  In all, pretty sweet machine.  Decent connectors.  3 usb, hdmi, vga, etc.  Hdmi to dvi works great.

---

### Post by Aaron Whisman on 2010-12-16
Sounds quite awesome. The Elitebook has a dock that includes the dvdrom, 4 extra USB ports, vga, and it can be removed which improves the battery life by about 4 or 5 hours, hah. If you're on the move and don't need to read discs often it's a pretty great small laptop.

---

### Post by ionplay on 2011-01-09
> **kpgalligan said:**
> Got it!!! I think, anyway.

synclient TouchpadOff=1 would keep turning back on after a while.  It turns out, the "disable while typing" was interfering with that.  I unchecked the "disable while typing", and now it seems to stay off.

where did you type that?
just at the prompt??

I am on a ASUS X72D
and the FN + F9 does nothing

I tried calling synclient from the command line and it has no effect either

K72Dr:~$ synclient TouchpadOff=1
K72Dr:~$ synclient -l | grep Touch
    TouchpadOff             = 0
K72Dr:~$ synclient TouchpadOff=1
K72Dr:~$ synclient -l | grep Touch
    TouchpadOff             = 0

how did you get yours to stop working using synclient?

---

### Post by ionplay on 2011-01-09
I tried some xinput variations in addition to more with the synclient from the command line, no luck.

Just created a panel ("Add to Panel") launcher
**Name:** Disable touchpad
 **Command: **synclient TouchPadOff=1
 **Comment: **Disable TouchPad

oddly enough this works every time I click the launcher

and then about 15 seconds later, the touchpad is auto enabled again

anyone understand what is happening here???

---

### Post by bilkay on 2011-01-10
I have good news and bad news.

The good news is that there is a configuration program that provides an option for disabling the touchpad.

The bad news is that it isn't on any of the default menus, and I can't remember what the command is.

I'll keep looking.

---

### Post by bilkay on 2011-01-10
> **bilkay said:**
> I have good news and bad news.

The good news is that there is a configuration program that provides an option for disabling the touchpad.

The bad news is that it isn't on any of the default menus, and I can't remember what the command is.

I'll keep looking.
I found it!

```
$ gconf-editor
```

desktop -> gnome -> peripherals -> touchpad

uncheck touchpad_enabled

---

