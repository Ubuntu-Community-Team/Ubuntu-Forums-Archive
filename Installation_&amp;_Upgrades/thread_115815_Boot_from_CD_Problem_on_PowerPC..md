---
title: "Boot from CD Problem on PowerPC."
date: 2006-01-11
forum: Installation &amp; Upgrades
---

### Post by antroy on 2006-01-11
Hi all,

I have inherited an old Apple iMac G3 500MHz running OSX 10.2
(blue/grey if that is relevant - don't laugh, I've seen the colour
referenced loads in the forums !!), and want to install Ubuntu on it.
I have burned off the ppc version of the installation CD, but cannot
get it to boot from CD.

After trawling the web for ideas, I have tried holding the following
key combinations down during the boot sequence with no success:

1) C
2) Alt
3) CTRL-C (this gives me a boot prompt eventually for the OSX shell)
4) command-opt-shift-del (I haven't even got these keys on the
keyboard, so I tried every feasible combination of control, apple and
alt keys with shift and delete - nothing worked).

Any other ideas?? The mac is next to useless to me at the moment.

--
Ant...

---

### Post by linear on 2006-01-11
Some questions:

How did you burn the CD? (Sure iso was burned as an image? Tried burning at low speed?)
Will the iMac boot off of other CDs?
If you hold down the option key at startup, is the CD recognized as a bootable disk?

---

### Post by antroy on 2006-01-11
Hi linear,

Don't worry, I'm not a complete iso burning dunce - I've burned countless ISO images successfully. I can browse this one just fine in OSX's Finder. I've also tried several other boot CD's (the following in total: Kubuntu Live, Kubuntu Installer, Gentoo Installer) all with the same lack of success.

> If you hold down the option key at startup, is the CD recognized as a 
> bootable disk?

Don't know which the option key is! There isn't one on my keyboard - the only control keys are CTRL, Alt and the Apple key. Any ideas which one would correspond to the Option key? I've tried holding down Alt, and I don't get a menu at all (despite OSX and OS9 both being given as bootable in the Start up disk menu in OSX). I have also tried CTRL and I get a shell prompt.

Thanks for your help!

-- 
Ant...

---

### Post by linear on 2006-01-11
Very strange. Will it boot from an Apple OS X (or OS 9) install disk?

Alt should = Option.

If you're feeling adventurous, you could try the following (from a support article for a different model):

[http://docs.info.apple.com/article.html?artnum=25793](http://docs.info.apple.com/article.html?artnum=25793)

> Restart the computer and hold these keys: Command-Option-O-F . This asks the computer to start in Open Firmware.
Tip: If you don't start in Open Firmware, try again. Make sure you're using a USB keyboard, and that the keyboard is connected directly to one of the computer's USB ports.
type: boot cd:,\\:tbxi
Press Return.

EDIT: Just found that having keyboard directly connected to computer's USB port is important (in case it helps). Also holding down Option to select boot disk (aka Startup Manager) was introduced with the slot-loading iMac G3 and isn't present on earlier models.

---

### Post by antroy on 2006-01-13
[QUOTE=linear]Very strange. Will it boot from an Apple OS X (or OS 9) install disk?
[/QUOTE]

Don't know. I haven't got the installation disks. The Mac is an old teaching machine (thanks to a teacher friend of mine!).

[QUOTE=linear]
Alt should = Option.

If you're feeling adventurous, you could try the following (from a support article for a different model):

[http://docs.info.apple.com/article.html?artnum=25793](http://docs.info.apple.com/article.html?artnum=25793)

EDIT: Just found that having keyboard directly connected to computer's USB port is important (in case it helps). Also holding down Option to select boot disk (aka Startup Manager) was introduced with the slot-loading iMac G3 and isn't present on earlier models.[/QUOTE]

This last thing may have been the problem - I was connected through a USB hub. Actually I held down the 'programmers button' on the side of the machine during boot and got the 'Open Firmware' prompt, but couldn't tyoe anything! Plugged the keyboard directly into the machine and tried again, and could type the voodoo command 'boot cd:,\\:tbxi' and the CD booted up fine!

So thanks for your help - I may be back, because at first run of the Live CD kde refused to boot up - I think the X config wasn't set up right looking at the errors. But then I wasn't really paying attention to the options I was presented with as I was running late for work... Tonight is the night for the install, so I'll see how it goes!

Ant...

---

