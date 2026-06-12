---
title: "about creating my own keyboard layout."
date: 2008-10-16
forum: General Help
---

### Post by alfonz19 on 2008-10-16
Hi,

I would like to ask how to create my own keyboard layout under linux (or ubuntu to be more specific). I already create one own layout, but now I need to do something more complicated and cannot find any answers.

Motivation: I need to work with two layout for two languagues. Both have some useless keys for me, and also some needed keys, but most of the keys are the same, including their positions. Then switching between these two brings problems such as situation, when you realise that you wrote a paragraph in wrong layout and you can rewrite it, because many of letters are wrong. Because I need to use arrow keys heavily I also want to place them to main part of keyboard, because I hate to search for "home position" for my right hand again and again.

Few question: I've looked in some layouts in directory /usr/share/X11/xkb/symbols/ Is the only allowed key combinatins of letter 'a': 'a', 'shift-a', 'alt_gr-a' and 'shift-alt_gr-a'? Or can I make key combinations with windows key for example (if I can, how to do that)? 

If I was right about key combinations in previous paragraph, then I need another hint(s). How to turn 'windows' key to be equal with shift-alt_gr key combination and eventually how to modify left alt key to be equal with alt_gr key (the motivation is simple: I need another set of keys which some letters can be assigned to, and which are on both side of keyboard).

thanks in advance
alfonz.

---

### Post by Icebear on 2008-10-16
there is some useful information at this site
[http://www.xfree86.org/current/XKB-Config.html](http://www.xfree86.org/current/XKB-Config.html)

---

### Post by alfonz19 on 2008-10-17
I read it through, and that article contain some usefull hints, but they are concerning mainly about setting up some existing layouts I want to use and shortcuts to switch between them.

But I want to create new layout (i.e. redefine key symbols) and make windows key to generate ****-alt_gr key combination (probably redefine some key codes rules or types of modifiers, I really do not know). And these questions resp. answers mentioned article does not contain.

Anyone know how to do it?

---

