---
title: "screen + irssi =&gt; utf8"
date: 2005-11-16
forum: General Help
---

### Post by bugmenot on 2005-11-16
Hello!

I have a small problem with the display of certain charset characters with screen + irssi.

my system:
+ 'locale' - all is set to utf-8 ( de_DE.UTF-8 )
+ irssi's term_charset is set to utf-8 (same with: recode_terminal_charset & recode_default_charset)
+ I call irssi or screen from Gnome-Terminal (not xterm)


Problem:
If I run irssi from within screen the display of special characters by users with iso-xxxx charset is borked. Even starting screen with parameter -U (Tell screen to use UTF-8 encoding.) doesn't help.

So there seems to be a problem with irssi + screen, that I can't figure out..does someone has an idea?

Version-Info:
Ubuntu Breezy
irssi 0.8.10-rc5
screen 4.00.02

P.S.
Problem solved. Changed the settings for recode_terminal_charset & recode_default_charset back to iso-xxxx and it works now.

---

### Post by _kk on 2006-03-04
Hi there.

I have the same exact problem. I can't use the danish letters æøå. Could you elaborate on what you did to make it work.

I'm using PuttY to my Ubuntu box. When I set the charset to utf-8 in PuTTY I can write æøå and see my letters but it doesn't make sense when it's send.

---

### Post by _kk on 2006-03-04
Ok, I got it working... Some thread this is. Asking and answering our own questions... :)

I'll post my setting here for others to find:

What I use:
Ubuntu Breezy
irssi 0.8.10-rc5
screen 4.0.2
PuTTY 0.58

PuTTY is set to UTF-8. Then in irssi I set:

term_charset = UTF-8
recode_fallback = ISO8859-1
recode_out_default_charset = ISO8859-1

and that's it! Easy as pie :cool:

---

### Post by Klejs on 2006-03-13
Thanks! The /set term_charset UTF-8 worked for my swedish too...:D :D

---

### Post by gusto on 2007-10-20
I tried this with 7.10, and its not working. 
If I try to connect to a channel which name contains æø or å, it looks like I have joined. 
But I am all alone. 
And if I then check which channels I have joined with another client, I am joined some channel with weird characters. 

Any idea on how to get æøå to workin in screen + irssi now?


irssi 0.8.11
screen 4.00.03
putty 0.60

---

### Post by n0xie on 2007-11-22
Try this How-To:

[http://www.iovene.com/the-ultimate-guide-for-utf-8-in-irssi-and-gnuscreen/](http://www.iovene.com/the-ultimate-guide-for-utf-8-in-irssi-and-gnuscreen/)

---

### Post by tors on 2007-11-22
When I want swedish characters do be displayed correctly for me and for others when using irssi i use a program called "luit" to change the encoding:

```
luit -encoding "ISO 88591" irssi
```

Setting up an alias for this can be nice:

```
alias irssi='luit -encoding "ISO 88591" irssi'
```

Hope it helps!

---

