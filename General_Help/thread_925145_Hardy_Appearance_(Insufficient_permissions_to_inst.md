---
title: "Hardy: Appearance (Insufficient permissions to install the theme)"
date: 2008-09-20
forum: General Help
---

### Post by Genjinaro on 2008-09-20
This is the theme I am using:
[http://maketecheasier.com/turn-your-ubuntu-hardy-to-mac-osx-leopard/2008/07/23](http://maketecheasier.com/turn-your-ubuntu-hardy-to-mac-osx-leopard/2008/07/23)

This particualr part:
[IMG]http://maketecheasier.com/wp-content/uploads/2008/07/appearance-customize.jpg[/IMG]

Somehow after using the theme for a week, no issues. One day after booting up, its gone:confused:

Ok, no problem. I still have the files, I can re-install (or so I thought) asd I could before but out of the blue I get hit with this message:

Insufficient permissions to install the theme in:
/home/georgegrw/.themes


? Ok, so I try to attempt aback door approach by doing sudo gnome-appearance-properties but it only works for "that" gnome window. :(

What is going on here, why do I mysteriously "lack" permisions to install themes to "my" desktop?

Is there a way to "fix" this?










Not sure how much detail I need to give but I'm running:

UbuntuEee 8.041 (Hardy Heron) Gnome desktop.

---

### Post by Genjinaro on 2008-09-20
? Even odder, after a full shutdown and boot things are back to norm. 

Still theres an uneasy gap of "why"...

EDIT, crap no this was a fluke. not working.

---

### Post by Genjinaro on 2008-09-22
Anyone...? *Getting views like crazy*

Should I file a bug report?

---

### Post by maaaatteo on 2008-10-25
> [QUOTE=Genjinaro;5835373]
> Anyone...?

me, but just for a moment.. :-s

```
 gnome-appearance-properties -i %u

```

was reporting the same message posted in the subject,and i was not allowed to do any change.

but now, it says ```
"%u" does not appear to be a valid theme.
```
and then it works.

WTF???

:confused: ](*,)

---

