---
title: "Keyboard issue: Gnome &amp; X System Settings Differ"
date: 2007-04-09
forum: Hardware &amp; Laptops
---

### Post by wyth on 2007-04-09
Lately, whenever I boot up my laptop, I'm getting the following error:

> The X system keyboard settings differ from your current GNOME keyboard settings.

Expected was model "pc101", layout "us" and no options, but the the following settings were found: model "pc104", layout "us" and option "lv3    lv3:ralt_switch".

Which set would you like to use?

I've never seen this before, and am not exactly sure what it means.  I assume it's an xorg.conf issue; it (correctly) has my keyboard as pc104.

Any thoughts on this?

---

### Post by mssever on 2007-04-10
I got that on my desktop after upgrading to Edgy (but not immediately after, I don't think). It didn't seem to matter which option I chose, so I just checked the box to tell it not to complain again. After checking the box (I don't remember which option I chose), the keyboard shortcut for the keyboard language switcher applet thingy got changed. But that was simple enough to restore.

---

### Post by voided3 on 2007-10-29
I get this dialog every time on startup with gutsy, and no matter which I select, it keeps coming up on boot. Any suggestions?

---

### Post by jsully1 on 2007-10-30
Commenting out the single line (# Option         "XkbLayout" "us") in my xorg.conf fixed this issue.

---

### Post by ullal on 2007-11-01
I do not think that commenting out the option in xorg.conf, as suggested by jsully1,  is the solution. I have the same problem and my message states the following:
Expected: model "generic" layout "us" and no options
Found:      model "pc105" layout "de" and no options
Please note that my keyboard is a Generic 105-key (intl) PC keyboard, as seen and set under System-> Preferences->Keyboard->Layouts.

I commented out the line Option "XkbLayout" "de" which is part of the Section defining the generic keyboard and which is correctly defined for a German keyboard.

On rebooting I find that the login screen uses the US layout, the message about different keyboards is not shown and System-> Preferences->Keyboard->Layouts now shows a US layout. This is not what I need.

Manually changing this System-> Preferences->Keyboard->Layouts setting to a German layout and rebooting has no effect.

This means that the reason for the message about different keyboards is not the xorg.conf file but some thing else. The original post by wyth also noted this.

Who can help?

---

### Post by alvinistic on 2007-11-05
I went to keyboard preferences and click on the radio button under default. It solves my problem (the dialog box does not appear anymore). Hope it can help.

---

### Post by buntubunny on 2008-01-08
alvinistic's solution worked for me. Thanks alvinistic!

My guess is that setting a particular layout as "default" in Gnome would set the Gnome keyboard settings to the particular model and layout that you chose. If there was no "default" chosen, Gnome would revert back to model "generic", layout "us". In this case if the X layout (which you set in xorg.conf) did not match Gnome's selection, it would report an error.

Seems like a bug to me.

---

### Post by PhilLord on 2008-01-14
Alvinistics solution didn't seem work for me until I randomly added a new keyboard layout (a US one) and then set mine (the UK one) up as default. 


Now the message has gone away at last. 

Phil

---

### Post by Yellow Pasque on 2008-01-14
For those experiencing this issue that want to get to the heart of the problem, fire up the Configuration Editor (sudo gconf-editor). Now follow this path /desktop/gnome/peripherals/keyboard/kbd/ Remove the values from layout, model, and options keys, (leave them blank) and check the overrideSettings key.

---

### Post by tigon5 on 2008-03-03
my experience of this problem was that the gconf settings were already as suggested (ie override on, others blank), and only after I added a second non-default keboard did the message go away.

---

