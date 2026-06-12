---
title: "No dedicated support for some of the media keys of e.g. a Logitech K400 keyboard"
date: 2015-03-16
forum: Hardware
---

### Post by ako673de on 2015-03-16
My application has a configuration file that maps X key event names to user defined actions. The problem is that this configuration file does not accept modifiers like "Shift", "Alt", "Ctrl". With a normal "PC-105" keyboard configured in the system, this fact is limiting usage of the media keys to those that obviously are being given dedicated names by default. Such are e.g. the key with a lens on it (showing "XF86Search" in the tool xev), or the key with a music note not it (showing "XF86Tools").

But e.g. the key with a lock on it just shows an "l" and the "meta" bit set in the modifier byte. This is true for at least 7 media keys, that all generate combinations of a letter together with "Meta" (=the "Windows"-Key) and sometimes even "Ctrl".

The question: Is there a preset file for setxkbmap, that simply can be loaded to add dedicated support for these (Windows specific) media keys?

Or has anybody build one by himself? I tried myself but gave up very soon, just when it came to expanding the modifier levels to "five levels" (xkbmap by default is limited to "Shift", "Ctrl" and "Alt" (three levels) when it comes to generation of key event names). Or are there other (generic) solutions out there?

best regards
ako673de

---

