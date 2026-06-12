---
title: "[SOLVED] What happens if i install &amp;quot;kubuntu-desktop&amp;quot; on ubuntu?"
date: 2008-10-13
forum: General Help
---

### Post by Noxn on 2008-10-13
The title says it all i think.

What exactly happens when i install the  "kubuntu-desktop" package (With apt-get) on my Ubuntu?

Just curiosity!

---

### Post by Gutt on 2008-10-13
You'll have a Kubuntu desktop, in other words before you login you can switch to KDE instead of having to be on Gnome.

---

### Post by Noxn on 2008-10-13
You mean like just at the login screen it ASKS you if you want to use Kubuntu desktop in that session or gnome?

---

### Post by howefield on 2008-10-13
It doesn't exactly ask you, at the login screen you click on the OPTIONS menu, then SELECT SESSIONS and and from there either KDE or GNOME.

---

### Post by SuperSonic4 on 2008-10-13
You select whichever one you want

---

### Post by b9k9kiwi on 2008-10-13
> **Noxn said:**
> The title says it all i think.

What exactly happens when i install the  "kubuntu-desktop" package (With apt-get) on my Ubuntu?

Just curiosity!

You will end up with the KDE desktop available as an option in the sessions dialogue at the login prompt - apt-get etc. will also download and install all the KDE associated applications and utilities (which you might not want to happen).

Like you, I was just curious, so I did 'apt-get install kubuntu-desktop' on my experimental/play PC.  Having then decided I didn't like KDE or, for that matter, the silly naming convention for KDE associated apps/utils, I discovered that getting rid of the KDE apps after uninstalling KDE was real headache.  My play PC hasn't got the hard disk real estate that my main machine has, so I wasn't keen to simply remove the KDE apps/utils from the Gnome menu - leaving them installed but not immediately available.

To tidy things up properly I had to zap the Ubuntu install and reinstall from scratch.

---

### Post by aysiu on 2008-10-13
Read this:
[http://www.psychocats.net/ubuntu/kde](http://www.psychocats.net/ubuntu/kde)

---

### Post by Noxn on 2008-10-13
Isnt there anyway of only having the KDE, without all the stuff?

Hmm, maybe if i get a bigger harddrive i would do it (in edit menus you can show/hide stuff).

:D


And thanks everyone.
This community is helpful and nice :D

---

### Post by aysiu on 2008-10-13
> **Noxn said:**
> Isnt there anyway of only having the KDE, without all the stuff?

Hmm, maybe if i get a bigger harddrive i would do it (in edit menus you can show/hide stuff).

:D


And thanks everyone.
This community is helpful and nice :D
```
sudo aptitude update && sudo aptitude install kde-core
``` would get you KDE "without all the stuff."

---

### Post by Noxn on 2008-10-13
Thank you.

And yes i know i am bad explaining things, and on top of that English inst my native language etc...


Anyway, that would still add the option to switch beetwen KDE and gnome, right?

---

### Post by aysiu on 2008-10-13
> **Noxn said:**
> Thank you.

And yes i know i am bad explaining things, and on top of that English inst my native language etc...


Anyway, that would still add the option to switch beetwen KDE and gnome, right?
Yes, but you'd get a bit more of a barebones KDE than Kubuntu.

---

### Post by Noxn on 2008-10-13
I just wanted to know how to do it, i still dont know if i want to try it.

btw: i saw some posts from you, when looking around the forum.
Looks like you are one of the most helpful persons here :KS

---

### Post by aysiu on 2008-10-13
I try to be helpful when I can. I hope you'll do the same for new users. Let us know if you have further questions.

---

### Post by Noxn on 2008-10-13
If i see someone i can help, i will.

But at the moment im more the guy that makes questions, instead of answering them, but meh, you have to start somewhere!

---

