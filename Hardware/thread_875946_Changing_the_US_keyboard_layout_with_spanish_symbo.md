---
title: "Changing the US keyboard layout with spanish symbols"
date: 2008-07-31
forum: Hardware
---

### Post by georgeguitar on 2008-07-31
Hi friends,

I have a Aspire 3680 laptop with us keyboard and I want to use the special characters is Spanish by pressing the AltGr key like the ñ and the accents. 

In the last Ubuntu version, my keyboard was working perfect, I could press:

AltGr + n = ñ
For the accents it was just enough to press the " ' key followed by the vowel key to write:

á é í ó ú

But since I've upgraded to Ubuntu 8.04 - the Hardy Heron - released in April 2008, the keyboard is working in a different way, when I press the " ' key followed by a key vowel I have this output:

'a 'e 'i 'o 'u


I've found some information about this and basically it says that I have to change the keyboard symbols in the /etc/X11/xkb/symbols/us file:

```
partial alphanumeric_keys
xkb_symbols "altgr-intl" {

   name[Group1]= "USA - International (AltGr dead keys)";

   include "us(intl)"

// five dead keys moved into level3:

//Original
//   key <TLDE> { [    grave, asciitilde,  dead_grave,   dead_tilde      ] };
//   key <AC11> { [apostrophe,quotedbl,    dead_acute,   dead_diaeresis  ] };

//Changed
   key <TLDE> { [dead_grave,  dead_tilde,      grave,        asciitilde   ] };
   key <AC11> { [dead_acute,  dead_diaeresis,  apostrophe,   quotedbl     ] };

// diversions from the MS Intl keyboard:

   key <AE01> { [        1, exclam,      onesuperior,  exclamdown      ] };
   key <AD04> { [        r, R,           ediaeresis,   Ediaeresis      ] };
   key <AC07> { [        j, J,           idiaeresis,   Idiaeresis      ] };
   key <AB02> { [        x, X,           oe,           OE              ] };
   key <AB04> { [        v, V,           registered,   registered      ] };

// onequarter etc (not in iso8859-15) deleted to get three unshifted deadkeys:

   key <AE06> { [        6, asciicircum,       dead_circumflex         ] };
   key <AE07> { [        7, ampersand,         dead_horn               ] };
   key <AE08> { [        8, asterisk,          dead_ogonek             ] };

   include "level3(ralt_switch)"
};


```
With this changes I can use the AltGr to write the Spanish accents:

AltGr + a = á
AltGr + e = é
AltGr + i = í
AltGr + o = ó
AltGr + u = ú


But is not what I want, I want my keyboard as It was before, because I'm get used to that.

Thanks in advance.

---

### Post by LowSky on 2008-07-31
you need to reconnfigure you xorg.conf file, I suggest this way

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

and run through the commands

---

### Post by sergiom99 on 2008-07-31
my laptop has US keyboard. I type in spanish by using the left Windows key as a compose key

Solved adding this to my xorg.conf file:

```


Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
# agregado para tratar de usar LWIN como Compose Key -- 08/06/08
        Option         "XkbOptions" "compose:lwin"
EndSection

```
cheers!

---

### Post by agave on 2008-08-07
I am having the same problem with a spanish (es) keyboard. accents do not work at all, and when I change the layout no changes seem to happen. I get also get ´a´e´i´o´u .

---

