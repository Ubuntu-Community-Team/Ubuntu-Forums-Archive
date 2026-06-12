---
title: "Cannot install Feisty or Gutsy RC on IBM z61m"
date: 2007-10-16
forum: Hardware &amp; Laptops
---

### Post by phazer on 2007-10-16
Boot of the live CD, goes all the way until it needs to start Gnome up and then it fails...

Anyone got any ideas...quite annoying as I had a z60m previously and everything worked 100% this z61m is a company upgrade.

---

### Post by blenderfish on 2007-10-18
It sounds like you are having the same problem I had when I installed Feisty on my z61m.  It has something to do with the LiveCD not having the proper video drivers for your card.  The solution was to apt-get the fglrx drivers after the system had crashed to console on boot.  I can't remember the exact steps, but if you search around the forums, you'll find them.  

Also, you could always boot from the Alternate CD and everything should go fine once you have it installed.

Good Luck!

---

### Post by mzuther on 2007-10-25
Hello phazer!

I had the same problem as you, but managed to fix it using this (very long) link:

[http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.04_on_a_ThinkPad_Z61m#Live_CD_plus_Internet]("http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.04_on_a_ThinkPad_Z61m#Live_CD_plus_Internet")

Here is what I did:

I started from the Ubuntu Gutsy Gibbon CD-ROM using the first option ("Start or install Ubuntu") with a network cable plugged into the ThinkPad. When Ubuntu failed to start Gnome, I used CTRL-ALT-F6 to get into a console. You might have to repeat that key stroke a few times, as the system goes on trying to start Gnome...

*The letters in the console were horribly big and not everything was shown. So when things went offscreen, I used the commands "ls -l" to scroll down a little and "clear" to move the cursor back to the top of the screen.*

Here are the commands you have to type (don't type the dollar sign, though, it just indicates you're typing in the console):

```
$ sudo apt-get update
$ sudo apt-get install xorg-driver-fglrx
```

You might have to enter a "y" (for "yes, please install this driver") at this point. I had a small fight at that point because everything was offscreen and I had forgotten that on German keyboards "y" and "z" are exchanged... ;)

```
$ sudo depmod -a
$ sudo aticonfig --initial
$ startx
```

At this point Gnome should start and you can install Ubuntu on the ThinkPad. If it doesn't, you can try to reboot by pressing CTRL-ALT-DEL and start all over again.

After installing Ubuntu, I rebooted the system. Ubuntu started from the harddisk, but guess what - Gnome didn't. Instead, the graphics repair tool started. But I decided to go the plain way and just repeated the above steps. Gnome started, and since then no problems have arisen.

I hope I could help you a little. All the best,

Martin

---

### Post by namaste on 2008-01-05
Hi mzuther,
Many thanks:). Following your instructions with many 'clear's worked. I had tried FF but it wouldn't install at all. I was almost at the point of giving up wth GG! LOL namaste.

---

### Post by mzuther on 2008-01-06
That's great - I feared you didn't make it... ;)

All the best,

Martin

---

