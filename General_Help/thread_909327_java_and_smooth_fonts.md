---
title: "java and smooth fonts"
date: 2008-09-03
forum: General Help
---

### Post by cb951303 on 2008-09-03
hello all, I use openjdk and I feel that netbeans ide's fonts are not smooth enough comparing to gnome (or maybe there is something wrong with my eyes)

so is it possible to enable subpixel smoothing in java apps globally?

thanks in advance

---

### Post by jespdj on 2008-09-03
Have a look at this: [http://www.jonathanhfisher.co.uk/b2/?p=93](http://www.jonathanhfisher.co.uk/b2/?p=93)
It's about Mac OS X, but probably the response by Martin Neumann is also useful on Ubuntu:
> from Chet Haase’s Blog ([http://weblogs.java.net/blog/chet/archive/2005/06/phils_font_fixe.html):](http://weblogs.java.net/blog/chet/archive/2005/06/phils_font_fixe.html):)

Q. How can I specify the text antialiasing/font smoothing settings to be used by Swing in applications on Java SE 6?

A. This is generally is a question from users of KDE or Windows 2000 who would like to use LCD subpixel text. There’s no programmatic way to do it in Java SE 6 (However if you know what you want you can set a system property :

java -Dawt.useSystemAAFontSettings=lcd
which request to use LCD subpixel text in the most common subpixel configuration There are a few more useful values for this property as follows :

“false” corresponds to disabling font smoothing on the desktop.
“on” corresponds to Gnome Best shapes/Best contrast (no equivalent Windows desktop setting)
“gasp” corresponds to Windows “Standard” font smoothing (no equivalent Gnome desktop setting)
“lcd” corresponds to Gnome’s “subpixel smoothing” and Windows “ClearType”

I hope this works for you…

---

### Post by cb951303 on 2008-09-03
because netbeans has its own executable I tried 

export _JAVA_OPTIONS='-Dawt.useSystemAAFontSettings=lcd'

but it doesn't seem to have an effect

---

### Post by nimrod_abing on 2008-11-20
> **cb951303 said:**
> because netbeans has its own executable I tried 

export _JAVA_OPTIONS='-Dawt.useSystemAAFontSettings=lcd'

but it doesn't seem to have an effect

Go into your Netbeans install directory. Look for the etc directory and open the file named netbeans.conf in your favorite text editor. 

Add the following to your netbeans_default_options:

```
-J-Dawt.useSystemAAFontSettings=lcd
```

---

### Post by StarQuake on 2009-11-26
That's the only thing I don't like about netbeans. I guess we're stuck with java's font rendering engine, instead of the OS one.

I use slight hinting in Gnome and there is no setting in java that looks like that.

---

