---
title: "Binding the extra buttons of my Logitech MX-600"
date: 2009-03-13
forum: Hardware
---

### Post by Sohcahtoa on 2009-03-13
I've recently switched to Ubuntu from Windows XP due to getting hit by a virus that spread itself over so many EXEs that I was going to have to reformat anyways, so I decided it'd be a good idea to give Linux a try.

Anyways, I use a Logitech MX-600 mouse with 8 buttons and a tilting scroll wheel.  I liked it because I'm a major World of Warcraft addict and wanted all the extra mouse buttons without paying $80 for a fancy "gaming" mouse.  However, WoW did not detect all the extra buttons (Just the standard three plus the two thumb buttons) so I used Logitech's SetPoint software to bind the extra buttons to keyboard keys, then bound actions in WoW to those keys.

I can't figure out how to perfectly recreate this action in Ubuntu.  I managed to sort of do it using xbindkeys and xautomation, but there's a slight problem.  If I'm holding the right mouse button and hit one of the extra buttons, xbindkeys doesn't trigger the action.  This becomes a problem in WoW when I'm holding the right mouse button to rotate my character while hitting the mouse button to use a specific ability.  The ability doesn't get used.

I tried duplicating one of the key binds in xbindkeys's config file, adding special cases for hitting both mouse buttons at the same time, but it totally broke it.  The result ended up being that hitting just the extra mouse button did nothing, while clicking the right mouse button caused it to trigger twice.

Here's the code I'm using right now in my .xbindkeysrc file to bind one of my buttons to press the number 6 on my keyboard:

```
"xte 'key 6' &"
  b:10
```

And it works, but only if I'm not holding the right mouse button.  To try to detect pressing that mouse button while the right mouse button was being held, I added this entry:

```
"xte 'key 6' &"
  b:10 + b:3
```

And as I said, with both entries, it makes it so hitting just the button does nothing, but clicking the right mouse button causes 6 to be hit twice, even if I'm not pressing that other mouse button at all.

I did some searching and discovered the program HIDPoint, but it doesn't detect my mouse at all, and even worse, it makes my mouse behave like a simple 2-button mouse with a scroll wheel throughout Ubuntu.  Even xev didn't detect any other button presses while HIDPoint was installed.

Any help?

---

