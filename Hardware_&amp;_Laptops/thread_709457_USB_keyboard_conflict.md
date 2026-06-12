---
title: "USB keyboard conflict"
date: 2008-02-27
forum: Hardware &amp; Laptops
---

### Post by Foster Grant on 2008-02-27
I recently installed Gutsy on my Gateway MT6451 (1G RAM/120G HD/ATI graphics) and I've noticed a couple of issues. One is the suspend/hibernate problem that nobody seems to have a resolution for other than waiting on the dev team (Go, dev team! Fix those bugs!! RAH RAH SIS BOOM BA! :) )

The other problem is a bit more esoteric.

On my desk at home, I've set up a docking station of sorts with a USB hub that most of my peripherals plug into, including a Logitech wireless keyboard and a Microsoft trackball.

When I start up with the hub plugged into the computer, Linux can't "see" my laptop's built-in keyboard and Synaptic touchpad. The problem does not correct itself when I unplug the USB hub, leaving me with no available input method other than a hard crash and reboot.

When I start up with the hub unplugged, Ubuntu usually has no problem noticing the built-in hardware. When I start with the hub's main cable unplugged and plug it in to the computer after boot and login, I can use the on-board and USB input devices of my choice. This emulates the laptop's performance under Windows Vista, which also "sees" both on-board and USB inputs with no problems.

The USB peripherals work under any circumstances, so long as they're plugged in (obviously). However, if the suspend/hibernate issues are ever solved I'd like to be able to move the computer from my home office, where the docking station is set up, to the living room (for example).

What's causing this driver conflict? Is this an issue I will always have to deal with after installation, or is this something that can be permanently corrected in a settings file after installation?

Thanks for any help y'all can provide.

---

