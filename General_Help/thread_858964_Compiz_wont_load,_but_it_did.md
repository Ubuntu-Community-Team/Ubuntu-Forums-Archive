---
title: "Compiz wont load, but it did"
date: 2008-07-14
forum: General Help
---

### Post by mortuk on 2008-07-14
Hey all

I use hardy at work. Friday afternoon it was running fine and dandy.

I come in on monday morning and my PC is off. I suspect the cleaner as a) my 2 TFT's have nasty great smears down them like they have been cleaned with desk polish and b) my keyboard isnt in the upright position, its flat against the desk like someone got a duster and cleaned the keys with it not realising it was on :(

Anyways first thing I notice is that compiz wont load on boot. Have rebooted a few times now and no joy. Tried to run it via the terminal and now i get
```
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0194 (rev a2) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity 

```

Any ideas? Am using an nvidia graphics card, the nvidia CP works which it doesnt if the drivers arent loaded.

---

### Post by mortuk on 2008-07-15
bump anyone? :confused:

---

### Post by mortuk on 2008-07-22
anyone?? it just makes no sense that it happened over the weekend with no real interaction on my part

anything that happened to the machine was at random (ie a duster over the keyboard), so why do I no longer have working compiz?

---

### Post by overdrank on 2008-07-22
> **mortuk said:**
> anyone?? it just makes no sense that it happened over the weekend with no real interaction on my part

anything that happened to the machine was at random (ie a duster over the keyboard), so why do I no longer have working compiz?

Hi what is the model of graphics card? Also you may look at the FAQ's link in my signature and use compiz-check to help narrow down the issue.

---

### Post by moody_mark on 2008-07-22
Sorry to ask a really obvious question but you checked that no one has opened your box up and whipped out the cards or dislodged them? The only other thing is would your system have booted into another kernel image that doesnt have the drivers installed?

---

### Post by mortuk on 2008-07-22
its got an nvidia 8800 GTX

nope, its definitely not been dislodged as if so I wouldnt see anything ;)

also good thinking re: kernel version but no, it only has 1 version so cant be that either.

will try that compiz-check and report back, cheers

---

