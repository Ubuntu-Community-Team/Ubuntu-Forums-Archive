---
title: "Hardy suddenly not booting"
date: 2008-08-23
forum: General Help
---

### Post by nscreed15 on 2008-08-23
Well this morning I turned on my computer, everything fine. Noticed there were some updates so I installed them. After about an hour my computer froze, no big deal so I restarted. I typed in my username and password, hit enter, and it freezes. So I reboot AGAIN, and it freezes at the orange loading bar about 1 1/2 boxes in... I popped in my Hardy Live CD, same thing... freezes

Then I read that unplugging my harddrive and booting to live cd might help, but it didn't. Eventually I swapped the video card out (XFX 8600 GTS was the graphics card I had been using) to a very old PCI graphics card(made in 1999, i'll look up the specs on it later) and it boots fine with the Live CD.

So, thinking its the graphics card I tried my 8600 in another computer, and it worked... I'm stumped as to why Ubuntu suddenly stopped working. Any help would be greatly appreciated!!

---

### Post by nscreed15 on 2008-08-24
Bump

Any help please? I really like Ubuntu and don't want to go back to Windows...

---

### Post by linux_tech on 2008-08-24
Did you try booting in recovery mode?

---

### Post by caljohnsmith on 2008-08-24
> **nscreed15 said:**
> Well this morning I turned on my computer, everything fine. Noticed there were some updates so I installed them. After about an hour my computer froze, no big deal so I restarted. I typed in my username and password, hit enter, and it freezes. So I reboot AGAIN, and it freezes at the orange loading bar about 1 1/2 boxes in... [COLOR="Blue"]I popped in my Hardy Live CD, same thing... freezes[/COLOR]

Then I read that unplugging my harddrive and booting to live cd might help, but it didn't. Eventually I swapped the video card out (XFX 8600 GTS was the graphics card I had been using) to a very old PCI graphics card(made in 1999, i'll look up the specs on it later) and it boots fine with the Live CD.

So, thinking its the graphics card I tried my 8600 in another computer, and it worked... I'm stumped as to why Ubuntu suddenly stopped working. Any help would be greatly appreciated!!
That Hardy Live CD that freezes--were you previously able to boot into it OK? Or have you never been able to boot that Live CD when using your XFX graphics card?

If you can boot up any Live CD with your XFX graphics card, try mounting your Ubuntu partition and looking in the /var/log/dmesg and /var/log/syslog files (for example) to find what errors are occurring when you boot Ubuntu. That might give some useful clues.

---

### Post by nscreed15 on 2008-08-24
The XFX graphics card is the card I cannot boot anything with. I went from Ubuntu Feisty to Hardy a couple months ago using the same CD(used the Live CD to check it out before installing, worked fine.)

And it locked up going into recovery mode.

The only thing I changed was the updates and I updated my IPTables for azureus. I used a code off of another site that looked the same as the one on the Ubuntu site(When i try the suggestions you gave i'll check the email address in the history). Maybe it could be the problem.

I'll post back

---

### Post by nscreed15 on 2008-08-25
My graphics card AND monitor died Saturday >.< When I get em both replaced i'll try and fix ubuntu again.

---

### Post by Crafty Kisses on 2008-08-25
> **nscreed15 said:**
> My graphics card AND monitor died Saturday >.< When I get em both replaced i'll try and fix ubuntu again.

By died do you mean like a issue with Linux or the hardware went bad.

---

