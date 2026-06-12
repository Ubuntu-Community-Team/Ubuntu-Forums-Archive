---
title: "Some hot keys on wireless keyboard work, some dont, help with mouse too."
date: 2008-08-12
forum: General Help
---

### Post by PsychedelicWonders on 2008-08-12
Alright I have the microsoft ergonomic desktop pro (if it matters)

Seems the volume buttons and the calculator buttons work, but none of the F1-F12 keys work and niether does my pics, docs music work either.

Also the two thumb hot keys I have on the mouse dont seem to work either.

I checked out keyboard shortcuts under system>preferences but it doesnt seem to let me assign anything.

suggestions?

---

### Post by PsychedelicWonders on 2008-08-28
bump on getting hot keys to work.

---

### Post by mssever on 2008-08-28
The program to use is xmodmap, but I don't remember what I used to find the keycodes. Basically, you run xmodmap in login. Here's my file that I hand xmodmap to enable the browser back and forward buttons on my keyboard. Hopefully I've told you enough to enable you to find what you need. I wish I could remember what all I did.```
! Enable the ThinkPad buttons
keycode 234 = XF86Back
keycode 233 = XF86Forward
```

---

### Post by PsychedelicWonders on 2008-08-28
> **mssever said:**
> The program to use is xmodmap, but I don't remember what I used to find the keycodes. Basically, you run xmodmap in login. Here's my file that I hand xmodmap to enable the browser back and forward buttons on my keyboard. Hopefully I've told you enough to enable you to find what you need. I wish I could remember what all I did.```
! Enable the ThinkPad buttons
keycode 234 = XF86Back
keycode 233 = XF86Forward
```

Where do I get xmodmap?

Do I have to type all of that in in various code for every single key?

---

### Post by mssever on 2008-08-29
> **PsychedelicWonders said:**
> Where do I get xmodmap?

Do I have to type all of that in in various code for every single key?
Type xmodmap. If you have it, you'll get a brief usage message. if you don't have it, you'll get instructions for how to get it.

You only have to type the codes for the keys that don't work. The program xev will give you the keycodes for the keys you want to configure. For what to map the keycodes to, F1-F12 are self-explanatory. For the others, you'll have to Google a bit. I don't have those keys, so I have no experience with them. (Enabling your extra mouse buttons is another matter altogether. xev will tell you the button number of the button in question, but I don't know where to configure those buttons. Maybe /etc/X11/xorg.conf, but that's just a guess.)

---

### Post by PsychedelicWonders on 2008-08-29
where do i type xmodmap?  The terminal?

---

### Post by mssever on 2008-08-29
> **PsychedelicWonders said:**
> where do i type xmodmap?  The terminal?
Yes.

---

### Post by PsychedelicWonders on 2008-12-03
How do I get my mouse hot keys to work?

They seem to work in Firefox, but not Opera?

I know in windows, I was able to change the hot keys on the mouse from say forward or back to a magnifying glass... can I do that in ubuntu?


I did this.... now what?...

psychedelicwonders@JohnnyScience:~$ xmodmap
xmodmap:  up to 3 keys per modifier, (keycodes in parentheses):

shift       Shift_L (0x32),  Shift_R (0x3e)
lock        Caps_Lock (0x42)
control     Control_L (0x25),  Control_R (0x6d)
mod1        Alt_L (0x40),  Alt_R (0x71),  Meta_L (0x9c)
mod2        Num_Lock (0x4d)
mod3      
mod4        Super_L (0x7f),  Hyper_L (0x80)
mod5        Mode_switch (0x5d),  ISO_Level3_Shift (0x7c)

psychedelicwonders@JohnnyScience:~$

---

### Post by PsychedelicWonders on 2008-12-03
My volume key brings up a picture of a speaker when I press it... but it actually doesnt affect the sound?

Things like "My Music" and "My Pictures" hot buttons dont do anything?

Stuff like print screen works fine though?

I dont think my F keys are working either?

---

### Post by PsychedelicWonders on 2008-12-03
bump

---

