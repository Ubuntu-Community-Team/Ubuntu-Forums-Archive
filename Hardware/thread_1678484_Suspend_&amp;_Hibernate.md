---
title: "Suspend &amp; Hibernate"
date: 2011-01-30
forum: Hardware
---

### Post by kistenman on 2011-01-30
I have 10.10 on one pc and a couple of laptops.  Pc works ok one laptop work ok but the old IBM A31
has a problem with suspend and hibernate. It will enter both but will not come out have to do a hard boot to get going again.  Any advise would be appreciated.

---

### Post by SaintDanBert on 2011-01-30
**Suspend** (which I call "sleep") is actually suspend-to-ram.
**Hibernate** is actually suspend-to-disk.

Both are troublesome for all sorts of reasons -- some hardware, some software (grin) some arcane magic. There may be no solution for some, especially older, hardware.

One item of magic involves the use of a swap partition -- **partition** not file. The partition must be larger than your total physical RAM because the suspend-to processing copies all of ram to the swap partition.

When I say "larger than" I mean that you need swap space for every byte of RAM and then some additional space for administrative details. Sorry, but I have not found an exact value or formula.
[indent]
COMMENTARY-- Since this is a "requirement" one would think that the installers would sort this out and recommend a minimum swap partition size that satisfies the space needs. That has not been my experience. Also, there is evidence that once one has some amount of RAM, linux rarely if ever uses swap space so folks with ram-rich machines can run fine without any configured swap ... but then suspend-to doesn't work.
[/indent]

Another trouble spot involves USB connected devices in general and some in specific. In addition, some video and network parts present specific troubles.

First, unmount any USB connected "disk drives" before you suspend-to.
Second, unload the drivers (kernel modules) for **usb_storage** and your video and network parts before you suspend-to.

There are other threads that will explain how to configure so that all of this happens automatically. (If you have trouble sorting this, post again or PM.)

On resume-from, all of that hardware powers up, the kernel notices the hardware and creates the corresponding devices then loads the associated kernel modules. This re-activates the devices that you unloaded during suspend-to.

Having said and done all of this, you might still have troubles ... I do. I have two identical laptops. Both will suspend-to-ram and resume. One will suspend-to-disk and resume. The other will not. I have spent hours trying to discover why without success. It will be something silly when I find it, but until then ... sigh!

Bonne chance,
~~~ 0;-Dan

---

### Post by kistenman on 2011-02-01
I tried the USB thing did not work.  Am still working on it but no luck at this time.  If you solve the problem please advise.  Thank for your help.

---

### Post by SaintDanBert on 2011-02-01
Sadly there is not **one problem** to solve...

At the top level there are four situations:
[list]
[*] "suspend" (suspend-to-ram)
[*] "resume" after suspend-to-ram
[*] "hibernate" (suspend-to-disk)
[*] "thaw" after suspend-to-ram
[/list]
The words in quotes are the event names used in the /etc/pm/sleep.d/* scripts and reflected in the /var/log/*pm* logfiles.

Below this top level, there are details for every device, its driver(s), and services your box is running. Known culprits include video, displays, wifi networking, other networking, and anything USB connected.

During "suspend" many laptops have some sort of LED to show that the power remains on.  During "hibernate" power is off. When you request either, do you get to the respective situation?

There is a configuration option that says, "... Lock the desktop on resume ..." I prefer to have this enabled. Sadly, I don't remember where it is -- either "power management" or "gnome config" I think.

When you "resume" -- regardless of which -- you should get the locked desktop. When you unlock the desktop, you should have whatever you were doing near where you left off. There are a couple of exceptions.
[list]
[*]X11 is known to do funny things on resume. This depends on your video hardware and Lord knows what else.
[*]Networking in known to struggle -- especially wifi. This also depends on your hardware and its drivers.
[*]If you have usb-connected drives, the default behavior happens so you may have a screen filled with open folders, music players, photo galleries and similar based on how things are configured.
[/list]
Remember, "hibernate" saves everything and then does a real shutdown. On "resume" from "hibernate", your box begins a normal startup and then decides "Oh, I need to use whatever I saved." All of your devices will have done a hard reset during the power-off-then-on cycle. The devil lies in coordination between a cold device restart and the "what was I doing before" hardware and software state.

I would focus on getting "suspend" (what I call "sleep") to work first because your devices stay power-on and idle before and after. Once that is working, you can tinker with "hibernate" I must warn you that your efforts might never bear fruit given your hardware and its drivers.
I've been chasing resume from hibernate for almost a year. (sigh)

Bonne chance,
~~~ 0;-Dan

---

### Post by pi/roman on 2011-02-01
You could try to spam the keyboard shortcuts with your function key that affect your screen and see if that will knock it out of sleep mode.  If you have a dim/brighten screen shortcut or video output shortcut try hitting it repeatedly and see what happens.

---

