---
title: "Aspire Switch 11 - specific touchpad quirk."
date: 2015-07-03
forum: Hardware
---

### Post by halfnote52 on 2015-07-03
Okay, I have just about finished tweaking Xubuntu 15.04 on my new Acer Aspire Switch 11  (SW5-171).  (this is a hybrid tablet/laptop with a Intel Core i5 64-bit processor.)

After installing the hid-acer snap-on keyboard patch from github, updating the greeter so it takes input from onboard, making a script to modprobe the inputs after resume from suspend, and messing about with themes that make it easier to use in tablet-mode, it's is almost PERFECT!

HOWEVER!  The touchpad has a quirk. 

If you **boot the computer WITHOUT the snap-on keyboard on**, and then attach it after it's booted, **it's** **fine**. You an detach an re-attach it as many times as you'd like. 

If you boot the computer WITH the snap-on keyboard/touchpad attached, it **still works fine. Until you remove it. ** When you re-attach it, the keyboard comes back, and the touchpad BUTTONS work, but the pad itself doesn't move the mouse cursor. 

The workaround is, of course, to be sure you fire the thing up with the keyboard separated, but it's be nice not to have to worry about it. 

Any ideas?

**EDIT:  OH! One more thing, after the touchpad stops working, running synclient yields NOTHING. I don't mean the fields are blank, I mean there ARE NO fields. I am guessing that if you leave it plugged in on boot, a different driver loads than when it's detected after boot, but I dunno why that'd be.**

[SIZE=1]Also, when I get finished playing with it, I'm going to use systemback and make a liveboot iso for backup. Anyone who doesn't particularly feel like messing with all of this themselves, provided you don't mind the thing is going to be heavily customized to my tastes right off the bat, is welcome to have a copy. [/SIZE]

---

### Post by chris-m-greenman on 2015-09-09
I'm curious, I've noticed the same issue with with my Sw5-171 but I also have noticed a other issue.   After a while the mouse pointer starts randomly going up and down and registers a right button click.   Sometimes it stops but other times the only fix is a reboot.   Do you see this behavior as well?

---

### Post by chris-m-greenman on 2015-09-14
I'm curious, I've noticed the same issue with with my Sw5-171 but I also have noticed a other issue.   After a while the mouse pointer starts randomly going up and down and registers a right button click.   Sometimes it stops but other times the only fix is a reboot.   Do you see this behavior as well?

---

### Post by vasjapupkin on 2016-01-15
I'm running Debian on the same machine with 3.18 kernel. It required to compile acer-hid module, as described here: [https://gist.github.com/franga2000/2154d09f864894b8fe84](https://gist.github.com/franga2000/2154d09f864894b8fe84) and runs ok after that. The only thing is that I don't know, how to produce right click with the touchpad. Unfortunately, it produces it only when held pushed for a while.

---

