---
title: "[SOLVED] special characters &amp;amp; keyboard"
date: 2008-10-31
forum: General Help
---

### Post by jesuisbenjamin on 2008-10-31
hello Forum

In the context of my studies i need to use intensively a certain amount of characters, i.e.:

[LIST]
[*]&#257;, &#299;, &#363; *
[*]&#347; **
[*]&#7693;, &#7717;, &#7735;, &#7747;, &#7751;, &#7771;, &#7779; and &#7789;
[*]&#7773;, &#7737;
[*]&#7745;, &#7749;
[/LIST]
* [I]These i managed to output with Alt+Shift+3, a or i or u.
** Success with ', s[/I]

Except for the case noted above i cannot output these characters unless i use the Character Map, which (when you have to work on a daily basis translations) is very inefficient.

I would like:
[LIST]
[*]Either to be able to create a simple combo (that is not a character number as it remains too long)
[*]Either to edit a new Keyboard Setting (lets say IAST - International Alphabet of Sanskrit Transliteration).[/LIST]

Is there anyone able to advise me on how to do that? Since Ubuntu has been able to be translated and transliterated in many other languages, this does not seem an impossible task to me.

Thanks for your support!

---

### Post by jesuisbenjamin on 2008-11-02
Poping it up!

---

### Post by jesuisbenjamin on 2008-11-04
i had hoped to catch a little attention with this question :|

---

### Post by der_joachim on 2008-11-04
You can either configure an international keyboard layout, with or without deadkeys, or configure a compose key. I prefer the compose key. Compose+'+a gives you an á, Compose+=+C gives you a &#8364;, et cetera. I am currently not on my Ubuntu box, so you'll have to use the search function. ;)

---

### Post by jesuisbenjamin on 2008-11-04
> **der_joachim said:**
> You can either configure an international keyboard layout, with or without deadkeys, or configure a compose key. I prefer the compose key. Compose+'+a gives you an á, Compose+=+C gives you a €, et cetera. I am currently not on my Ubuntu box, so you'll have to use the search function. ;)

Thanks. I am already using the US international keyboard, which provides the limited keys i mentioned above but won't provide all characters i need (obviously since there are thousands of possible characters with the IPA only).
The keyboard layout configuration does not provide me with the option to attribute some characters to certain keys.

What i would like to know is how to compose a full keyboard i.e. attributing characters to keys. This must be possible (or it wouldn't be Ubuntu ;) )

---

### Post by jesuisbenjamin on 2008-11-08
hello Forum,

Someone? Please?

---

### Post by kellner on 2008-11-08
You might want to take a look at [this thread]("http://ubuntuforums.org/showthread.php?t=665335"). 

Basically, there are two options I know of: design your own custom-made Xmodmap file (that you then need to run with the command "xmodmap", as in: "xmodmap Your_xmodmap_file"), or use xkb, which is the method described in the thread I linked to. 

I myself am having problems of getting either of these to fully work with Ubuntu 8.10 and am in the midst of troubleshooting at the moment.

---

### Post by jesuisbenjamin on 2008-11-15
All characters available with US international AltGr + keys on Ubuntu 8.10.
Thanks to the dev team \\:D/

---

