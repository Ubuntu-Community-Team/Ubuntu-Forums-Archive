---
title: "Abiword spelling for language South African English"
date: 2009-04-21
forum: Installation &amp; Upgrades
---

### Post by majikins on 2009-04-21
Hi

Decide to post this as I did not find this while googling or searching these forums.  I install my Ubuntu workstations selecting English(South African) as language(as I am South African :-)  and I assume this is why the myspell-en-za dictionary gets installed.  Problem is this dictionary does not recognize words like "jumped" and "means" for instance.  Specifically in Abiword, one of the ways to fix is to do the following:

WARNING - USE AT OWN RISK!

1)Open terminal.
2)sudo cp /usr/share/AbiSuite-2.4/templates/normal.awt-en_ZA /usr/share/AbiSuite-2.4/templates/normal.awt-en_ZA.bak
(you are making a backup here)
3)sudo cp /usr/share/AbiSuite-2.4/templates/normal.awt-en_GB /usr/share/AbiSuite-2.4/templates/normal.awt-en_ZA (you are replacing the za dictionary with the english dictionary however Abiword still sees it as the South African Language)

According to the guru at the abiword irc channel, this is a hack and not an elegant solution - therefore as warned previously, you will be applying the above at your own risk!

Worked for me tho.  

Cheers
:popcorn:

---

### Post by adrianx on 2009-05-12
I've noticed the same problem in a few other applications - OpenOffice, Gedit, Firefox. So, something must be wrong with myspell-en-za.

---

