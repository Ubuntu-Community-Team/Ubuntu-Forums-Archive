---
title: "[SOLVED] Fcron won't run gui's - I'm going crazy!!!!!"
date: 2008-11-30
forum: General Help
---

### Post by euphemus on 2008-11-30
[SIZE="2"]:mad: **HELP!**

I did fix this problem on my last box / installation. I have just upgraded and also installed Ubuntu 8.10 Ibex, and the problem has returned, but now I can't fix it.

I am trying to get fcron to run LimeWire (for now) but as before it won't launch.

**fcrontab -e =**
00 01 * * * * export DISPLAY=:0 && limewire [COLOR="Blue"]**[that is a no go]**[/COLOR]
also tried
00 01 * * * * export DISPLAY=:0.0 && /usr/bin/limewire [COLOR="Blue"]**[again no go]**[/COLOR]
I have also tried creating a .sh file [COLOR="Blue"]**[you guessed it]**[/COLOR]
but it worked just fine with export DISPLAY=:0 && limewire before.

**fcron is working: mail =**
Subject: fcron <"me"@euphemus> * export DISPLAY=:0 && limewire
From: fcron <"me"@euphemus>
Date: Sat, 29 Nov 2008 01:00:02 +1100

/bin/bash: AV: command not found
Job * export DISPLAY=:0 && limewire terminated (exit status: 127) (mailing output)

So I have done everything right from what I can remember. I have even stop / started the daemon [COLOR="Blue"]**[no not that either]**[/COLOR]

From what I can remember I had to update some file with a blah-blah-blah.so something-or-other - but can I find that page? [COLOR="Blue"]**[NO]**[/COLOR]

I have searched Google and Ubuntu forums for hours (+24) and nothing.

Please help.[/SIZE]

---

### Post by euphemus on 2008-11-30
I am an idiot - as soon as I posted this I noticed the problem - can you see it?

00 01 * * ***[COLOR="Blue"] *[/COLOR]** export DISPLAY=:0 && limewire
ONE TOO MANY *.

HAHAHA pwned myself!

It was all so simple. I'd delete this thread but I don't know how.

---

### Post by geirha on 2008-11-30
Seems limewire is failing because it can't find an executable called AV. Find out where it is, and put that in limewire's env.

```
0 1 * * * DISPLAY=:0 PATH=$PATH:/extra/path limewire
```

EDIT: Ah, so the * got expanded to AV, which wasn't an executable. That explains it.

---

### Post by euphemus on 2008-11-30
Next question: will I make it to the 2nd cup of Ubuntu :?:

---

### Post by geirha on 2008-11-30
> **euphemus said:**
> Next question: will I make it to the 2nd cup of Ubuntu :?:

No, I think it jumps from 1 to 5 :)

---

