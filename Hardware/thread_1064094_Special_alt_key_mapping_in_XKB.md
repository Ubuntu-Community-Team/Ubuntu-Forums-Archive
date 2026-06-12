---
title: "Special alt key mapping in XKB"
date: 2009-02-08
forum: Hardware
---

### Post by issueperson on 2009-02-08
I am trying to remap my left alt key to serve as a backspace in the /etc/X11/xkb/symbols/us file, and shift the L_Alt function to the windows key.  I managed to get the windows key working as alt, but cannot get the alt to backspace.  Any ideas?

```
partial alphanumeric_keys
xkb_symbols "dvorak-intl" {

    name[Group1]= "USA - Dvorak international";

    include "us(dvorak)"
    key <AE01> { [	    1,	exclam, exclamdown	]	};
    key <AE04> { [         4,  dollar,    EuroSign ] };

    key <AD02> { [     comma,    less,  adiaeresis,       dead_caron ] };
    key <AD03> { [    period, greater, ecircumflex,   periodcentered	] };
    key <AD04> { [         p,       P,  ediaeresis,     dead_cedilla ] };
    key <AD05> { [         y,       Y,  udiaeresis ] };
    key <AD08> { [         c,       C,    ccedilla,    dead_abovedot ] };
    key <AD11> { [	slash,	question,  questiondown       ]	};
    key <AC01> { [         a,       A,      aacute, Aacute ] };
    key <AC02> { [         o,       O, oacute, Oacute ] };
    key <AC03> { [         e,       E,      eacute, Eacute ] };
    key <AC04> { [         u,       U, uacute, Uacute ] };
    key <AC05> { [         i,       I, iacute, Iacute ] };
    key <AC09> { [	   n,       N, ntilde,           Ntilde ] };
    key <AC10> { [         s,       S,      ssharp ] };

    key <AB01> { [ semicolon,   colon, acircumflex ] };
    key <AB02> { [         q,       Q,  oacute,      dead_ogonek ] };
    key <AB03> { [         j,       J,      egrave, dead_doubleacute ] };
    key <AB04> { [         k,       K,      ugrave ] };
    key <AB05> { [         x,       X,  idiaeresis ] };
  [B]  key <LWIN> { [         Alt_L ] }; *[COLOR="Red"]<--- works[/COLOR]*
    key <LALT> { [         BackSpace ] };*[COLOR="Red"]<--- doesn't work[/COLOR]*[/B]

    include "level3(ralt_switch)"
};
```

---

### Post by issueperson on 2009-02-12
bump

---

### Post by billdotson on 2009-10-24
If I come across anything that is helpful I'll let you know

---

