---
title: "Keyvoard inberted V and B keys -_-"
date: 2011-12-20
forum: Hardware
---

### Post by metafaniel on 2011-12-20
No... The title I wrote was not a mistake! It's just to illustrate my problem:x:-(
I've got Ubuntu Natty 11.04. I use KDE, it's not Kubuntu, it's Ubuntu with both desktop environments, I mainly use KDE.
```
$ uname -a
Linux user 2.6.38-13-generic #52-Ubuntu SMP Tue Nov 8 16:48:07 UTC 2011 i686 i686 i386 GNU/Linux
```

I've been working good with no problems, until today! I was writing some text and I noticed I was very foolish today misspelling words, then I noticed it was not my foolishness, but a problem with my keyboard -__-

The keys B and V in my keyboard are inverted! I'm writing this post with difficulty double-thinking each time I use those keys or correcting my mistakes, for the sake of a good reading of this post ;)   My system's language it's spanish:
```
$ env | grep LANG
LANG=es_MX.UTF-8
GDM_LANG=es_MX
LANGUAGE=es_MX:en
```

I've got a QWERTY Latin American keyvoard with a Generic 100 keys geometry (I'm mexican :))
```
$ setxkbmap -print
xkb_keymap {
	xkb_keycodes  { include "evdev+aliases(qwerty)"	};
	xkb_types     { include "complete"	};
	xkb_compat    { include "complete"	};
	xkb_symbols   { include "pc+latam+inet(evdev)+terminate(ctrl_alt_bksp)"	};
	xkb_geometry  { include "pc(pc101)"	};
};

```

Everything has been working fine, I didn't received any errors or warnings notifications. I've tried to reboot, switch to Gnome, switch back to KDE, change the keyboard layout, the locale, the distribution to a USA keyboard, ES, FR, any mixes of these and in ALL of them the bery same problem remains...

I habe no idea what could ve causing this provlem =/ As you can see in this sentence it's difficult to correct eberytime a mistake it's done or to pay more attention to the words using these letters.
I'be testes the rest of the keyvoard and ebery single key it's working as it should...

ANY IDEAS??
Are there any commands I should run so you people can help me??
THANKS A LOT <=)

---

### Post by 2F4U on 2011-12-20
Can you rule out that the keyboard has a hardware defect? Any chance to test in with another computer or do you have a backup keyboard?

---

### Post by metafaniel on 2011-12-20
HI! Thanks for answering ;) Yes of course, I forgot to mention that I've tested with a USB keyboard but no luck =( The original keyboard it's connected via a PS/2...
I wonder what's going on u.u hehe

---

