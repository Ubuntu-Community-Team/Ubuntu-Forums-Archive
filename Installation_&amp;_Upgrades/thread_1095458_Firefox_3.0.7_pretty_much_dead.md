---
title: "Firefox 3.0.7 pretty much dead"
date: 2009-03-13
forum: Installation &amp; Upgrades
---

### Post by allspiritseve on 2009-03-13
OK, I have firefox 3.0.7 on my laptop. I assume it must have been upgraded by Synaptic, because I didn't manually upgrade. I have the following problems:

Home page doesn't show up
Bookmarks are gone (and can't import from backups).
Can't hit submit buttons
Ctrl+T opens a new tab, with the text from the old tab (very odd behavior)

Any ideas? What can I do to fix this? Is there a way to downgrade?

Cory

---

### Post by AlexDudko on 2009-03-13
Strange, non of the problems with my FF 3.0.7. Everything works just fine.

---

### Post by allspiritseve on 2009-03-13
I did start firefox as root before this happened, think that could have anything to do with it?

---

### Post by gjoellee on 2009-03-13
try this in the terminal:
```
firefox &
```

---

### Post by allspiritseve on 2009-03-13
Nope, same problems, though I can click submit buttons now. (That may have been a problem with firebug or something, I disabled all my add-ons to see if that helped)

---

### Post by allspiritseve on 2009-03-14
I deleted my profile and restarted, and everything is working. Just have to reinstall all my extensions...

---

### Post by phantom3113 on 2009-03-14
> **allspiritseve said:**
> I did start firefox as root before this happened, think that could have anything to do with it?

I believe that could have been it (though can't be certain). I've heard accounts of people that run graphical programs through sudo (or root) and end up messing something up. If you run gksudo next time, it shouldn't give you a problem. Granted, this is assuming you ran "sudo" initially anyway :P

---

### Post by allspiritseve on 2009-03-14
> **phantom3113 said:**
> I believe that could have been it (though can't be certain). I've heard accounts of people that run graphical programs through sudo (or root) and end up messing something up. If you run gksudo next time, it shouldn't give you a problem. Granted, this is assuming you ran "sudo" initially anyway :P
I usually run gksudo, but maybe I was being lazy at the time... dunno.

---

### Post by pizpot on 2009-03-16
I just updated ubuntu 8.10 and got Firefox 3.0.7 and firefox wants to be restarted even if I do. I rebooted. I did not run it with sudo. I assume nuking my .mozilla folder will do it, but it would be much nicer to know the actual fix, but I could not find it on mozilla's site yet. Cheers.

Edit: I  renamed my .mozilla folder and problem solved. I had already lost my add-ons, but bookmarks were fine. I do not notice any problem except for the restart ribbon bobbing up and down.

I did void my firefox warrenty, I guess. I went to about:config and searched for "sessions" and had set:

browser.sessionstore.enabled;false
browser.sessionstore.resume_from_crash;false

because that is the only way to be sure the last version would never show where you have been, to the next person to run it from the same linux account. ("always clear my data on exit" with all checked was not enough)

---

### Post by GDent on 2009-03-16
probably my odd firefox (3.0.6) behaviour is somehow related:

sometimes rightclick->open_in_tab opens add_to_favourites or mailto: dialogs, which leaves me in a rather confused and annoyed state.

rm -rf .mozilla ist not an option.

my config is default, except additional nocscript, adblock, stumble.

---

