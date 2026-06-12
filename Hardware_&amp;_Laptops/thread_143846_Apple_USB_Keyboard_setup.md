---
title: "Apple USB Keyboard setup"
date: 2006-03-13
forum: Hardware &amp; Laptops
---

### Post by tawsi on 2006-03-13
I've been trying to find the correct map under X for my UK Apple keyboard and I've run into the following problems.

1. The key with ' and " on it requires that it be pressed twice to produce a symbol.

2. If I use the Mac map I seem to lose the ability (or it's mapped to another combination) to use ctrl+alt+ (F key) to switch between terminals.


Am I right to try and use the Mac keyboard type? 

I've tried searching the forums but can't find solutions to the specific problems mentioned above.

I'd also like to know how to set up the keyboard for use in the console but thats not a major issue.

---

### Post by takayuki on 2006-03-24
I'm looking for the correct settings for my usb apple pro keyboard as well.  anyone got an apple usb keyboard that's working as it should?  if so, could you post the keyboard section of your xorg.conf?

thanks,

takayuki

---

### Post by tawsi on 2006-03-24
I've now got it working perfectly on my setup. Unfortunately I needed to change some of the files in /etc/X11/xkb to add new symbols to the keys to get it to work with my all UK keyboards keys.

Edit: I'm also using Dapper so the packages may have changed.

---

### Post by takayuki on 2006-03-24
tawsi,

which files did you edit.  i took a look at /etc/X11/xkb, but didn:t know where to begin.

thank,

takayuki

---

### Post by tawsi on 2006-03-25
If you type setxkbmap -print if should tell you which symbol files (in /etc/X11/xkb/symbols) are being used.  On mine I think it uses macintosh_vndr/us + macintosh_vndr/gb (I can't be exact as I'm nowhere near my linux box at the moment).

What version of the keyboard are you using and what keys are wrong?

---

### Post by takayuki on 2006-03-27
when i installed ubuntu i was using a japanese pc keyboard.  then i got a kvm switch, and plugged in my apple pro keyboard from 2000.  so i've got limited functionality b/c the system thinks the apple keyboard is a japanese pc keyboard.

should i edit the xorg.conf file, and if so, what should i enter?

here's the keyboard part of my xorg.conf file:

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"c"	"pc105"
	Option		"XkbLayout"	"jp"
	Option		"XkbVariant"	"jp106"
EndSection



and here's the setxkbmap -print output...

/etc/X11$ setxkbmap -print
xkb_keymap {
        xkb_keycodes  { include "xfree86+aliases(qwerty)"       };
        xkb_types     { include "complete"      };
        xkb_compat    { include "complete"      };
        xkb_symbols   { include "pc(pc102)+jp(latin)+jp:2"      };
        xkb_geometry  { include "pc(pc104)"     };
}

thanks,

takayuki

---

### Post by takayuki on 2006-03-27
did a bit of googling...  changed xorg.conf to

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbVariant"	"jp106"
EndSection


and it works like a champ.  

and i also discovered system > preferences > keyboard.  doh!  that was far too easy.  

thanks,

takayuki

---

### Post by tawsi on 2006-03-28
Does that make things like the section key and the keypad equals work?

---

### Post by takayuki on 2006-03-28
Everything works except the equal sign on the keypad.  the equal key (under F10, to the left of delete) works fine.

even the volume up and down keys work.

oh, and i changed the xorg.conf file to what you see above, *then* i went into the System > Preferences > Keyboard Preferences and changed the keyboard model to "Macintosh" and the layout to U.S. English.

that probably wasn't the "right" way to do it, but it works.

---

### Post by tawsi on 2006-03-28
Are ~ and § in the right place on the US layout? I've got a UK keyboard and I don't know how different the layout is from the US version.

---

### Post by takayuki on 2006-04-02
the ~ is in the right spot.  don't know about the other character.

is there an app to show all available characters?  can't find it...

---

### Post by jrb114 on 2006-04-30
Hi,

Sorry if this is a bit late, but I've spent a while now and I think I've managed to get an Apple USB keyboard setup correctly. For the record, this was bought in the UK, and I like to use one of the keys to the right of the space bar as a "Compose" key. For the purposes of this, I've chosen the right hand Apple key, which is defined as the right hand Windows key.

I'm also running Dapper, but I guess this may well work for Breezy too.

From System, choose Preferences, Keyboard.

Choose the Layout tab, and select Generic 102 Key (Intl) as the model.

Choose US English. Make sure that this is at the top of the box.

Close the window.

Now, open a terminal:

```
gedit ~/.xmodmap.conf
```

Copy and paste all this in

```
keycode   8 =
keycode   9 = Escape
keycode  10 = 1 exclam 1 exclam exclamdown onesuperior 1 exclam onesuperior exclamdown 1 exclam exclamdown onesuperior
keycode  11 = 2 at 2 at EuroSign twosuperior 2 dead_diaeresis twosuperior onehalf 2 at twosuperior dead_doubleacute
keycode  12 = 3 sterling 3 sterling numbersign threesuperior 3 sterling threesuperior onethird 3 numbersign threesuperior dead_macron
keycode  13 = 4 dollar 4 dollar onehalf foursuperior 4 dollar EuroSign onequarter 4 dollar currency sterling
keycode  14 = 5 percent 5 percent onethird threeeighths 5 percent onehalf threeeighths 5 percent EuroSign
keycode  15 = 6 asciicircum 6 asciicircum threequarters fiveeighths 6 dead_circumflex threequarters onesixth 6 dead_circumflex onequarter asciicircum
keycode  16 = 7 ampersand 7 ampersand braceleft seveneighths 7 ampersand braceleft seveneighths 7 ampersand onehalf dead_horn
keycode  17 = 8 asterisk 8 asterisk bracketleft trademark 8 asterisk bracketleft trademark 8 asterisk threequarters dead_ogonek
keycode  18 = 9 parenleft 9 parenleft bracketright plusminus 9 parenleft bracketright plusminus 9 parenleft leftsinglequotemark dead_breve
keycode  19 = 0 parenright 0 parenright braceright degree 0 parenright braceright degree 0 parenright rightsinglequotemark dead_abovering
keycode  20 = minus underscore minus underscore backslash questiondown minus underscore backslash questiondown minus underscore yen dead_belowdot
keycode  21 = equal plus equal plus dead_cedilla dead_ogonek equal plus dead_cedilla dead_ogonek equal plus multiply division
keycode  22 = BackSpace Terminate_Server
keycode  23 = Tab ISO_Left_Tab
keycode  24 = q Q q Q at Greek_OMEGA q Q at Greek_OMEGA q Q adiaeresis Adiaeresis
keycode  25 = w W w W lstroke Lstroke w W lstroke Lstroke w W aring Aring
keycode  26 = e E e E e E e E eacute Eacute
keycode  27 = r R r R paragraph registered r R paragraph registered r R registered registered
keycode  28 = t T t T tslash Tslash t T tslash Tslash t T thorn THORN
keycode  29 = y Y y Y leftarrow yen y Y leftarrow yen y Y udiaeresis Udiaeresis
keycode  30 = u U u U downarrow uparrow u U downarrow uparrow u U uacute Uacute
keycode  31 = i I i I rightarrow idotless i I rightarrow idotless i I iacute Iacute
keycode  32 = o O o O oslash Oslash o O oslash Oslash o O oacute Oacute
keycode  33 = p P p P thorn THORN p P thorn THORN p P odiaeresis Odiaeresis
keycode  34 = bracketleft braceleft bracketleft braceleft dead_diaeresis dead_abovering bracketleft braceleft dead_diaeresis dead_abovering bracketleft braceleft guillemotleft guillemotleft
keycode  35 = bracketright braceright bracketright braceright dead_tilde dead_macron bracketright braceright dead_tilde dead_macron bracketright braceright guillemotright guillemotright
keycode  36 = Return
keycode  37 = Control_L
keycode  38 = a A a A ae AE a A ae AE a A aacute Aacute
keycode  39 = s S s S ssharp section s S ssharp section s S ssharp section
keycode  40 = d D d D eth ETH d D eth ETH d D eth ETH
keycode  41 = f F f F dstroke ordfeminine f F dstroke ordfeminine f F
keycode  42 = g G g G eng ENG g G eng ENG g G
keycode  43 = h H h H hstroke Hstroke h H hstroke Hstroke h H
keycode  44 = j J
keycode  45 = k K k K kra ampersand k K kra ampersand k K
keycode  46 = l L l L lstroke Lstroke l L lstroke Lstroke l L oslash Oslash
keycode  47 = semicolon colon semicolon colon dead_acute dead_doubleacute semicolon colon dead_acute dead_doubleacute semicolon colon paragraph degree
keycode  48 = apostrophe quotedbl apostrophe quotedbl dead_circumflex dead_caron dead_acute at apostrophe bar dead_acute dead_diaeresis apostrophe quotedbl
keycode  49 = section plusminus section plusminus
keycode  50 = Shift_L
keycode  51 = backslash bar backslash bar
keycode  52 = z Z z Z guillemotleft less z Z guillemotleft less z Z ae AE
keycode  53 = x X x X guillemotright greater x X guillemotright greater x X
keycode  54 = c C c C cent copyright c C cent copyright c C copyright cent
keycode  55 = v V v V leftdoublequotemark grave v V leftdoublequotemark grave v V
keycode  56 = b B b B rightdoublequotemark apostrophe b B rightdoublequotemark apostrophe b B
keycode  57 = n N n N n N n N ntilde Ntilde
keycode  58 = m M m M mu masculine m M mu masculine m M mu mu
keycode  59 = comma less comma less horizconnector multiply comma less horizconnector multiply comma less ccedilla Ccedilla
keycode  60 = period greater period greater periodcentered division period greater periodcentered division period greater dead_abovedot dead_caron
keycode  61 = slash question slash question dead_belowdot dead_abovedot slash question dead_belowdot dead_abovedot slash question questiondown dead_hook
keycode  62 = Shift_R
keycode  63 = KP_Multiply XF86_ClearGrab
keycode  64 = Alt_L Meta_L
keycode  65 = space
keycode  66 = Caps_Lock
keycode  67 = F1 XF86_Switch_VT_1
keycode  68 = F2 XF86_Switch_VT_2
keycode  69 = F3 XF86_Switch_VT_3
keycode  70 = F4 XF86_Switch_VT_4
keycode  71 = F5 XF86_Switch_VT_5
keycode  72 = F6 XF86_Switch_VT_6
keycode  73 = F7 XF86_Switch_VT_7
keycode  74 = F8 XF86_Switch_VT_8
keycode  75 = F9 XF86_Switch_VT_9
keycode  76 = F10 XF86_Switch_VT_10
keycode  77 = Num_Lock
keycode  78 = Scroll_Lock
keycode  79 = KP_Home KP_7
keycode  80 = KP_Up KP_8
keycode  81 = KP_Prior KP_9
keycode  82 = KP_Subtract XF86_Prev_VMode
keycode  83 = KP_Left KP_4
keycode  84 = KP_Begin KP_5
keycode  85 = KP_Right KP_6
keycode  86 = KP_Add XF86_Next_VMode
keycode  87 = KP_End KP_1
keycode  88 = KP_Down KP_2
keycode  89 = KP_Next KP_3
keycode  90 = KP_Insert KP_0
keycode  91 = KP_Delete KP_Decimal
keycode  92 =
keycode  93 = Mode_switch
keycode  94 = grave asciitilde grave asciitilde numbersign
keycode  95 = F11 XF86_Switch_VT_11
keycode  96 = F12 XF86_Switch_VT_12
keycode  97 = Home
keycode  98 = Up
keycode  99 = Prior
keycode 100 = Left
keycode 101 =
keycode 102 = Right
keycode 103 = End
keycode 104 = Down
keycode 105 = Next
keycode 106 = Insert
keycode 107 = Delete
keycode 108 = KP_Enter
keycode 109 = Control_R
keycode 110 = Pause Break
keycode 111 = Print Sys_Req
keycode 112 = KP_Divide XF86_Ungrab
keycode 113 = Alt_R Meta_R ISO_Level3_Shift NoSymbol ISO_Level3_Shift ISO_Level3_Shift
keycode 114 =
keycode 115 = Super_L
keycode 116 = Multi_key Multi_key Multi_key Multi_key Multi_key Multi_key Super_R
keycode 117 = Menu
keycode 118 =
keycode 119 =
keycode 120 =
keycode 121 =
keycode 122 =
keycode 123 =
keycode 124 = ISO_Level3_Shift
keycode 125 = NoSymbol Alt_L
keycode 126 = KP_Equal
keycode 127 = NoSymbol Super_L
keycode 128 = NoSymbol Hyper_L
keycode 129 =
keycode 130 =
keycode 131 =
keycode 132 =
keycode 133 =
keycode 134 =
keycode 135 =
keycode 136 =
keycode 137 =
keycode 138 =
keycode 139 =
keycode 140 =
keycode 141 =
keycode 142 =
keycode 143 =
keycode 144 =
keycode 145 =
keycode 146 =
keycode 147 =
keycode 148 =
keycode 149 =
keycode 150 =
keycode 151 =
keycode 152 =
keycode 153 =
keycode 154 =
keycode 155 =
keycode 156 = NoSymbol Meta_L
keycode 157 =
keycode 158 =
keycode 159 =
keycode 160 =
keycode 161 =
keycode 162 =
keycode 163 =
keycode 164 =
keycode 165 =
keycode 166 =
keycode 167 =
keycode 168 =
keycode 169 =
keycode 170 =
keycode 171 =
keycode 172 =
keycode 173 =
keycode 174 =
keycode 175 =
keycode 176 =
keycode 177 =
keycode 178 =
keycode 179 =
keycode 180 =
keycode 181 =
keycode 182 =
keycode 183 =
keycode 184 =
keycode 185 =
keycode 186 =
keycode 187 =
keycode 188 =
keycode 189 =
keycode 190 =
keycode 191 =
keycode 192 =
keycode 193 =
keycode 194 =
keycode 195 =
keycode 196 =
keycode 197 =
keycode 198 =
keycode 199 =
keycode 200 =
keycode 201 =
keycode 202 =
keycode 203 =
keycode 204 =
keycode 205 =
keycode 206 =
keycode 207 =
keycode 208 =
keycode 209 =
keycode 210 =
keycode 211 =
keycode 212 =
keycode 213 =
keycode 214 =
keycode 215 =
keycode 216 =
keycode 217 =
keycode 218 =
keycode 219 =
keycode 220 =
keycode 221 =
keycode 222 =
keycode 223 =
keycode 224 =
keycode 225 =
keycode 226 =
keycode 227 =
keycode 228 =
keycode 229 =
keycode 230 =
keycode 231 =
keycode 232 =
keycode 233 =
keycode 234 =
keycode 235 =
keycode 236 =
keycode 237 =
keycode 238 =
keycode 239 =
keycode 240 =
keycode 241 =
keycode 242 =
keycode 243 =
keycode 244 =
keycode 245 =
keycode 246 =
keycode 247 =
keycode 248 =
keycode 249 =
keycode 250 =
keycode 251 =
keycode 252 =
keycode 253 =
keycode 254 =
keycode 255 =

```

And save the file.

Now log out and back in again, and you should be prompted to load the keyboard mappings found in .xmodmap.conf. Do this, and, hey presto, all your keybindings should now work.

You may notice that there is no hash (#) on the keyboard. To get this (using this setup) press the right hand <Alt> and <3>. If you press right hand <Alt>  and any other key (try with all the number kets) you can get loads more characters. Also right hand <Alt> + right hand <Shift> and any other key (again, try the numbers) gives plenty more characters too.

e.g.

RH <Alt> + <1> ¡
RH <Alt> + <2> €
RH <Alt> + <3> #
RH <Alt> + <4> ½
RH <Alt> + <5> &#8531;
RH <Alt> + <6> ¾

RH <Shift> + RH <Alt> + 1 ¹
RH <Shift> + RH <Alt> + 2 ²
RH <Shift> + RH <Alt> + 3 ³
RH <Shift> + RH <Alt> + 4 &#8308;
RH <Shift> + RH <Alt> + 5 &#8540;
RH <Shift> + RH <Alt> + 6 &#8541;

These are all customisable. If you look inside the .xmodmap.conf file, you will see lines like:

```

keycode  10 = 1 exclam 1 exclam exclamdown onesuperior 1 exclam onesuperior exclamdown 1 exclam exclamdown onesuperior

```

Which means that keycode 10 (which is returned by the keyboard with the <1> key is pressed) should return,

numeral 1 if no other key is pressed.
exclamation mark is shift is pressed at the same time.
an upside down exclamation mark (I'm not too hot at its use, see [http://en.wikipedia.org/wiki/%C2%A1](http://en.wikipedia.org/wiki/%C2%A1) for more info)
¹ (a superscript 1) if <Shift>+<Alt> and 1 are pressed at the same time.

You'll also notice that the line has "1 exclam 1 ..." I'm not entirely sure of the meaning of the first two listings for every line. If anyone else knows ...

One final note. I mentioned I had set this up with the "Compose" key ready to go. I find this really useful, since it can do all sorts of accented characters by key combinations...

e.g.
é = <Right Hand (RH Apple)> then <'> then <e>
à = <RH Apple> then <`> then <a>
« = <RH Apple> then < < > then < < >     (NB < < > is <Shift>+<,>)
» = <RH Apple> then < > > then < > >     (NB < > > is <Shift>+<.>)
ç = <RH Apple> then <,> then <c>
ï = <RH Apple> then <"> then <i>

Try it with other letters to get the idea.

Well, this seem to be dragging. Hope it's of use to someone, and try out all those <Alt> and <Shift>+<Alt> combinations.

James

---

### Post by danalderman on 2006-08-02
This doesn't seem to be working quite right for me (Apple Uk USB keyboard on Intel P4 865).  I have the following in xorg.conf

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc102"
        Option          "XkbLayout"     "us"
EndSection

I entered the information that you gave into my .xmodmap.conf, which goat loaded at login, but now whenever I hit right_alt + 3 I get (arg: 3) displayed in my term, and nothing in any other app.  Writing code without a 'hash' key is quite frustrating ](*,) 

I've tried fiddling with the modifier options in gnome keyboard settings but I can't get it to work.  Any hints?

Cheers,

D.

---

### Post by jrb114 on 2006-08-03
Ah,

Looks like you hit it on the head there; your xorg.conf is different from mine.

Try replacing your keyboard section with this:

```

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "gb"
EndSection

```

Incidentally, I've just noticed that my Gnome keyboard settings currently are UK layout and "Generic 105 Keys (Intl)". I've just tried changing them to US and "Generic 102 Keys Intl", Log out, Log in, and everything still just works. I guess the Gnome setting is being overridden by X. (The whole 2 settings to control the same thing is where everything becomes a nightmare.)

Good luck !

James

=== EDIT ===

By the way, I'm guessing that the  (arg: 3) issue is due to the 102 vs. 105 key issue (addition of Windows/Apple/Meta/What's-its-name keys will bump up the right hand alt key ID by a couple compared to a keyboard with out them) as I didn't understand how you got (arg: whatever) until I tried the left hand alt with 1, 2, etc.

---

