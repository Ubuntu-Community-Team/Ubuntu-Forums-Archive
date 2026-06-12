---
title: "keyboard layout howto"
date: 2010-12-28
forum: Hardware
---

### Post by Andy Meier on 2010-12-28
Ubuntu 10.10 
I use a local keyboard with us and Thai layout.
The us layout is ok for me, but I like to have some
additional german characters like "äöü ÄÖÜ"
This can easy be implemented with xmodmap, but if 
you switch to the second layout, you will observe 
some strange results.

After plenty of  googling, I found an IMHO easy and 
perfect solution: create and use your custom keyboard!

1) /usr/share/X11/xkb/symbols/
   choose your nearest preference, in my case "us"
   and save it with a new name: "us-de" 

2) delete anything, which you don't need, and change, 
   what ever you like. My file for "us-de":
-----------
default
xkb_symbols "basic" {

    name[Group1]= "ASCII with german";

    // Alphanumeric section
    key <TLDE> {    [     grave,    asciitilde    ]    };
    key <AE01> {    [      1,    exclam         ]    };
    key <AE02> {    [ 2, at, twosuperior        ]    };
    key <AE03> {    [ 3, numbersign, threesuperior    ]    };
    key <AE04> {    [ 4, dollar, onequarter        ]    };
    key <AE05> {    [ 5, percent, onehalf        ]    };
    key <AE06> {    [ 6, asciicircum, threequarters    ]    };
    key <AE07> {    [      7,    ampersand    ]    };
    key <AE08> {    [ 8, asterisk, oneeighth    ]    };
    key <AE09> {    [      9,    parenleft    ]    };
    key <AE10> {    [ 0, parenright, degree            ]    };
    key <AE11> {    [     minus,    underscore    ]    };
    key <AE12> {    [     equal,    plus        ]    };

    key <AD01> {    [      q,    Q         ]    };
    key <AD02> {    [      w,    W        ]    };
    key <AD03> {    [ e, E, EuroSign, cent        ]    };
    key <AD04> {    [      r,    R        ]    };
    key <AD05> {    [      t,    T        ]    };
    key <AD06> {    [      y,    Y        ]    };
    key <AD07> {    [ u, U, udiaeresis, Udiaeresis    ]    };
    key <AD08> {    [      i,    I        ]    };
    key <AD09> {    [ o, O, odiaeresis, Odiaeresis    ]    };
    key <AD10> {    [      p,    P        ]    };
    key <AD11> {    [ bracketleft,    braceleft    ]    };
    key <AD12> {    [ bracketright,    braceright    ]    };

    key <AC01> {    [ a, A, adiaeresis, Adiaeresis    ]    };
    key <AC02> {    [      s,    S        ]    };
    key <AC03> {    [      d,    D        ]    };
    key <AC04> {    [      f,    F        ]    };
    key <AC05> {    [      g,    G        ]    };
    key <AC06> {    [      h,    H        ]    };
    key <AC07> {    [      j,    J        ]    };
    key <AC08> {    [      k,    K        ]    };
    key <AC09> {    [      l,    L        ]    };
    key <AC10> {    [ semicolon,    colon        ]    };
    key <AC11> {    [ apostrophe,    quotedbl    ]    };

    key <AB01> {    [      z,    Z         ]    };
    key <AB02> {    [      x,    X        ]    };
    key <AB03> {    [      c,    C        ]    };
    key <AB04> {    [      v,    V        ]    };
    key <AB05> {    [      b,    B        ]    };
    key <AB06> {    [      n,    N        ]    };
    key <AB07> {    [ m, M, mu              ]    };
    key <AB08> {    [     comma,    less        ]    };
    key <AB09> {    [    period,    greater        ]    };
    key <AB10> {    [     slash,    question    ]    };

    key <BKSL> {    [ backslash,         bar    ]    };
    key <CAPS> {        [ VoidSymbol            ]       };

    // End alphanumeric section
    include "level3(ralt_switch)"
};
-----------

3) /usr/share/X11/xkb/rules/evdev.xml
   Modify "evdev.xml" so your custom keyboard will be recognised:
   search for "</layoutList>" and 
   add the following just previous to "</layoutList>"  
-----------
    <layout>
      <configItem>
        <name>us-de</name>                                                                                                            <!-- 1) -->
        <shortDescription>US-DE</shortDescription>          <!-- 2) -->
        <description>ASCII with german</description>             <!-- 3) -->
        <languageList><iso639Id>eng</iso639Id></languageList>    <!-- 4) -->
      </configItem>
    </layout>
-----------
<!-- 1) --> "us-de"  is the filename of the new keyboard layout in X11/xkb/symbols
<!-- 2) --> "US-DE"  this will appear eg. in the indicator applet
<!-- 3) --> "ASCII with german" must coincide with the text at the begin of your file:
            name[Group1]= "ASCII with german";
            This text will also appear as comment under "Layouts"
<!-- 4) --> if you choose "eng" your layout will be shown in 
            System->Preferences->Keyboard->tab Layouts->Add->By Language->English
            under "Variants"

4) log out and log in again, and check 
   System->Preferences->Keyboard->tab Layouts->Add->By Language->English
   if you can find your custom layout, happy! You are ready to go!
   Select your first and second layou here. Add a keyboard switcher applet
   here under "options" you can also disable the CapsLock key.

5) the default keyboard will annoy you and sometime reappear... 
   If you like to get rid of this, edit
   /var/cache/gdm/$USER/dmrc
   and place anything existing as your new default: "Layout=us-de"
   then reboot..

I post this, as it is easy, but difficult to find out, and perhaps
to make somebody happy...
Feedback and hints to improve are welcome!

---

### Post by oldarney on 2011-10-23
Hey, Great guide.

Any ideas on how to add layouts to the us-de file? For example, the us file has layouts for querty, dvorak and many others. It would be nice if I could have an "olds" file with math, logic and other arcane keyboards.

Thanks. And sorry for the gd.

---

