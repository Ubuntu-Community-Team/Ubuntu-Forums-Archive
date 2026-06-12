---
title: "dell laptop issues -- resolved!"
date: 2006-01-11
forum: Installation &amp; Upgrades
---

### Post by polkadotchickens on 2006-01-11
ok, this isn't a question, but after what i went through i want to make sure nobody else needs to go through the same, and so i want to put this information in a oft-searched place for answers.

i recently installed ubuntu 5.10 on my dell inspiron 2600 laptop, and the install seemed to go fine minus a quickly-fixed seizure-inducing screen flash, except once everything was done, x wouldn't start.  i kept getting an error message about no screens with useable configurations being found, no matter what i seemed to do to the xorg.conf file (working under strict guidance from a real geek, as i don't actually know anything about linux yet) and no matter what my real geek guide seemed to do.  tried messing with the drivers (the problem as previously documented on the internet seemed to center around the i810 chipset drivers), but it was all in vain.

fast-forward to a day of despair later: i find a little tiny aside in someone's blog rant about how dell is terrible about a disastrous problem with the bios.  the bottom line is this: apparently, no version of the bios for my computer higher than a08 will allow x to work.  period.

so, all you dell-laptop-owning, despairing people out there: downgrade your bios.  all of the old versions of the bios are still available on the dell website, support.dell.com, you just have to search for them.  then you just run it like an upgrade from the floppies you make, and voila!  x will start and you will have a happy linux system.

---

### Post by MacV on 2006-01-12
[QUOTE=polkadotchickens]ok, this isn't a question, but after what i went through i want to make sure nobody else needs to go through the same, and so i want to put this information in a oft-searched place for answers.

i recently installed ubuntu 5.10 on my dell inspiron 2600 laptop, and the install seemed to go fine minus a quickly-fixed seizure-inducing screen flash, except once everything was done, x wouldn't start.  i kept getting an error message about no screens with useable configurations being found, no matter what i seemed to do to the xorg.conf file (working under strict guidance from a real geek, as i don't actually know anything about linux yet) and no matter what my real geek guide seemed to do.  tried messing with the drivers (the problem as previously documented on the internet seemed to center around the i810 chipset drivers), but it was all in vain.

fast-forward to a day of despair later: i find a little tiny aside in someone's blog rant about how dell is terrible about a disastrous problem with the bios.  the bottom line is this: apparently, no version of the bios for my computer higher than a08 will allow x to work.  period.

so, all you dell-laptop-owning, despairing people out there: downgrade your bios.  all of the old versions of the bios are still available on the dell website, support.dell.com, you just have to search for them.  then you just run it like an upgrade from the floppies you make, and voila!  x will start and you will have a happy linux system.[/QUOTE]

How odd. How old is your laptop, I have a inpiron 8200 and never had problems putting various distros of linux on it. Kudos to you for figuring out your problem though.

---

### Post by danish_demon on 2006-01-12
i just purchased a dell b120 laptop which will be arriving tomorrow.  i hadn't heard anything about this before, has anyone else had this problem???

---

### Post by wanger123 on 2006-01-13
Some more info about he 2600:
[http://www.physics.ucsb.edu/~taro/comp/inspiron2600/install.html](http://www.physics.ucsb.edu/~taro/comp/inspiron2600/install.html)

wanger

---

### Post by RetroFreak on 2006-07-06
Yep, just discovered something similar here. Can't get Dapper to install at all, problems with X on the live CD, the alternate installer just gives me a black screen with 2 small cursor blocks, one in the middle of the screen, and one to the far left. So installed Breezy instead, and it failed to launch X, despite me running it on a 2600 previously. Further investigation revealed the laptop that it would work on has Bios rev A06, the one it wouldn't was A11. Re-flashed it to A06 it it works fine.

---

### Post by analyzer123 on 2007-10-22
any OS that forces me to downgrade my bios is a crappy one...go for windows instead!

---

### Post by smyrna112 on 2007-10-22
> **analyzer123 said:**
> any OS that forces me to downgrade my bios is a crappy one...go for windows instead!

Wow not to mock, but you are an insparation to us all....Windows! LMFAO

---

