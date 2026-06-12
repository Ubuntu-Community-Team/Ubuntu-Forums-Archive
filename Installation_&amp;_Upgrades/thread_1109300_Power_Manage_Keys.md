---
title: "Power Manage Keys"
date: 2009-03-28
forum: Installation &amp; Upgrades
---

### Post by Kirby Johnson on 2009-03-28
First, I am a medium-level Linux user.  (An EE who finally saw the light)  I use two different Hardy 8.04 machines with very similar hardware. The OS was installed from the same CD, and they have identical revision levels. They are both unassuming workaday desktops.  My unique problem is that I use backlit keyboards which have a 'Sleep' key, but no power key.  I assume the sleep key is the standby or suspend key in most instances.

I do not use suspend, so I had gone into gconf-editor and modified the gnome power manager to change the suspend button as it is called, to shutdown.  I was very happy, and it worked great on the first machine.

I did the same on the second machine, but decided to snoop around in the "Preferences" powermanagement to look for a more direct method.  On the general page, there are the two selections for "when the power button... and When the suspend button is pressed".  The power button was set to shutdown, and this was of no concern, since my keyboard does not have a power button.  The suspend button selection was blank though.  Unfortunately, when I clicked the selection arrows the only three options available were hibernate, suspend and Do Nothing.  IE: I could not go back to a blank selection.

This ruined my clever scheme to power off with my suspend key on the keyboard.  Irregardless of how I set the key in Gnome Power Manager, the setting of the power management setting in Preferences overrides it.  Do Nothing disables the suspend key, and hibernate and suspend do those, albeit those two functions are not worth trying to figure out in Linux, and I do not need them.  Not happy to have corrupted one machine, further experimentation likewise disabled my power key scheme on the machine which was up to this point working as wanted.  DUH, how else do you learn?

As we all know, if you are doing anything more than satisfying your curiosity, using Linux is like a FREE car, but then you must build your own motor for it.  In the end you have a work of art which can't be had at any price elsewhere, but there is some effort involved.  

That said:  Short of reinstalling everything on two machines, with the associated tweaks for Wake On Lan, Compix, etc.  etc.  does anybody have a suggestion?  My initial thought was to just go somewhere and intercept the keycode Hex DF for the sleep button, and substitute a hex DE for it.  With Ubuntu, that, unfortunately is beyond my ability at this stage.

I know, buy some grown-up keyboards and quit complaining, right?

---

