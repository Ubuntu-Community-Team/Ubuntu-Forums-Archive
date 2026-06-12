---
title: "how do i dual screen with a laptop?"
date: 2008-09-14
forum: Hardware
---

### Post by Gdschaf on 2008-09-14
i have an lcd tv pluged in and im getting the same picture on both my laptop monitor and the tv, can i change that shome how and the resolution so the tv isn't so screwed up?

---

### Post by shak541 on 2008-09-14
if you are using nvidia type in nvidia-settings into terminal and adjust from there.

---

### Post by Gdschaf on 2008-09-14
can u explain how to do that? i don't think its nvidia type though, i don't take interest in my laptop

---

### Post by howefield on 2008-09-14
What is the make and model of the laptop ?

---

### Post by Gdschaf on 2008-09-14
toshiba satalite A135-S4407

---

### Post by shak541 on 2008-09-14
go into applications-accesories-terminal. when that loads up type "nvidia-settings" with the quotes. when that loads up go into x server display configuration and it will show you both displays. click on your LCD and the resolution adjustment is just down below.
EDit: if you do not have nvidia-settings type: sudo apt-get install nvidia-settings  , into terminal to install.
edit 2: ok nvm sorry my instructions will not work because you have intel graphics on your laptop

---

### Post by Gdschaf on 2008-09-14
yeah i thought i had an intel graphics card, i just can't remember, is there ne way to do it with an intel graphics card?

---

### Post by howefield on 2008-09-14
think you will need to edit xorg.conf manually, sorry can't tell you what to enter, but hopefully someone will come along that can.

---

### Post by Gdschaf on 2008-09-14
yeah i found some people that have had luck with editing xorg.conf but honestly, i don't know where to find that :-/ im a novice, but everyones gotta start somewhere :-) how would i edit that than? i got what i think is a code that'll work

---

### Post by howefield on 2008-09-14
In a terminal (applications > accessories > terminal) type the following

sudo gedit /etc/X11/xorg.conf

Be careful, make a copy first, so you can get back to where you started if all goes wrong. To make a backup of the file, do this this first in a terminal.

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf-backup

---

