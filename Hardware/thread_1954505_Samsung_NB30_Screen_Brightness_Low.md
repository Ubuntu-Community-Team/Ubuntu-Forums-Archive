---
title: "Samsung NB30 Screen Brightness Low"
date: 2012-04-08
forum: Hardware
---

### Post by Snappa on 2012-04-08
As my first move into Linux, I have just installed Ubuntu 11.10 on my Samsung NB30.  The installation was straightforward, as was installation of Apache, PHP and mySQL, in fact these were much easier than in Windows !  However, I have a few problems which I want to address one by one.
The first problem is that the screen brightness is low.  I can access and change the brightness controls in System Settings | Screen and the Fn+F5+Arrow keys.  These both show full brightness, but even when I put them down to as low as possible, the brightness doesn't change at all.  
The "Dim screen to save power" checkbox is not checked.

How can I get more brightness from my screen ?
Thanks for any advice.

---

### Post by mardicas on 2012-04-08
Does pluging the power cord in changer anything?
Do other functions work with the Fn key?

The output of this command might help.
```
lspci | grep VGA
```

---

### Post by Toz on 2012-04-08
Fortunato Ventre has a PPA devoted to samsung notebooks. See: [https://launchpad.net/~voria/+archive/ppa?field.series_filter=oneiric]("https://launchpad.net/~voria/+archive/ppa?field.series_filter=oneiric")

It might help.

---

### Post by Snappa on 2012-04-08
Thanks guys.

The command   lspci | grep VGA   gives a response 
"00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller"

What does this tell me ?

Thanks for the pointer to Fortunato Ventre's site.  I'll have a look.

Pulling the power cord, and plugging in again does nothing to teh brightness.  In fact, it is always as if the netbook is running on battery.  The function key brings up the brilliance slider winodw, but this does nothing.  I'll try the other function keys this evening.

Cheers.

---

