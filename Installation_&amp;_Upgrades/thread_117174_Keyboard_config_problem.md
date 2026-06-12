---
title: "Keyboard config problem"
date: 2006-01-14
forum: Installation &amp; Upgrades
---

### Post by LadyLuck on 2006-01-14
After uppgrading to Breezy my keyboard settings are messed up. In the GUI environment the Layouts tab in Keyboard Preferences (System > Preferences > Keyboard) shows the correct keyboard map is default (icelandic) and english is the altrernate. However after reeboot the English keyboard map is "active" again.

Running

[B]setxkbmap -v
[/B]
in a terminal wondiw yields

[B]Trying to build keymap using the following components:
keycodes:   xfree86+aliases(qwerty)
types:      complete
compat:     complete
symbols:    pc(pc105)+is+inet(dell)+us:2+group(alts_toggle)
geometry:   pc(pc104)[/B]

and subsequently the correct keyboard map is set, but only until the next reboot. How can I make this permanent.

Cheers 
LL

---

### Post by adwait on 2006-01-14
In the same place that you set the keyboard maps system>preferences.... there must be an option to change the start up keyboard map or something.

---

### Post by LadyLuck on 2006-01-14
As far as I can see the correct layout is checked as default. The problem it seems to me is that the "system" is not aware of this setting until I "setxkbmap -v." 

Being a newbie I admit I don't know what "setxkmap -v" does exactly, but it works. According to my ref. it allows one to "view your current X keyboard settings"

So two questions. How do I make the icelandic keyboard a permanent feature? and what does "setxkmap -v" do exactly?

cheers
LL

---

### Post by adwait on 2006-01-14
ok.....well I can't really find the exact problem, but I can give you a stop gap solution that will work. Just put
> setxkbmap -v

in a file. Now make that file executable with
```
chmod +x <filename>
```

Now go to Settings>Prferences>Sessions and chose this file to be run every time you login. This way, the command will be run automatically everytime you login.

---

