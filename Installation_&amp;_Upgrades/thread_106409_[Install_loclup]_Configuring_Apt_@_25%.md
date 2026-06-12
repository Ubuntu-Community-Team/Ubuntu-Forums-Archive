---
title: "[Install loclup] Configuring Apt @ 25%"
date: 2005-12-20
forum: Installation &amp; Upgrades
---

### Post by Ouweneel on 2005-12-20
My install locks up @ 25% of configuring apt.

The message is like "Setting up primary ......."

Anyone knows what this is?

The messages in term #3 are like:

DEBUG: base-system

I'd tryd the 64 bit version and the 32 bit version (have AMD64 so both should work fine).

Thanks.

---

### Post by Ouweneel on 2006-02-22
I still have the same problem.
If i want to install kubuntu, it locks @ 25% of configuring apt.

Anyone ?

---

### Post by JuggyUK on 2006-04-04
[QUOTE=Ouweneel]My install locks up @ 25% of configuring apt.

The message is like "Setting up primary ......."

Anyone knows what this is?

The messages in term #3 are like:

DEBUG: base-system

I'd tryd the 64 bit version and the 32 bit version (have AMD64 so both should work fine).

Thanks.[/QUOTE]
Hello 

I'm new to Ubuntu  and I have found the similar problem with my installation of the software.
To understand what the problem is, try using Ctrl + Alt with the F1-12 (don't know which one) but it should give you a log file containing  error message of why Ubuntu is not installing.

Enjoy...

---

### Post by renzokuken on 2006-04-08
i feel your pain guys....i had the same problem........so actually i felt (past tense) your pain...mwuahaha

i dont what causes this problem, but the solution i used is this.....

PS you need an ethernet internet connection that is always on.....

1. Insert the install CD (really??)
2. Type "server" when asked to on the first screen to install just the base components.
3. When completed, you will be left at a black terminal screen.
4. At this screen simple type....

```
sudo apt-get install ubuntu-desktop gdm
```

this will install the ubuntu desktop onto the server giving u the full installation. this obviously requires downloading a fair chunk of files from the repos, but took about an hour for me on my 512mb connection

good luck

EDIT: heres the thread i posted back when i had this problem...... [http://www.ubuntuforums.org/showthread.php?t=76631](http://www.ubuntuforums.org/showthread.php?t=76631) .....should be some more help in there

---

