---
title: "Numpad keys stop working at some point"
date: 2008-02-25
forum: Hardware &amp; Laptops
---

### Post by metafile on 2008-02-25
Hello, Ubuntu people.

I'm using Ubuntu 7.10 and the problem is that at some point numpad keys of my keyboard stop working. Well, actually, they stop working normally and start working really weird.

This first happened with Genius Comfy KB-21e, when everything was okay until I suddenly noticed that numpad keys not working.

The keyboard was really old so I decided to replace it. While I was accumulating the force to take my butt off the chair and get to the store, apparently, gdm was restarted and the Numpad problem magically disappeared. I changed the keyboard anyway, and everything was fine with the new Logitech Media Keyboard's numpad until the problem revealed itself once again.

Regardless of numlock state, "1", "2", "3", "4", "6", "7", "8", "9", "/", "*", "-" and "." keys just don't respond.

"0", "5" and "+"... Well, I'm not really sure what do they do right now. I was just going to write "call some strange context menu" but while I was experimenting, some portion of this post went to clipboard and now pressing "plus" or "five" or "zero" just pastes that piece of text from clipboard.

The Numpad Enter key still works fine.

Does anyone have any idea about this?

P.S.: I don't use compiz and my system is i(dammit!)386 version, not 64bit one.
P.P.S.: This only happens in GNOME. In the console presented by Alt+Ctrl+F1 everything works fine.

---

### Post by Ballestein on 2008-04-25
In system->preferences->keyboard, turn off the "control mouse with keyboard"-option.

Worked for me :-)

---

### Post by h3_ on 2008-04-29
> **Ballestein said:**
> In system->preferences->keyboard, turn off the "control mouse with keyboard"-option.

Worked for me :-)

THANKS, had the same problem.. solved it.

Who the hell is the twit who made this useless option enabled by default in Hardy..

---

### Post by metafile on 2008-04-29
Thanks for the solution, but I'm still on Gutsy and I just can't find this checkbox in any tab of the "Keyboard Preferences" window.

All I got in the "Keyboard" tab is "Repeat Keys" and "Cursor Blinking".

---

