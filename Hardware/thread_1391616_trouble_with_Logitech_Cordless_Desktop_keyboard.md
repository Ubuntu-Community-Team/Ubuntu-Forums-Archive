---
title: "trouble with Logitech Cordless Desktop keyboard"
date: 2010-01-27
forum: Hardware
---

### Post by Craig P on 2010-01-27
I selected a Logitech Cordless Desktop Comfort Laser because I read that it was compatible, even plug and play, with Jaunty and Ibex. It is a keyboard and mouse combo, which use the PS/2 ports when available. The mouse works fine, but the keyboard not at all. They both appear to be communicating with the receiver just fine. I tried re-booting and tried all the relevant Logitech keyboards using the GUI System/Preferences/keyboard/layout. Below you will see what was logged on dmesg the last time I plugged them in and tested them.

Strangely, it looks like two different Logitech mice (unknown 127 and Explorer) are identified, and doesn't seem to register any keyboards, only unknown keystrokes.

Any ideas? I'm a relative newbie, using Jaunty 9.04, with AMD 64x2 dual core processor.

[20656.573784] logips2pp: Detected unknown logitech mouse model 127
[20657.117347] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[20657.624202] logips2pp: Detected unknown logitech mouse model 127
[20658.093087] input: ImExPS/2 Logitech Explorer Mouse as /devices/platform/i8042/serio1/input/input6
[20706.919622] atkbd.c: Unknown key pressed (translated set 2, code 0xf6 on isa0060/serio0).
[20706.919630] atkbd.c: Use 'setkeycodes e076 <keycode>' to make it known.
[20707.165941] atkbd.c: Unknown key released (translated set 2, code 0xf6 on isa0060/serio0).
[20707.165949] atkbd.c: Use 'setkeycodes e076 <keycode>' to make it known.
[20707.803440] atkbd.c: Unknown key pressed (translated set 2, code 0xf6 on isa0060/serio0).

---

### Post by djchandler on 2010-01-27
> **Craig P said:**
> 
Any ideas? I'm a relative newbie, using Jaunty 9.04, with AMD 64x2 dual core processor.

[20656.573784] logips2pp: Detected unknown logitech mouse model 127
[20657.117347] **synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume**
[20657.624202] logips2pp: Detected unknown logitech mouse model 127
[20658.093087] input: ImExPS/2 Logitech Explorer Mouse as /devices/platform/i8042/serio1/input/input6
[20706.919622] atkbd.c: Unknown key pressed (translated set 2, code 0xf6 on isa0060/serio0).
[20706.919630] atkbd.c: Use 'setkeycodes e076 <keycode>' to make it known.
[20707.165941] atkbd.c: Unknown key released (translated set 2, code 0xf6 on isa0060/serio0).
[20707.165949] atkbd.c: Use 'setkeycodes e076 <keycode>' to make it known.
[20707.803440] atkbd.c: Unknown key pressed (translated set 2, code 0xf6 on isa0060/serio0).

Is this a laptop with a single PS/2 port?

Do you have both the Logitech external mouse and its matching keyboard plugged into that port with a y adapter?

Please post the file I put in bold type in your quote included in my answer. Also post more information on your computer. With the Synaptics mouse pad and a built-in keyboard, you may be having two keyboards trying to input. What happens if you type on the laptop keyboard?

---

### Post by Craig P on 2010-01-28
Thanks, djchandler. I'm using a desktop with two PS/2 ports, one for a keyboard and one for a mouse, and have the mouse and keyboard outputs from the receiver plugged into them. Before I can do this, I naturally have to unplug the old hardwired keyboard and mouse. Could this be the cause of the message ***synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume***? I'm sorry, but I'm not sure what you mean when you asked me to post that file. Let me know, along with any other info about my computer you need, and I'll post them right away.

When I was installing Jaunty yesterday, I got a message: *"Debconf on craig-desktop, configuring console-setup at /etc/default....console-setup. Keyboard layout not supported by config program. So current config will be preserved."* At that time, I still had the old keyboard plugged in.

---

### Post by djchandler on 2010-01-30
> **Craig P said:**
> Thanks, djchandler. I'm using a desktop with two PS/2 ports, one for a keyboard and one for a mouse, and have the mouse and keyboard outputs from the receiver plugged into them. Before I can do this, I naturally have to unplug the old hardwired keyboard and mouse. Could this be the cause of the message ***synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume***.... At that time, I still had the old keyboard plugged in.

Forget what I asked about retrieving and supplying a file for now, and let's concentrate purely on hardware for now.

The i8042 is the keyboard controller. Either it is perceiving your keyboard as a mouse or you may have the ports accidentally switched. The other possibility is the receiver is defective, maybe as simply as the color coded plugs being switched. I don't think it would hurt a thing to power down, switch the two PS/2 plugs, and try this again just for grins.

What also grabbed my attention is the message referring to synaptics. A lot of laptops have a synaptics touchpad, so that's what caused me to leap to the conclusion you were on a laptop.

So are you saying you had both keyboards plugged in simultaneously on a desktop computer? I don't think the keyboard decoder on a desktop motherboard is configured to accept input from two different keyboards. Was the old "wireed" keyboard plugged in via the USB bus? This is what has me confused.

I have an older Logitech mouse/keyboard combination running just fine on Karmic. My receiver has a USB port and a PS/2 port on it, along with an adapter to convert the USB mouse plug to PS/2 in case you have two PS/2 ports as you now are telling me you do.

Sorry I took so long to get back to you. I got caught up in another issue where we had someone posting links to possibly malicious code and got sidetracked.

---

### Post by efflandt on 2010-01-31
I had a Logitech wireless keyboard and mouse many years ago, and seem to remember it having reversed keyboard and mouse PS/2 plugs.  So I marked them K and M with a Sharpie (permanent marker).  But I have not used it for years because it did not transmit  certain 3 key combinations used by Quake or Quake II (haven't done that for a while).

I currently have a Logitech diNovo Edge Bluetooth keyboard/mousepad and it definitely works out of the box with its included USB BT dongle (including CMOS setup or BIOS password).  It can be hot plugged and works simultaniously with laptop keyboard/mousepad or wired keyboard/mouse.  It does not have numeric keypad, but it is a nice size for connecting PC/laptop to HDTV and sitting back in your easy chair with keyboard/mousepad.  Its volume control automatically works with gnome and it has li-ion battery.

---

### Post by Craig P on 2010-01-31
Thanks djchandler and efflandt. I tried switching the mouse and keyboard outputs from the dongle, as you both suggested, but still only the mouse worked. I tried twice, and each time tried rebooting, and still only the mouse worked. For good measure, I also tried using the usb connector only, and still only the mouse worked. So I don't think this is the problem. I have never tried hooking up both keyboards. Each time I reboot with the wireless one installed, I can't log in (no working keyboard), so I unplug it and plug in the hardwired one. I've put other new batteries in the keyboard, and it still communicates with the dongle/receiver fine.

I searched for i8042; my computer only has a small file called i8042.h. 
Would it help if I posted it?

Or what about reconfiguring the xserver (or x11)? Given what you saw in my dmesg, would it work to go through all the keyboard set up etc.?

Thanks again for any help you can provide,
Craig

---

