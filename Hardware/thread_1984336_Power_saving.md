---
title: "Power saving"
date: 2012-05-21
forum: Hardware
---

### Post by hjjfffaa on 2012-05-21
What are ways I can save power on my laptop with 12.04?  I'm using it on my Asus G53 and I only get 1.5 hours in Ubuntu where in W7 I can get 2 to 2.5 hours.  Anything I can enable for more aggressive power saving?  The power settings in Ubuntu are pretty minimal.  Is there something to manage power profiles so I can select them like Windows?

---

### Post by Redblade20XX on 2012-05-22
There are many things you can do in order to make an efficient system.

1) Check and see if you have WOL enabled in the BIOs. This function will continuously drain your battery even if the system is off.

2) Set your screen to the lowest settings. 

3) Disable bluetooth and wifi when not necessary.

4) Look into cpu scaling in which you can underclock the cpu when its idle and save you some more power.

Some of these aspects might be given in Ubuntu through programs but you can always script them (if your up to it, I don't mainly use Ubuntu so this is what I do).

-Red

---

### Post by capsiplexreview99 on 2012-05-22
1. Turn off Wi-Fi and BlueTooth - Most laptops have shortcut keys to instantly disable wireless networking.
2. Don't play computer games, music or DVD movies - Multimedia activities drain laptop batteries.
3. Disconnect all external device like PC Card modems, Firewire, USB devices and optical drives. Use the notebook touchpad instead of an external mouse.
4. Adjust your screen brightness - Dimming your display saves battery power.
5. Tweak Windows Power Options - Choose a Laptop power scheme that turns off the notebook monitor and hard disk after 10 minutes of inactivity.
6. Decrease or mute the Laptop Speaker Volume.
7. Turn off all scheduled tasks.
8. Turn off Auto-save features in Microsoft Office and other applications.
9. If your PC has a built-in wireless card, turn it off or disable it when not in use.
10. Programs that are run from a CD or DVD can be copied to and run from the hard drive, which typically consumes less power than an optical drive.

---

### Post by hjjfffaa on 2012-05-22
> **Redblade20XX said:**
> There are many things you can do in order to make an efficient system.

4) Look into cpu scaling in which you can underclock the cpu when its idle and save you some more power.

-Red
Isn't this supposed to be included with the 3.2 kernel?

---

### Post by Redblade20XX on 2012-05-23
> **hjjfffaa said:**
> Isn't this supposed to be included with the 3.2 kernel?

It has always been there since a long time but requires users to actually set it up, I think. Google it. Ubuntu usually doesn't address stuff like this because it requires too much from the user and the distribution is suppose to be user friendly.

-Red

---

