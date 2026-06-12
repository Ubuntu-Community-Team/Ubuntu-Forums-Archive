---
title: "Lenovo Yoga 900 vs. ThinkPad Yoga X1"
date: 2016-01-07
forum: Hardware
---

### Post by shuukazedojo on 2016-01-07
Hello. I'm considering the purchase of a new Lenovo laptop and have it narrowed down to either the Yoga 900 or the ThinkPad Yoga X1. I've been reading about some of the primary issues people are having with the Yoga 900, but because the TP Yoga X1 is newer, I haven't been able to find much on user experience. My hope is that some of the great people on this forum will be able to consider the specs of each system and offer thoughts on potential issues/compatibility. 

The Yoga 900 seems like a safer bet with more user experience and guidance for common issues. However, I understand the ThinkPad to have an historically good relationship with Ubuntu and am curious if others expect the TP Yoga X1 to perform well. Further, is it unreasonable to expect the included stylus to work in Ubuntu or is this a pretty easy function to get working?

Thank you all in advance for your thoughts and responses.

---

### Post by davidm2 on 2016-01-26
> **shuukazedojo said:**
> Hello. I'm considering the purchase of a new Lenovo laptop and have it narrowed down to either the Yoga 900 or the ThinkPad Yoga X1. I've been reading about some of the primary issues people are having with the Yoga 900, but because the TP Yoga X1 is newer, I haven't been able to find much on user experience. My hope is that some of the great people on this forum will be able to consider the specs of each system and offer thoughts on potential issues/compatibility. 

The Yoga 900 seems like a safer bet with more user experience and guidance for common issues. However, I understand the ThinkPad to have an historically good relationship with Ubuntu and am curious if others expect the TP Yoga X1 to perform well. Further, is it unreasonable to expect the included stylus to work in Ubuntu or is this a pretty easy function to get working?

Thank you all in advance for your thoughts and responses.

I'd like to know as well. I've ordered the X1 Yoga "on faith," noting people do have the Yoga 260 working with some command line boot parameters [http://askubuntu.com/questions/723166/cant-install-ubuntu-on-new-skylake-ultrabook-thinkpad-yoga-260](http://askubuntu.com/questions/723166/cant-install-ubuntu-on-new-skylake-ultrabook-thinkpad-yoga-260).

---

### Post by philip33 on 2016-02-04
Used lenovo yoga 900 for a week now, updated to kernel 4.5 and everything works fine! I was choosing between Yoga 900 and Dell XPS 13, but choosed lenovo for it's 2 in 1 and slimness. Working as a developer

---

### Post by derek41 on 2016-02-05
I successfully installed 15.10 Desktop on the X1 Yoga after much suffering. The boot option that worked for me was "intel_pstate=disable".
"acpi=off" also worked for booting but restart / shutdown didn't work - it would just seemingly hang on the shutdown splash screen.

The wireless network adapter was only recognized after upgrading the kernel to 4.4.1-040401 by following [COLOR=#000000][FONT=arial][this procedure]("http://askubuntu.com/questions/119080/how-to-update-kernel-to-the-latest-mainline-version-without-any-distro-upgrade/142000#142000").

[/FONT][/COLOR]I haven't had a chance to put it through its paces but the machine boots and is usable.
[COLOR=#000000][FONT=arial]
[/FONT][/COLOR]

---

### Post by mkfs on 2016-02-29
> **derek41 said:**
> I successfully installed 15.10 Desktop on the X1 Yoga after much suffering.

Any luck with the touchscreen? That is the only remaining hurdle for my Debian install. 

Quick summary: upgrade to kernel 4.4.3 (actually 4.2 and up) and upgrade the iwlwifi firmware to get wifi working. Had to upgrade X intel video driver as well, but this may not be required in Ubuntu. The 4.x kernel has a p-state bug for this CPU, so the kernel parameter 'intel_pstate=no_hwp' is necessary (disable also works, but is less fine-grained). ACPI works just fine, both suspend and hibernate. Sound works. All that stuff.

Everything but the touchscreen. The kernel module recognizes it, the X server recognizes it, xinput displays it, "xsetwacom --list" displays it, the window manager (XFCE) allows it to be configured, but the touchscreen does not respond to touch or stylus (except in windows, of course). The X log shows something odd when using Option "DebugLevel" "12" : the eraser is detected, and passed INIT, ON, and then OFF. The other devices (Pen, Touch) are only passed OFF. After that, no debug messages appear. Using evemu, with X stopped (via "/etc/init.d/lightdm stop"), no events are captured.

In other words, detected and initialized but not functional. Same thing happen for you?

UPDATE: Touchscreen works after firmware update (and hard-reset). See [https://forums.lenovo.com/t5/ThinkPad-X-Series-Laptops/X1-Yoga-Touch-Screen-No-Longer-Working/td-p/2269132](https://forums.lenovo.com/t5/ThinkPad-X-Series-Laptops/X1-Yoga-Touch-Screen-No-Longer-Working/td-p/2269132) for the firmware discussion.

---

