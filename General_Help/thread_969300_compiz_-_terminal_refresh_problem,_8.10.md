---
title: "compiz - terminal refresh problem, 8.10"
date: 2008-11-03
forum: General Help
---

### Post by saladdin on 2008-11-03
Hello,

I'm new to ubuntu althouh not a linux-newbie. I have this new 8,10 version and what I can see that, with compiz running, my terminal.console window does not refresh correctly. Especially if the prompt line is at the bottom of the window. Changing viewport, minimizing window etc. helps but it's not very comfortable.
My graphics card is NVidia GeForce 9650GTM (Asus L50 laptop). NVidia drivers 177 are loaded and seem to work (screen resolution is fine).

---

### Post by saladdin on 2008-11-04
Solved. xfce-terminal works fine and looks the same.

---

### Post by MaNI3k on 2008-11-12
I have the same problem with it. Also in yakuake window.
Looks like there's something with 177 nvidia drivers.

Mario

---

### Post by reeksy on 2009-01-29
I have exactly the same problem. Every 5 commands or so the terminal wont refresh correctly. You have to hit return to get the window to refresh.

I actually dont find this too bad when typing commands, but it's a absolute nightmare whilst using vim!

Is using xfce-termina the only solution?

---

### Post by G-mL on 2009-04-12
Sorry to revive an old thread, but I had the same problem. Is xfce-terminal the only solution to this?

---

### Post by Mr. Frog on 2009-04-14
I have the exact same problem with Ubuntu 8.10 (up to date), nvidia 180 drivers.
All my terminals in my X are doing this, gnome-terminal, konsole, putty, wterm and even xterm!
xterm is more usable than the others, at least, the text scrolls up, but some sections of the term is just blank until I click on the window and hit enter or something like this.
Even x3270 (infoman...) is doing that sometimes!

I am a unix admin, I use my laptop with Ubuntu at work on AIX, Sun and Linux servers, so this is quite annoying.

Is there something to do about this, except by disabling compiz?

Thanks

---

### Post by skipy on 2009-04-15
I have the same problem for Ubuntu 8.10 fully updated, nVidia 180 drivers.
I think the problem has something to do with the 180 drivers, as I did not have this problem a month ago (when these drivers were not available).

Thanks!

---

### Post by skipy on 2009-04-15
Some more intel (sorry for doubleposting):
I falled back to 177 nvidia drivers and the terminal seems to work fine now.
I'll just wait for the next version, which hopefully will be fixed.

Pretty lame for a drivers version to introduce a bug that was not present in the previous ones, isn't it? boo nvidia!

---

### Post by Mr. Frog on 2009-04-16
I had the same problem with nvidia-177.
As the others said, xfce-terminal is working fine for me for now!
That's weird, but at least, it looks almost the same as gnome-terminal!

---

### Post by Mr. Frog on 2009-04-16
ok there's still some glitches, but I can work in vi!

---

### Post by xme on 2009-05-04
Hmmm...

Same config, same symptoms here!
Is the downgrade to version 177 of Nvidia drivers the solution?

Otherwise, I'm still waiting to upgrade to 9.04. Maybe the problem is solved with the new release? Feedback anybody?

Tx!

---

### Post by Mr. Frog on 2009-05-04
I upgraded last week to 9.04 and from what I can see, it looks fixed!
Not sure how and not sure why, but it doesn't happen like it was before!
There is some refresh glitchs with some others apps, but it is not as bad as it was with the terminals!

---

### Post by xme on 2009-05-05
Finally, I decided to upgraded to 9.04. Driver version 180.44 was natively installed with the new release. 

Everything went smoothly and the nasty is now fixed! Enjoying the new release now ;-)

---

