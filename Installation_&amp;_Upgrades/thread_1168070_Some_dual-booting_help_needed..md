---
title: "Some dual-booting help needed."
date: 2009-05-23
forum: Installation &amp; Upgrades
---

### Post by StanleyKodak on 2009-05-23
Hello forum members,

I'm 16 in the USA, and have been having some recent fun with various 'flavors' of linux such as ubuntu, backtrack (of course :p), knoppix, pud linux, etc.  I have experimented mostly with ubuntu, and have so far only booted these operating systems in the following ways:

Running through VPC (mostly)
Running through a Live-CD
Running through my USB drive (PUD and Ubuntu...I got this to work at my school :D)

As I know that all of the above ways to run an operating system do not have the capability of showing me just how professional Ubuntu can be, I would like to dual-boot Vista(32-bit, which I am currently running) with Ubuntu 9.04.

While I would like to do this, I would also NEED the ability to uninstall the OS at any point, making the PC look as though Ubuntu had not even been there.  Basically, I want to intall linux, test it, and uninstall later that same evening, while not effecting Vista, as my parents don't know I'm doing this....

So, as I see it, I have 2 options:
-Figure out a way for this to work (with your help, of course :D)
-Find out what this Wubi thing is...(does wubi have access to everything, as Vista does?)

Which of these would be the best, most reliable means of testing Ubuntu even further, and how exactly would one go about doing so?

Thanks a lot,
StanleyKodak

---

### Post by lisati on 2009-05-23
There are different ways of "dual booting", each with its own pros and cons.

A "regular" dual-boot sets things up with each OS in a separate partition on the hard disk and and a new bootloader. One of the advantages is that if something goes wrong with one OS, it is less liklely to mess up the other. One disadvantage is that if you want to remove one OS permanently it can mean messing around with partitions, which can be a bit daunting to newcomers.

An installation through Wubi differs from a "regular" install is that it uses a special folder on the Windows partition and makes a note in the system so you can uninstall it from the Windows control panel. This can make things easier for newcomers. One disadvantage is that if Windows gets messed up it can hurt your Ubuntu installation.

There are probably other things that other users of the forum can mention.....

---

### Post by StanleyKodak on 2009-05-23
Sweet. I just did some googling for some info about wubi, and I think that this may be the best option.  As far as you know, does it have access to everything, just as Vista does? (Basically, I want my graphics to be decent :p )

---

### Post by presence1960 on 2009-05-23
not to put a damper on you, but being only 16 and it not being your computer, as a parent myself I am loathe to give you any suggestions. Why don't you run it by your parents first, especially since it is not your machine.

P.S. if you pursue without permission make sure you back up everything first- as anything can happen at any moment even with wubi. I don't think your parents would be too happy with data loss or a non-booting machine.

---

