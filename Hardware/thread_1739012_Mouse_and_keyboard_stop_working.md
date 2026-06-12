---
title: "Mouse and keyboard stop working"
date: 2011-04-25
forum: Hardware
---

### Post by Easy Does It on 2011-04-25
Hi, I have a desktop PC with an ACER PS/2 keyboard, Labtec USB mouse and keysonic mini wireless keyboard with built-in trackpad, also using usb for the receiver.

I have been having intermittent problems sine 10.4, in 10.10 and now in 11.04 beta.

After random amounts of time after logging on (random being seconds to hours) I gradually lose all input to the computer.  

Usually I lose the trackpad first, often losing the ability to click before the rest goes, although frequently the whole thing stops working.  Then I tend to lose the keyboard part of my wireless keyboard, then the USB mouse, and if I have still not rebooted, the PS/2 keyboard.

Sometimes I lose function of everything at once, sometimes both mice stop registering clicks.

I have searched forums but not found any answers, and have tried doing a clean install but it still happens.

I have tried just having the wired keyboard and mouse, and also just the wireless keyboard, plugged in but it still happens.

I dual boot to windows and have no problems with the keyboards or mice.

Sometimes they die while I am using them, sometimes while they are dormant.  The wireless keyboard often wakes from dormant with no problems, sometimes it doesn't.

I have tried unplugging them and plugging them back in but it does not work, I have to do a hard reset.

On top of this, but possibly unrelated, sometimes it will hang while booting.  This happens just after the grub screen and on 10.10 I would get a black screen with a flashing underscore in the top left, and on 11.04 the screen has a plain purple rectangle.

There seems no pattern to any of this.

Any help would be appreciated.

---

### Post by KegHead on 2011-04-25
Hi!

Very basic;

system..preferences...mouse 7 keyboard.

You might need to reinstall your distro, or have you updated recently?

KegHead

---

### Post by Easy Does It on 2011-04-25
I have just done a clean install of the 11.04 beta, but it was doing the same after a clean install of 10.10, and with all upgrades installed.

Mouse and keyboard work fine until they randomly stop, so what would I be looking for under mouse or keyboard?

---

### Post by quesadilla on 2011-04-25
go to system => administration => update manager. and also see if there are any drivers you might need to install that might make your equipment do weird stuff

---

### Post by KegHead on 2011-04-25
Hi!

I know this sounds weird, but if I don't ground myself when I attach my headphones, my desktop does the same thing.

I'm reaching, but there maybe a short somewhere..

KegHead

---

### Post by feed5000 on 2011-04-25
I had a problem similar to this a few years back. On multiple distributions I would lose input devices and experience system freezes.  I eventually solved it by switching my RAM to different slots. It must have had something to do with dual-channelling and how my motherboard wanted the chips arranged. Maybe this will work for you?

---

### Post by KegHead on 2011-04-25
Hmm,

Try this via terminal

sudo apt-get update

sudo apt-get upgrade -f

sudo apt-get dist-upgrade -f

sudo apt-get install linux-image -f

Restart.

Advise.

KegHead

---

### Post by Easy Does It on 2011-04-26
> **KegHead said:**
> Hi!

I know this sounds weird, but if I don't ground myself when I attach my headphones, my desktop does the same thing.

I'm reaching, but there maybe a short somewhere..

KegHead

You may have hit on something here, KegHead... I have a freezer in this room (I live in a _*small*_ flat) and I think it is giving some interference on the circuit this is on.

Going to try and find a filter for it, see if it makes the difference.  I may be some time...

Thanks for the feedback everyone.  When I can, I will let you know how I get on.

:)

---

### Post by KegHead on 2011-04-26
Hi!

Cool!

Don't forget to upgrade also.

KegHead

---

