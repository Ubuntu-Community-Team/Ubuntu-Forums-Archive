---
title: "Compile a tutorial for configuring win8 touch screen laptops in Ubuntu"
date: 2013-01-05
forum: Hardware
---

### Post by strikes2bowl on 2013-01-05
It's about time.

I have searched all over the internet and within this network with no luck in finding a guide that shows one how to turn a beautiful new touch screen laptop with crappy *** win8 into an even more beautiful new touch screen laptop with Ubuntu 12.10....with the touch screen features still enabled.

Currently, I am running a Sony Vaio SVT131290X with the following specs on Ubuntu 12.10:

Memory: 7.7 GiB
Processor: Intel Core i7-3517U CPU @ 1.90GHz x 4
Graphics: Within processor
OS type: 64-bit
Disk: 340.2 GB

Touch Screen: "Elan Touch Screen"  which in the xinput list output is listed like this:

Virtual core pointer
     ->Virtual core XTEST pointer
     ->ELAN Touchscreen
     ->SynPS/2 Synaptics TouchPad

Currently, the touch screen works, the only issue is that when I tap a button to make a selection on the screen, to close a program with the x circle for example, the touch screen input moves the cursor to the x circle, but does not actually execute the left click command that is necessary to close the window.

I have noticed there are a lot of others who have yet to figure out how to get touch screens in ubuntu to work, and with this new wave of windows 8 touch laptops it is time to finally solve this puzzle.

---

### Post by Lodmot on 2013-01-10
Hi,

I have an Acer Aspire V5 touch laptop, and I've tested Ubuntu on it. It seems like initially the touchscreen will click on things fine, but after a while it will just stop clicking on the screen. I think it's just a matter of Ubuntu lacking good support for touchscreens at this point in time, and we just have to wait until 13.04 or 13.10. 

I also noticed that Firefox doesn't scroll with flick gestures the way its Windows port can, so you have to press on the scrollbar at the right in order to move the page up and down. Pinch to zoom gestures also don't work as expected, which is a bummer. I have a feeling those are inputs that have to be recognized by the OS and not the browser, because on Windows 8 the same latest version of Firefox detects the gestures correctly. (Or it could be just a mere difference between the two ports of Firefox, who knows? :P)

The Nautilus file explorer, however, DOES scroll with flick gestures on a touchscreen, quite nicely I might add. But it's impossible to click on any files or folders... Weird...

Unity is amazing with the touchscreen, when it *works*. Lol. And Ubuntu actually has some multi-finger gestures for touchscreens that you can do:

-- Three fingers pushed together will reduce a maximized window.
-- Three fingers pulled apart will maximize a window.
-- Four fingers swiped to the right opens the dash (IIRC, this might not be right XD)
-- If you put 3 fingers on an open window then move around, it moves the window.

So there's some basic functionality for touchscreens in there, but from what I can tell playing around with it, its support is only in the beta stage right now.

I heard Fedora has better touch support than Ubuntu, but it crashed before it even booted up on my machine. XDD

Hope I was at least somewhat helpful. Good luck!

---

### Post by Lodmot on 2013-01-13
Hey, it's me again.

I've been messing with Ubuntu lately on my Acer V5 some more, and I came across several applications that make nice use of touchscreens. Here's a list of the ones I found:

**Empathy**
It already comes standard with Ubuntu, but the Empathy messaging client allows you to scroll through your buddy list with flick gestures on the touch screen. This may not seem very significant at first, but I realized they had to have implemented that feature specifically for touch screens when I tried the flick gesture in RhythmBox and it didn't scroll correctly at all. So if you're gonna be chatting with your friends on Ubuntu and you want to make some simple use of your touch screen, be sure to not replace Empathy with anything.

**KolourPaint**
This application is basically a clone of MS Paint, but it works great with touch screens. You can draw in it using your finger, and it works quite nicely. There isn't any multitouch support yet though, and there's a bug that happens once in a while where the cursor will jump around and draw random lines. They'll probably fix this in future updates though. But I'd give this guy a shot.

[B]Evolution
[/B]Like Empathy, Evolution has support for scrolling via flick gestures on touchscreens. Believe it or not, Thunderbird actually doesn't have that kind of support. As mentioned before, the application itself has to have the touchscreen features programmed into it, or it won't work. In Evolution, you can scroll through your inbox, and messages themselves with simple flicks of your fingers.

