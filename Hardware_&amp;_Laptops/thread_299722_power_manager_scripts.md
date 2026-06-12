---
title: "power manager scripts"
date: 2006-11-14
forum: Hardware &amp; Laptops
---

### Post by vmueller on 2006-11-14
I am new to Ubuntu, and I was wondering how to tweak the power saving settings in Edgy.  I'm running a Dell Inspiron 710m.

What I would like to do is be able to modify the "Running on AC" and "Running on Battery" options in the power save settings gui.  Specifically, what I want to do is be able to make the display sleep after 5 minutes of inactivity (instead of the 11 minutes at the left end of the slider bar) when running on batteries.  

Also, I want to be able to control the screen brightness (brighter when running on AC, dimmer when running on batteries).  Inactivity-based brightness levels would be cool too!  I.e. If inactive for 1 minute, dim screen to save power.  When activity is detected, bring screen back to normal brightness.

Are there scripts or config files where I could change or add these settings to my liking?

---

### Post by BitBurner on 2006-11-14
Go to menu:

System: preferences: Power Management

Should be what your looking for :D

---

### Post by vmueller on 2006-11-18
Thanks for the help, but I already knew about the power manager control panel.  My question is how to customize my power management beyond just that control panel.

"Specifically, what I want to do is be able to make the display sleep after 5 minutes of inactivity (instead of the 11 minutes at the left end of the slider bar) when running on batteries."

I also want to know how to incorporate screen dimming into my power management scheme (screen dims after specified period of no use).

I do appreciate you taking the time to reply though.

---

### Post by idlewild on 2006-11-22
Unfortunately gpm does not have this type of control available, it's trying to abide by the gnome philosophy of you get what you're given. If you're really dedicated to the aim you could try modify the source.

---

### Post by davebed on 2006-11-25
does ```
gconf-editor
``` work in Edgy?

It does in Dapper and there are severl advanced option available there (though many don't work on my Dell e1505, though I think there are other power management /ACPI conflicts occuring which I have yet to identify.

Anyhow, if it loads, goto apps / gnome-power-manager and note all the settings in the right-panel that can be adjusted.

---

