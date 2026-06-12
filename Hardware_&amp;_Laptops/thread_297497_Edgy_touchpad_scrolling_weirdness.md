---
title: "Edgy touchpad scrolling weirdness"
date: 2006-11-11
forum: Hardware &amp; Laptops
---

### Post by coffeecat on 2006-11-11
There've been a number of threads started by people who have experienced a variety of laptop touchpad problems in Edgy which they didn't have in Dapper. I've just discovered something very strange with Edgy on my Sony Vaio. This is not a plea for help - merely information that might be useful to someone else.

When I first boot up, neither horizontal nor vertical touchpad scrolling works - but it does on the same machine in Dapper (which I've retained on a separate partition). Otherwise the touchpad (as well as a usb mouse) works fine. The relevant section in xorg.conf is identical in Dapper and Edgy, viz:

```
Section "InputDevice"
    Identifier    "Synaptics Touchpad"
    Driver        "synaptics"
    Option        "SendCoreEvents"    "true"
    Option        "Device"        "/dev/psaux"
    Option        "Protocol"        "auto-dev"
    Option        "HorizScrollDelta"    "0"
EndSection
```I've tried adjusting the HorizScrollDelta value and adding a VertScrollDelta line and that doesn't help. But I discovered that if I restart the xserver with ctrl-alt-backspace, scrolling then works fine. Yes, that's right. On first booting up scrolling doesn't work, but does if I restart X. :?

Only trouble is, the logout button on the top panel then moves to the left of the clock and can't be moved unless I reboot, but then scrolling won't work. :) Oh, and Edgy won't boot if the power is plugged in - Dapper doesn't mind. And I haven't yet managed to get the Fn keys working with the howto I used in Dapper. :(

Well - it is 'edgy', isn't it?

Now feel free to talk among yourselves. :wink:

---

### Post by jrb114 on 2006-12-20
Just to let you know, I've got this problem too on a Sony Vaio (FS-305, I think).

I prefer to disable tapping on the touchpad, but this wasn't working until I did a control-alt-backspace. Then scrolling works, and tapping dies. Weird.

---

### Post by coffeecat on 2006-12-20
Thanks for responding. Apparently there's a bug - there's been some other threads about this on other makes of laptop and logging out and in again (or ctrl-alt-backspace) is the only way to get scrolling to work.

I've managed to get the Fn keys working, but it still won't boot up if I have the power cord in. For these reasons I'm still using Dapper most of the time on this multi-booting laptop and will probably continue to do so until Feisty is released. I just hope that Feisty won't have these issues.

**Edit:** Just to add - unlike on your machine tapping still works on mine after restarting X, which suits me - but odd nonetheless :-k

---

### Post by spier on 2006-12-20
Scrolling just work with dapper. 

With Edgy, it starts working as expected  after a fresh boot, but after a wake up it stops working. At this point, Ihave to Ctrl+alt+Backspace to bring it to life again. Odd... and annoying. 

Btw, Vaio FS740 here, and still searching.

---

### Post by sebos69 on 2006-12-20
you can also switch between terminals (CTRL+ALT+F1 then CTRL+ALT+F7).... faster than killing X...

---

### Post by coffeecat on 2006-12-21
> **sebos69 said:**
> you can also switch between terminals (CTRL+ALT+F1 then CTRL+ALT+F7).... faster than killing X...

I'll try that - thanks.

I've noticed something else that may explain the various problems people have with the touchpad in Edgy but not in Dapper. In Edgy there is a definite hesitation in mouse cursor response when one operates the touchpad for the first time after the Xserver starts up - also for the first time. It's as though mouse/touchpad initialisation doesn't happen until the touchpad is used. If you logout and login or ctrl-alt-backspace (and, I presume, ctrl-alt-F1 > ctrl-alt-F7) this hesitation doesn't occur. I haven't noticed this oddity in Dapper.

There's a different bootup initialisation in Edgy. I wonder if this is something to do with it.

---

### Post by eitan_a on 2007-01-01
I have the same problem..

Is there an easy way to revert back to 6.06?  This is one bug that just "bugs" me, hehe.  that, or someone convince the ubuntu admins to fix it already??  Since no one listens to me on these forums or in their irc channel..

---

