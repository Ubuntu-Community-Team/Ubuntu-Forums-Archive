---
title: "[SOLVED] Double press to get apostrophe"
date: 2008-09-02
forum: General Help
---

### Post by Bucky Ball on 2008-09-02
Hi all,

Have been screwing around with this for too long and not getting far. It is also happening on my wife&#347; laptop. You can see from the ´s´ in wife&#347; what I am talking about. Great if I was speaking another language!

I have been to System->Preferences->Keyboard and tried a million and one layouts (I exaggerate) but no change. If I want an apstrophe, I need to double press the apostrophe key. If I press it once, it does this to the next letter I press: ó. Eek. This is also happening with the tilde and obviously my keyboard (an old IBM from an Aptiva) is setup in Ubuntu for another language. I have changed everything to not be that way but must be missing something. This is frustrating, as you can imagine.

So, any ideas? Sorry, I know this must be really a simple thing to fix.

:)

---

### Post by iaculallad on 2008-09-02
What about trying to remap your keyboard layout to defaults with:

```
sudo dpkg-reconfigure xserver-xorg
```

Just be sure to create a backup of your /etc/X11/xorg.conf file.

---

### Post by Bucky Ball on 2008-09-02
Nope, no change. Incidentally, I did a backup of /etc/X11/xorg.conf file, but the reconfiguration GUI also seems to do one for me at the end of proceedings. Cool.

If this gives anymore clues; when I am in the terminal on the laptop (this is happening on my desktop) and I hit the up arrow key, it runs through the previous commands I have entered since the computer has been on, which is really neat and saves you remembering and typing in the same commands repeatedly. This just gives me a code for the key I am pressing. Same with backspace and a few other keys. Grim. ;(

---

### Post by mixmaster on 2008-09-02
Looks like you are picking up a non-English keyboard map - they apostrope key is being used as a dead key for an acute accent.  If you can't force your keyboard back to English you can play with xmodmap to investigate and change the behaviour of specific keys.

---

### Post by Bucky Ball on 2008-09-02
Yea, that&#347; the way it seems. Thanks for the tip - I&#314;l give it a try and let you know how I go ... lol, see what I mean? I am all set for English in System->keyboard. Gutsy was fine and just getting around to setting up this desktop with Hardy. Odd.

* Update: Back so soon ... Well, this is what I got in terminal. Where do I go from here?

```
$ sudo xmodmap
[sudo] password for ustudio: 
xmodmap:  up to 3 keys per modifier, (keycodes in parentheses):

shift       Shift_L (0x32),  Shift_R (0x3e)
lock        Caps_Lock (0x42)
control     Control_L (0x25),  Control_R (0x6d)
mod1        Alt_L (0x40),  Meta_L (0x9c)
mod2        Num_Lock (0x4d)
mod3      
mod4        Super_L (0x7f),  Hyper_L (0x80)
mod5        Mode_switch (0x5d),  ISO_Level3_Shift (0x71),  ISO_Level3_Shift (0x7c)
```

Can you spot anything that doesn´t look right?

---

### Post by forger on 2008-09-02
1) which brand/model laptop is it?
2) can you post the /etc/X11/xorg.conf file and tell me which keyboard layout you currently use? (System > preferences > Keyboard > layout)

Found some details for those characters:
> 
&#347;
U+015B LATIN SMALL LETTER S WITH ACUTE
General Character Properties
Unicode category: Letter, Lowercase
Canonical decomposition: U+0073 LATIN SMALL LETTER S + U+0301 COMBINING ACUTE ACCENT
Various Useful Representations
UTF-8: 0xC5 0x9B
UTF-16: 0x015B
C octal escaped UTF-8: \305\233
XML decimal entity: &#347;
Annotations and Cross References
Notes:
 • **Polish, Indic transliteration**, ...

...

&#314;

U+013A LATIN SMALL LETTER L WITH ACUTE

General Character Properties

Unicode category: Letter, Lowercase
Canonical decomposition: U+006C LATIN SMALL LETTER L + U+0301 COMBINING ACUTE ACCENT

Various Useful Representations

UTF-8: 0xC4 0xBA
UTF-16: 0x013A

C octal escaped UTF-8: \304\272
XML decimal entity: &#314;

Annotations and Cross References

Notes:
** • Slovak**


---

### Post by Bucky Ball on 2008-09-02
Done!

Set to Generic 105key-intl-pc.
Layout = USA

Weird, because it was never set to any other language than USA but by default was set to USA (dead keys), which I changed to United Kingdom (only other english option. It was set to 105 in the first place also. The difference appears to be the dead keys. Or something ... yet another charming quirk, but the beauty is, now it is set, I can forget! Just took an hour of experimenting! Thanks all. :)

* Hold everything - maybe I was a little quick off the mark and maybe I will re-post with this one, but ...

In the terminal, the up arrow is still give me key code rather than last command entered. Any ideas on that one? Hope you haven't all run away when you've seen 'Solved'! Eek!

---

