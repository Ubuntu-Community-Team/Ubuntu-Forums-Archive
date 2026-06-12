---
title: "Custom keyboard layout?"
date: 2007-04-20
forum: Hardware &amp; Laptops
---

### Post by jim0203 on 2007-04-20
I've been using Xubuntu on my old Toshiba Portege 2000 for quite a while now, but have got the keyboard to work properly. I've tried various different keyboard setups, but none of them seem to work properly: in particular, the home/end keys, the page up and down keys, and the hash/tilde keys don't work. 

Now, here are my questions:

(1) Is there a relatively simple way I can write a custom keyboard setup for my laptop?
(2) Is there a program available that would enable me to map the keys that aren't working to specific functions?
(3) Has anyone got any other ideas how I can sort this out???

--Jim

---

### Post by jim0203 on 2007-04-21
I'm bumping this, merely to say: if anyone who knows a thing or two about Ubuntu could reply, even if it is to say "you'll just have to put up with you PgUp and PgDn not working", it would  be great!

--Jim

---

### Post by NilsR on 2008-04-23
I'm currently looking at adding some keys to my keyboard. (I'm Norwegian on an GB laptop). I've found an interesting resource that may help you as well.

[http://people.uleth.ca/~daniel.odonnell/Blog/custom-keyboard-in-linuxx11](http://people.uleth.ca/~daniel.odonnell/Blog/custom-keyboard-in-linuxx11)

"""
The following shows how I customised my keyboard and compose sequences in Ubuntu (I currently use Ubuntu Edgy, but the method works on earlier versions). The same techniques should work in other X11-based distributions.
"""

Though I must say your problem sounds like symptoms of something buggy, so this may not be the right medicine.

---

### Post by NilsR on 2008-04-23
I ended up doing it slightly simpler than explained in that link.

I copied the "basic" entry from the /usr/share/X11/xkb/symbols/gb file and added it to the end of the same file.

Changed the first line from

partial default alphanumeric_keys
xkb_symbols "basic" {

to

partial alphanumeric_keys
xkb_symbols "no2" {

Changed the descriptive name:

    name[Group1]="United Kingdom (with Norwegian keys)"; 

Added keys where I wanted them:

    key <AD11>	{ [bracketleft,  braceleft, ae, AE ] };
    key <AD12>	{ [bracketright, braceright, oslash,  Ooblique ]	};

Changed one line more:

    key <BKSL>	{ [numbersign, asciitilde,   aring,   Aring ]	};

And saved it. Then the command:

# setxkbmap "gb(no2)" changed my keyboard to how I wanted it.

Upgrading to Ubuntu 8.04 removed my tweak, so it might be wise to follow the slightly more complex method in the link I gave.

Now for your problem. You could try out different keymaps, pick one that is fairly close to perfect, then add/change what you need to.

HTH

---

