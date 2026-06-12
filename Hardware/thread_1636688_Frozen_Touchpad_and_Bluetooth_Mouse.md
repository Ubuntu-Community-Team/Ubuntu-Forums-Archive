---
title: "Frozen Touchpad and Bluetooth Mouse"
date: 2010-12-03
forum: Hardware
---

### Post by Kixtosh on 2010-12-03
I currently have two installations of Lucid Lynx 10.04.

- Toshiba Portégé R205
- Toshiba Portégé R500

The first installation is fine, but on the R500, after a few days of use, the touchpad and bluetooth mouse just froze up. At first, a reboot would sometimes fix the problem, but now, rebooting changes nothing.

In an attempt to troubleshoot, I removed the bluetooth mouse device, and tried to install it fresh, but it is not connecting at all (it does not show up when I try to pair with a new device).

The only thing that I have been able to do is plug in a USB mouse (not bluetooth), and that is now working.

What can I do to get the touchpad and bluetooth mouse working again?

A Bluetooth mouse and touchpad work normally on the other laptop, the R205 model, also using Lucid Lynx.

---

### Post by Kixtosh on 2010-12-04
Forty-three views in twenty-four hours but no good ideas? Well, I figured it out! There were two things going on:

**1) Firstly, for the touchpad: **I realized it wasn't working in Vista either, so I used the Fn + F9 hotkey sequence to turn it on normally, and then rebooted to start Ubuntu, and it was working again. Oops!

I don't really expect to use Vista, so I hadn't remembered ever turning off the touchpad. The hotkey sequence for the touchpad is one of the few Fn hotkey functions that do not work out of the box in Ubuntu. I'm not sure if they can be enabled or not with some tweaking, but all the important ones already work, so I had not bothered to investigate this one yet.

To **troubleshoot the touchpad**, if you have a dual boot environment, always chTo **troubleshoot your wireless bluetooth mouse**, always try a new set of batteries just in case it's just as silly as that!To **troubleshoot your wireless bluetooth mouse**, always try a new set of batteries just in case it's just as silly as that!eck that you did not turn it off by accident in Windows.

**2) Secondly, for the bluetooth mouse: **This is embarrassing. This turned out to be an unrelated issue to the touchpad. By mere coincidence, the battery was strong enough to turn on the indicator light so that I thought it should be working normally, but not strong enough to operate properly. I changed the battery, and it started working again.

To **troubleshoot your wireless bluetooth mouse**, always try a new set of batteries just in case it's just as silly as that!

I hope this may help anyone else having issues.

---

