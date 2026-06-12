---
title: "Laptop Keyboard not working after Jaunty install"
date: 2009-05-03
forum: Installation &amp; Upgrades
---

### Post by gcrussell1 on 2009-05-03
Problem: My Laptop keyboard doesn't work after installing Ubuntu Jaunty 64-bit. This is the case in the Grub Loader, Ubuntu, and Vista Home Premium.

History: Computer has never been used for anything but Vista 32-bit. I installed Jaunty 64-bit a few days ago and the built-in keyboard was working fine (but my old Logitech Cordless Elite was used for the installation). Since then, the laptop's keyboard hasn't registered any touches, and the media keys along the upper strip (not part of the keyboard) don't seem to be registering either. The touchpad works fine - scrolls, taps, etc, but not the keyboard. This is especially problematic because A) my Logitech keyboard is 6 years old and bugs out occasionally so I need the built-in keyboard at those times and B) I don't always have the Logitech plugged in anyway - i.e. away from home.

Specs: Dell Inspiron 4200, T7500, 8400M GT, 3 GB RAM, 250 GB HD w/ approx 85 GB free, any other specs on request.

Needless to say, this is pretty bad, I could really use some help with this one.

---

### Post by tommcd on 2009-05-03
The easiest way to fix this is to reinstall Ubuntu using the laptop keyboard without the logitech keyboard attached. This will almost certainly setup you laptop keyboard just fine. Always install with the hardware that you actually plan to use.

---

### Post by gcrussell1 on 2009-05-03
> **tommcd said:**
> The easiest way to fix this is to reinstall Ubuntu using the laptop keyboard without the logitech keyboard attached. This will almost certainly setup you laptop keyboard just fine. Always install with the hardware that you actually plan to use.

I would love to try something like that, the problem is that the laptop keyboard is not working - i.e. booting the computer without the Logitech Keyboard = booting a computer without any working keyboard. If it hadn't been working five minutes before I installed Ubuntu, or if it had waited a couple days, or even a couple hours after installing Ubuntu, to fail, I would suspect hardware issues, but it happened right as I installed Ubuntu, and it's affecting the computer from bootup. Does anybody know of any possible solutions to this, or has anyone else experienced this before?

Edit: I checked the connection from the built-in keyboard to the MoBo. I'm no expert on those ribbon thingies, but I think it's connected just fine. Anyway, the bottom line on that front is that it was working fine, and then it wasn't.

---

### Post by tommcd on 2009-05-03
I noticed you are in China.
When booting the Ubuntu install CD, be sure to choose the correct keyboard layout for your keyboard. If you are using some type of international keyboard layout you will have to select the keyboard layout that works for you.
How is the logitech keyboard different from the laptop keyboard?

---

### Post by gcrussell1 on 2009-05-03
It's a US laptop, with the correct installation parameters (regarding the keyboard). The Logitech keyboard is also US, albeit bigger, with a numpad and a few extra media/browsing keys. Most significantly, it's connected via a USB wireless receiver rather than the direct-to-Mobo ribbon thingy.

---

### Post by tommcd on 2009-05-03
Try running:
```
sudo dpkg-reconfigure console-setup
```
then reboot and see if your keyboard works. Of course, this assumes you have a working keyboard. Perhaps you could copy & paste the command with the mouse if the keyboard is not working.
See the section "xorg input devices" from the Intrepid release notes:
[http://www.ubuntu.com/getubuntu/releasenotes/810](http://www.ubuntu.com/getubuntu/releasenotes/810)
This should still apply to Jaunty also.

---

### Post by gcrussell1 on 2009-05-06
Here's an update: I have updated the bios, completely removed Ubuntu, extended the Vista partition, fixed the master boot record, etc. I suppose this ceases to be an Ubuntu issue here, but it's still possible that someone here can help me, and it did begin as an Ubuntu issue.

Now, the current state of things: The keyboard still doesn't work as it should, but the computer clearly recognizes the button presses on some level. When I have booted up the computer lately (since installing Ubuntu), it beeps at me after the BIOS loads. Tapping any key on the built-in keyboard stops this beeping, which makes it clear that the key-presses are seen by the motherboard. I've already flashed the BIOS, what else can I do to get this keyboard working?

---

### Post by tommcd on 2009-05-07
If the keyboard still does not work properly in Vista after removing Ubuntu, then I would assume you have a hardware problem.

---

