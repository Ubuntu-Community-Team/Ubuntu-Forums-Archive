---
title: "Freeze upon resume from suspend - Dell 1545"
date: 2009-01-20
forum: Hardware
---

### Post by jim1964 on 2009-01-20
Here's another freeze upon resume from suspend problem. Using 8.10. System is totally frozen, blank screen with a cursor or sometimes the unlock screen. No keyboard, no touchpad. I can't SSH in. System logs don't show anything of interest. Must do hard reboot to restore. Freezing most of the time but not always. I tried turning off the wireless card but still froze. I don't know how to change graphics driver since that is no longer controlled with xorg.conf. I'm lost. Where can I go now? :(

---

### Post by jim1964 on 2009-01-21
Update - I shut off the powernowd and hotkey-setup services and, so far, have had no problems resuming from a suspend. It appears that the powernowd service will cause my system to freeze when resuming. The hotkey-setup service disables the keyboard when resuming. Of course my CPU's now run at full speed. But that's a price I'm willing to pay for the suspend feature. I haven't yet found the downside to turning off the hotkey-setup service. My volume hotkeys still work. ;)

---

### Post by neighbahood on 2009-02-21
Hey Jim I've had a problem with my system freezing after I leave it locked for a few hours.

I am able to type in my user/pass to unlock and than it shows my desktop backround but nothing else ever loads. I've tried various commands on the keyboard to try to get some thing to pop up but nothing happens. I can only get my laptop working again after I manually power off the system and back on.

I'm using a Dell Latitude D630 running the latest Ubuntu distro 8.10.

Is this the same issue you were experiencing? If it is how do you disable the powernowd as you mentioned?

Any help is appreciated. Thanks

---

### Post by jim1964 on 2009-02-25
> **neighbahood said:**
> Hey Jim I've had a problem with my system freezing after I leave it locked for a few hours.

I am able to type in my user/pass to unlock and than it shows my desktop backround but nothing else ever loads. I've tried various commands on the keyboard to try to get some thing to pop up but nothing happens. I can only get my laptop working again after I manually power off the system and back on.

I'm using a Dell Latitude D630 running the latest Ubuntu distro 8.10.

Is this the same issue you were experiencing? If it is how do you disable the powernowd as you mentioned?

Any help is appreciated. Thanks
Your problem sounds different. Mine would lock up right at the unlock screen.

---

### Post by jim1964 on 2009-02-25
> **jim1964 said:**
> Your problem sounds different. Mine would lock up right at the unlock screen.
You disable powernowd and hotkey-setup from the System/Administration/Services menu.

---

### Post by neighbahood on 2009-02-25
I disabled the screen saver (I think) by just setting the screen saver to blank screen and unchecked the option to turn it on when its idle or locked and I haven't seen the problem since. I'm not sure that I've left it locked for a long enough period of time yet tho cause it did seem like it had to be locked for a while.

We'll see what happens. If I don't see the prob anymore I'll post it.

---

### Post by jim1964 on 2009-03-23
I just installed Jaunty Alpha on my Dell 1545 laptop. The freeze upon resume from suspend appears to have been fixed. I can also dim the screen using the keyboard function keys. :p

---

