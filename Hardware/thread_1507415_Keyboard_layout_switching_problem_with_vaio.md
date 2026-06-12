---
title: "Keyboard layout switching problem with vaio"
date: 2010-06-11
forum: Hardware
---

### Post by feedbee on 2010-06-11
I set my system to switch KB layout with Alt+Shift combination.

But in reality I press Shift button before Alt. And with my Sony Vaio VPCEB1S1E no action happens after Shift+Alt was pressed. In case of Alt+Shift (Alt pressed before Shift) layout switches correctly.

Is any way to get Shift+Alt working properly?

---

### Post by simosx on 2010-06-12
> **feedbee said:**
> I set my system to switch KB layout with Alt+Shift combination.

But in reality I press Shift button before Alt. And with my Sony Vaio VPCEB1S1E no action happens after Shift+Alt was pressed. In case of Alt+Shift (Alt pressed before Shift) layout switches correctly.

Is any way to get Shift+Alt working properly?

Both Shift+Alt and Alt+Shift should work. I just verified.
There might be something different with your settings.
Could you run the following in a terminal window and report back?

gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd

---

### Post by feedbee on 2010-06-13
$ gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd
 layouts = [us,ru]
 options = [grp	grp:alts_toggle,grp	grp:alt_shift_toggle,grp	grp:lwin_toggle,grp	grp:rwin_toggle,lv3	lv3:ralt_switch,compat	misc:typo,keypad	keypad:oss,terminate	terminate:ctrl_alt_bksp]
 model = pc105

Both combinations works well on my second laptop (HP). But not on Vaio. By the way, both combinations works well on the same (Vaio) laptop in Windows.

Thanks for trying to help.

---

### Post by simosx on 2010-06-14
> **feedbee said:**
> $ gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd
 layouts = [us,ru]
 options = [grp	grp:alts_toggle,grp	grp:alt_shift_toggle,grp	grp:lwin_toggle,grp	grp:rwin_toggle,lv3	lv3:ralt_switch,compat	misc:typo,keypad	keypad:oss,terminate	terminate:ctrl_alt_bksp]
 model = pc105

Both combinations works well on my second laptop (HP). But not on Vaio. By the way, both combinations works well on the same (Vaio) laptop in Windows.


What I see is that you have quite a few things enabled in the 'options':
 options = [grp	grp:alts_toggle,grp	grp:alt_shift_toggle,grp	grp:lwin_toggle,grp	grp:rwin_toggle,lv3	lv3:ralt_switch,compat	misc:typo,keypad	keypad:oss,terminate	terminate:ctrl_alt_bksp]

The proper setting for Alt+Shift switching layouts is 'grp:alt_shift_toggle'. In your case you have 'grp:alt_shift_toggle,grp' with a ',grp' appended. In addition, you have 'grp:alts_toggle,grp' which is 'Both Alt keys switch layout'. These two may conflict.

I suggest that you start over with the Layout Options, with initial settings:
[INDENT]
 layouts = [us,ru]
 options = [grp	grp:alt_shift_toggle]
 model = pc105
[/INDENT]

Then, you can add one by one those additional settings you have until to find which new setting messed up with Alt+Shift/Shift+Alt. When you set a shortcut in Layout Options and click Close, the setting is enabled at once so you can run 'gconftool-2' to verify and press keys to check.

---

### Post by feedbee on 2010-06-14
Big thanks! You was right: "Both ALT keys" and "Alt+Shift" keys are incompatible. My problem was gone when I disabled "Both ALT keys" combination.

---

