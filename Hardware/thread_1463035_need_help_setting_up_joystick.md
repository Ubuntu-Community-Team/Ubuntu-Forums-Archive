---
title: "need help setting up joystick"
date: 2010-04-26
forum: Hardware
---

### Post by Crash Dummy Dave on 2010-04-26
I am using Ubuntu Hardy, kernel version 2.6.24-27.68. I have disabled onboard sound in bios and installed a cmi8738 sound card which is working properly and is the only sound card recognized by my system. I need to know how to enable the joystick port which is disabled by default.

Info listed at another website about setting up joysticks for sound cards (not usb) gives this:

driver: cmipci
module options: joystick_port
available values: 0 = disable (default), 1 = auto-detect, manual: any address (e.g. 0x200)

This site also states that this driver supports the joystick natively, whatever that means.

How do I do this? No real step by step instructions have been given to me, and that is what I need. I also wonder if there is a way to keep this setup permanent and survive kernel upgrades?

In terminal lsmod shows at least these modules loaded that seemed pertinent:
snd_cmipci             38528  3 
gameport               16008  1 snd_cmipci
soundcore               8800  1 snd

I haven't been able to get any modprobe commands to do anything. It seems maybe I have to get the joystick enabled on the card first and restart the system with the joystick connected?

One of my joysticks is an Interact Raider Pro P-210, but I have others I want to try. Thanks for any help.

---