[B]MehPhoto
[/B]Alright, this is kind of an obscure one, but this is an image viewer for Linux that was actually designed specifically for Linux tablets and/or touchscreens. It's not in the software center, so you have to hunt for it on Google, and when you find it, it needs to be converted from an .RPM to a .DEB file using alien. But it's *definitely *worth the trouble to set up. MehPhoto has nice big buttons that your finger can easily press, it has flick gesture support, so you can flick through your photos just like on an iPhone, and it even has multitouch support! You can pinch to zoom, and turn your fingers to rotate images, and it's very fluid and fun to use actually! This is by far the most impressive touchscreen software I've seen running on Ubuntu so far. Simply a must-have! ^^

[B]Epiphany Web Browser
[/B]I tried every browser for Ubuntu that I could get my hands on, and believe it or not, Epiphany is the only one at this time that has built in support for flick-to-scroll using a touchscreen. Sadly, you cannot pinch to zoom for now, but on a laptop with a big 15.6 inch touchscreen, that's not exactly an issue. All other browsers including Firefox don't have touchscreen flick gestures built in. Instead they all register flicks as mouse drags to highlight sections of text (which is obviously not what you want to do). Plus Epiphany is small, really fast and just a really great browser. ^^

Those are all the applications I could find that work well with touchscreens under Ubuntu. Hope this helps you and anyone else out there that sees this topic. ^^

One more thing before I take my leave: I noticed that Ubuntu 12.10 seems to have more bugs with the touchscreen than the current daily builds of Ubuntu 13.04. This could be just happenstance, but I think they made fixes to certain touchscreen issues in 13.04, so you might want to hold off until 13.04 finally comes out. I'll fool around with the two versions some more and see if my results are consistent with each other.

---

### Post by xianbei on 2013-01-20
sweet, thanks. I have a Lenovo x220t and somehow missed out on kolourpaint.

the "Grab and Drag" add-on for Firefox is good for browsing too. It's helpful to add it to your toolbar so you can toggle it.

---

### Post by coolbr33z3 on 2013-06-15
Just to add to your findings, i have the same aspire V5.  A few things that i've noticed.  It's just when i single click, and like you said, it happens after a while.  There has got to be some kind of trigger that makes single click unresponsive.  3 and 4 finger touch, flick,application switcher (3 finger tap, 3 finger hold) all seem to work fine.  ALSO when i am in workspace switcher, single click seems to be back, but upon going to a desktop, single click disappears.  That leads me to think drivers are good, while multi-touch is still alive and kicking.  maybe its something simple i'm overlooking, maybe its a (hopefully) small bug that will get ironed out soon.  Either way, I'm stoked about dual booting ubuntu and windows SEVEN! Took 8 off until they get it together... maybe indefinitely.

PS this is on 13.04

> **Lodmot said:**
> Hi,

I have an Acer Aspire V5 touch laptop, and I've tested Ubuntu on it. It seems like initially the touchscreen will click on things fine, but after a while it will just stop clicking on the screen. I think it's just a matter of Ubuntu lacking good support for touchscreens at this point in time, and we just have to wait until 13.04 or 13.10. 

I also noticed that Firefox doesn't scroll with flick gestures the way its Windows port can, so you have to press on the scrollbar at the right in order to move the page up and down. Pinch to zoom gestures also don't work as expected, which is a bummer. I have a feeling those are inputs that have to be recognized by the OS and not the browser, because on Windows 8 the same latest version of Firefox detects the gestures correctly. (Or it could be just a mere difference between the two ports of Firefox, who knows? :P)

The Nautilus file explorer, however, DOES scroll with flick gestures on a touchscreen, quite nicely I might add. But it's impossible to click on any files or folders... Weird...

Unity is amazing with the touchscreen, when it *works*. Lol. And Ubuntu actually has some multi-finger gestures for touchscreens that you can do:

-- Three fingers pushed together will reduce a maximized window.
-- Three fingers pulled apart will maximize a window.
-- Four fingers swiped to the right opens the dash (IIRC, this might not be right XD)
-- If you put 3 fingers on an open window then move around, it moves the window.

So there's some basic functionality for touchscreens in there, but from what I can tell playing around with it, its support is only in the beta stage right now.

I heard Fedora has better touch support than Ubuntu, but it crashed before it even booted up on my machine. XDD

Hope I was at least somewhat helpful. Good luck!

---

