---
title: "Wireless Mouse Locking up on Laptop in Edgy Eft"
date: 2006-11-13
forum: Hardware &amp; Laptops
---

### Post by novakry on 2006-11-13
Hi,

I've been having a single problem with Firefox in that when I'm browsing with a wireless mouse "Microsoft Wireless Notebook Optical Mouse 4000", also I've tried Logitech Wireless Notebook Mouse too. The basic problem is, when i first load Ubuntu up, the mouse works fine. I load up Firefox the mouse is still working, but after a short while of using Firefox the mouse will freeze . I tried ordinarily to unplug the usb receiver for the mouse and plug it back in again, or try a different port. This brought no Avril, I even tried using a "Logitech Wireless MX1000 Laser Mouse" and the same thing happens. I then proceeded to try reloading ubuntu, before i updated to edgy eft. I used the mouse in linux and the mouse received no lock ups. So i believe that this is an Edgy Eft only issue. 

I'm pretty new to using linux, so I don't know first how to diagnose the problem, is there a way to get the terminal to pick up on an possible hidden error that crops up when the mouse fails within firefox? I will try using Opera in the mean time to and see if the problem is only within firefox, I would ideally like to use Firefox.

Hopefully someone else has been having problems like this in a similar situation. 

TYIA,

Novakry

---

### Post by novakry on 2006-11-13
Just to confirm the mouse does not lock up in Opera, just firefox.

---

### Post by novakry on 2006-11-13
i guess no one has been having similar problems?

---

### Post by RobMBaker on 2006-11-22
Yes, I've just today installed/upgraded to Edgy from Dapper; and my USB (though not wireless) mouse freezes after a while in Firefox.
I think it's a USB issue, rather than just the mouse; but only because a similar problem occurred when I tried to install the ATI drivers a while ago. I ended up having to go back to the generic driver ...

Shame no-one has replied with any way of solving this yet.
It annoys me having to keep going back to the stupid touch-pad!

---

### Post by adam.tropics on 2006-11-22
same with Logitech MX1000. Sometimes after an hour, sometimes after a day. Still trying to figure it out.

---

### Post by adam.tropics on 2006-11-22
...wondering about the new flash plugin. Do you all have it installed?

---

### Post by RobMBaker on 2006-11-22
New flash plugin ... as in Flash 9? If so, then yes.
Could be that, although why would it be a problem in Edgy but not Dapper? I've had Flash 9 installed for about a week and everything was fine before.

It all started when I upgraded to Edgy, or probably more importantly, to Firefox 2.0 ...

This may be nothing, but it also seems to freeze when I'm in one of the Firefox Preferences menus; as opposed to just dropping the mouse randomly while browsing. Is that the same for you guys? Or does it just freeze the mouse whenever, regardless of whether you're using an extension or something at the time?

---

### Post by adam.tropics on 2006-11-22
Fine with the menus here. As for flash9, and watch it break as fast as I can type this, but I uninstalled flash9 a bit ago, no freezes yet....time will tell I guess! As for the why...I have no idea!

---

### Post by adam.tropics on 2006-11-22
bugger!.........no, not that!


maybe have a look at the versions of evdev for dapper versus edgy?

---

### Post by adam.tropics on 2006-11-22
Ok, so reinstalled flash. got rid of Opera, don't like it, and am checking a different evdev (driver). In early Dapper there was a problem with evdev, and we had to use an older version, which is still available [from here]("http://ubuntuforums.org/showthread.php?t=188302"). Post 1, section1. I don't want to jinx it (!) but so far......!

---

### Post by RobMBaker on 2006-11-22
Pardon my ignorance, but what does evdev do/what's it for?

Lol, I came on here to check the thread ... and my mouse froze when I clicked on one of the 'Close Tab' buttons ... how fitting.

---

### Post by adam.tropics on 2006-11-22
> **RobMBaker said:**
> Pardon my ignorance, but what does evdev do/what's it for?

Lol, I came on here to check the thread ... and my mouse froze when I clicked on one of the 'Close Tab' buttons ... how fitting.


[This link should]("http://packages.ubuntu.com/edgy/x11/xserver-xorg-input-evdev") answer your question....... So I use evdev in /etc/X11/xorg.conf, as follows...

```

Section "InputDevice"
    Identifier "Configured Mouse"
    **Driver     "evdev"**
    Option     "CorePointer"
    Option    "Device"    "/dev/input/event9" 
    Option "ZAxisMapping" "4 5 6 7"
EndSection
```

---

### Post by adam.tropics on 2006-11-23
3 hours and no freeze yet!....crossing fingers!

---

### Post by novakry on 2006-11-23
Hey Guys,

sorry for not posting in a while, but my main pc has been out of action. So I just took a break from it all. 

Anyway, I'll try your evdev thingy change and see if that helps. Mine however doesn't freeze, it just locks the mouse. So I can carry on using the touch pad and the Ubuntu like it never happened, evdev sounds like it could be the problem, because the usb port is still available for removable media. Anyway I'll let you know if this works *fingers crossed it does*.

