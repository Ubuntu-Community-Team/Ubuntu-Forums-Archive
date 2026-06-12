---
title: "X61 power usage too high"
date: 2008-05-05
forum: Hardware
---

### Post by tlawson on 2008-05-05
My X61 laptop with a clean install of Hardy is using more power than it should.  Other users have, at various times, reported wattage usages of 8 and under when the system is running lean.

I disable wifi, shut down eth0, the wlan, set the backlight brightness to minimal, disable the usb module, shut off sound, kill most of the running applets, and close EVERYTHING except for a window running powertop.  It reports ~10 wakeups per second, chiefly the kernel reconfiguring interrupts.  The CPU is spending 99.7% of its time in the deepest sleep state.

This nets me a wattage of ~11 watts, usually slightly under, which is not exactly ideal.

The hard drive isn't cycling down very often (hdparm -B 254) because of that nasty load-cycle bug, but even setting it back to hdparm -B 1 only gets me down to ~10 at best.

This is on a 64-bit Hardy install, and I have no idea where the extra power is being used.  Is anybody else getting better power usage on a similar laptop?  What about a comparison with 32-bit?

---

### Post by Rainman4500 on 2008-05-08
I juste installed Hardy on my X61 Tablet
(Cann't get the tablet to work, sucks)

I would like to send you me numbers but I have no clue how, I'm total newbie but I would gladly send you the results if you tell the axact commands to run.

Cheers!

---

### Post by tlawson on 2008-05-08
Are you having trouble with just the stylus, or with rotation?

If it's the first, you just need to add a few lines to /etc/X11/xorg.conf.

I found [this site]("http://www.krizka.net/2007/12/27/thinkpad-x61-tablet-and-ubuntu-hardy-heron/") and [this site]("http://luke.no-ip.org/x60tablet/") helpful for getting these both of these set up.

---

### Post by TheCarNinja on 2008-08-06
Was this ever resolved?

---

### Post by tlawson on 2008-08-31
Nope.  There are various things you can do (such as, if you're crazy, slowing down system fans with tpfand), but I haven't made any significant strides.

---

