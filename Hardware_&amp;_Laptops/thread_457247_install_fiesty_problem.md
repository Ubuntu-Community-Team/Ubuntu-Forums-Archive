---
title: "install fiesty problem"
date: 2007-05-28
forum: Hardware &amp; Laptops
---

### Post by joereith on 2007-05-28
i am trying to install fiesty from a live cd. I click on start or istall ubuntu and it says loading kernal and all those other things and whaen it says loading x it says ok then goes to a black screen with a blinking underscore line like the command propt and it just hangs up there.

how can i fix this problem?

---

### Post by taurus on 2007-05-28
Use the alternate CD.

---

### Post by ajgreeny on 2007-05-28
Or at the cursor login using your username and password chosen at installation time, and then try:-
**sudo dpkg-reconfigure xserver-xorg**
Most of the things can be accepted as they already are but most likely it is the graphic driver that is causing the problem.  If you know what your graphic card is then try the obvious choice for that (eg ati or nvidia) and when you get to the end, type **startx** and see if it all works.  If not repeat again with different driver such as vesa, which should work, at least to get you started.
Good luck!

---

### Post by joereith on 2007-05-28
aj it doesn't even start ubuntu from the cd it won't get that far

---

### Post by ajgreeny on 2007-05-28
OK, sorry I missed your meaning.  Agree with above post.

---

### Post by ijn on 2007-05-28
hi 
ok the only way is to:
download the alternate cd
install in text mode
at the end of installation u will have ubuntu graphical interface.

 in text mode be carefull to chose the right partition and mount partition that u want with this symbol (/)

it worked for me

---

### Post by joereith on 2007-05-28
i chose to download the kubuntu alternate and the option is to install from text. What will that require me to do any command promt stuff?

---

### Post by joereith on 2007-05-28
i am also installing over windows nt 2000. I need the cd to auto reformatt my hd

---

### Post by ijn on 2007-05-28
no command at all.
it's easy ,, and u 'll see yourself.
cause it's not in tty(black screen when y put commands on) but u have a minimalistic graphic where u see options and decide what to chose.use tab to selct and enter to chose.
just go for it:) have some of these before:popcorn:
bye

---

### Post by joereith on 2007-05-28
it just said entering low memory mode what do i do?

---

### Post by maksei on 2007-05-28
you didn't specify how much RAM etc. is available on your laptop.

it'd be  a safe bet to install from the alternate cd anyway

failing this, you could:

choose "install command-line system" option on the alternate cd
when installation is finished, do:
```

sudo apt-get install ubuntu-desktop

```

---