Novakry

---

### Post by RobMBaker on 2006-11-23
Thanks for the link. I'm reluctant to change driver though, as the generic 'mouse' driver has always worked before. As they say: If it ain't broke ...

---

### Post by adam.tropics on 2006-11-23
> **novakry said:**
> 
Anyway, I'll try your evdev thingy change and see if that helps. Mine however doesn't freeze, it just locks the mouse. So I can carry on using the touch pad and the Ubuntu like it never happened, evdev sounds like it could be the problem, because the usb port is still available for removable media. Anyway I'll let you know if this works *fingers crossed it does*.

Yes, sorry, perhaps I explained it poorly, same her. Just mouse, and can still use touchpad.....reluctantly.

> **RobMBaker said:**
> Thanks for the link. I'm reluctant to change driver though, as the generic 'mouse' driver has always worked before. As they say: If it ain't broke ...

Yes and I am not sure about wired usb mouse issues as i don't have one currently, though when I did, like you, just used the generic driver.

---

### Post by novakry on 2006-11-23
Thanks so much, you can't believe how happy I am not to use the touchpad AGAIN!. Oh yeah it worked like a charm, glad it was something so simple.

Thanks Again

Novakry

---

### Post by novakry on 2006-11-23
That just takes the biscuit, As soon as i clicked send reply to this post the mouse locked up again. Guess its not going to be so simple for me.

---

### Post by RobMBaker on 2006-11-23
Oh well, seeing as using evdev doesn't seem to solve it; I'll stick with the generic mouse driver for now, until the real cause of this issue is sorted.

I'm almost getting used to the touchpad now ... still annoys me though. My usb mouse is currently frozen but I can't be bothered to reboot.

---

### Post by novakry on 2006-11-26
> **RobMBaker said:**
> Oh well, seeing as using evdev doesn't seem to solve it; I'll stick with the generic mouse driver for now, until the real cause of this issue is sorted.

I'm almost getting used to the touchpad now ... still annoys me though. My usb mouse is currently frozen but I can't be bothered to reboot.

Let me know if you come up with anything, I'm becoming pretty used to the touchpad in the mean time. Its just so sensitive, and can be annoying. I'm kinda glad someone is stuck with the same problem, because hopefully you'll find something out. I really wouldn't know where to begin, I got the terminal to output errors, I crashed the mouse and no error showed up. So to me its mystery.

Novakry

---

### Post by RobMBaker on 2006-11-29
I don't want this to 'jinx' my lack of mouse freezing, but it seems the problem has gone away for me.
I did two things, either one could have solved the problem:
1) Booted 30 times so the filesystem checker kicked in and ran a scan-type-thing
2) At about the same time, I had just uninstalled the stupid Totem plugin - I much prefer mplayer ... and I was slightly annoyed that the Totem one overrides any previous plugins when you upgrade to Edgy.

I'm leaning towards the totem plugin as the offending package, but that's just a biased opinion. The package is totem-mozilla, just in case that was where the problem was. I'm using mozilla-mplayer now, as I was in Dapper; and have yet to have a mouse-freeze.

Hope that's helpful.

---

### Post by RobMBaker on 2006-11-29
By the by, does anyone know how to manually run the filesystem check? I looked in the help docs, but couldn't find what I wanted.

---

### Post by adam.tropics on 2006-11-29
open a terminal and read up on it.

```
 man fsck
```

Glad your mouse freeze days seem over!

---

### Post by RobMBaker on 2006-11-29
Thanks for letting me know the name of the manual entry.
Very helpful.

---

### Post by adam.tropics on 2006-11-29
lol. You might [prefer to look at this]("http://www.ubuntuforums.org/showthread.php?t=295262&highlight=Bonager"). It sits in the notification tray. If you hover over it, it will tell you when the next scheduled scan is (how many more boots), and if you click it, it gives you the option to force a scan on the next boot. I have tried it, and it seems pretty good.

---

### Post by RobMBaker on 2006-11-29
I just realised, my last comment looks a tad sarcastic - it wasn't. I genuinely didn't know what the process was called before. :)

---

### Post by adam.tropics on 2006-11-30
> **RobMBaker said:**
> I just realised, my last comment looks a tad sarcastic - it wasn't. I genuinely didn't know what the process was called before. :)

No drama at all, but thanks all the same. Hope the mouse is still going good.

---

### Post by Frem on 2006-12-03
*Is* the mouse still working? We've got a similar sounding problem here: [http://ubuntuforums.org/showthread.php?t=311462](http://ubuntuforums.org/showthread.php?t=311462)

---

### Post by RobMBaker on 2006-12-04
Hmm ... it seems that the problem isn't fixed here ... although I have only had one mouse-freeze since I posted that everything was ok. This occurred during a fairly 'heavy' session with multiple videos loading in different tabs - Firefox slowed down and hogged the cpu, before freezing the usb mouse.
Hasn't happened otherwise but - unlike before, when it would drop the mouse after a matter of minutes using Firefox.

---

