---
title: "Dell Fn-f2 - Is there any way to know if the wi-fi radio is on or off?"
date: 2006-12-12
forum: Hardware &amp; Laptops
---

### Post by David Mulligan on 2006-12-12
On Dell laptops, at least the Latitude series, Fn-f2 is used to turn on and off the wi-fi radio.  With Edgy installed on my Dell Latitude D600 the radio does indeed toggle on and off when I press Fn-f2 but I see no way of knowing if the radio is on or not.  In Windows there is a tool tray icon telling you that wifi is enabled or not.

In the logs I see:
```
atkbd.c: Unknown key pressed (translated set 2, code 0x88 on isa0060/serio0).
atkbd.c: Use 'setkeycodes e008 <keycode>' to make it known.
```
whenever I hit the keys.  Is there a way to ask the driver every time those keys are hit and update a panel icon? (or whatever the linux analog of tooltray icon is)

The D600 I has a bcm4309 (bcm43xx) based wireless card.

Thanks,
David

---

### Post by Scheater5 on 2006-12-12
This seems to be a problem with Dell laptops.  Mine does the same thing - from what I can tell, the only way to get it to do that is custom compile a kernel, which comes with a whole host of problems.  If you manage your wireless from an application like Wi-Fi Radar, then you can tell if you know you have a good wireless signal in range.  Load up Wi-Fi radar if you're radar is on, then you'll see the signal.  hit Fn-f2 and it will quickly go to no signal and the bars turn gray.  Hit Fn-f2 again and soon the signal bars will reappear.

---

### Post by David Mulligan on 2006-12-12
Why does it appear to be a Dell/kernel issue?  Does linux have a way to report of other types of laptops have their radio enabled?

Thanks,
David

---

### Post by Scheater5 on 2006-12-12
That's a question I don't have an answer to - but I can surmise from what I know about how kernels work.  The wireless radio is treated as a basic component - spoken to directly by the kernel (I'm sure I'm using analogy as opposed to technical terms, and I'm not even sure I'm correct - take this with a grain of salt).  Did you notice that the light that reflects the radar's status worked in Windows, regardless of what program you had running?  You could turn Windows Zero Configuration off and it still worked.  That leads me to believe it's controled directly by the kernel.  And for some reason on Dell laptops it doesn't work out of the box - I can't speak for the status of other laptops

---

### Post by David Mulligan on 2006-12-12
Ahh the D600 has no such light.  Because of that I am looking for an on screen widget or whatever to tell me if the radio is enabled or not.  It is partially security and partially for power conservation.

---

### Post by David Mulligan on 2006-12-12
There has been a bug logged about this.  Or something like this. [https://launchpad.net/distros/ubuntu/+source/network-manager/+bug/63728](https://launchpad.net/distros/ubuntu/+source/network-manager/+bug/63728)

Also according to /etc/acpi/wireless.sh there is a file called power/state that is supposed to be updated.  I guess it is not mine always seems to be 0 regardless of whether it is on of off.  If that is really supposed to be updated then it could be watched.

---

### Post by Scheater5 on 2006-12-13
I know of no such widget - if you find one let me know!  But if you use Ubuntu (as opposed to KDE or XFCE) then you'll notice an icon in the tray for network connections.  If that's set to wireless then it will be showing activity if your radar is on - even if there are no signals in sight it will periodically show activity searching for signals.  If it's off, it still remain blank.

---

