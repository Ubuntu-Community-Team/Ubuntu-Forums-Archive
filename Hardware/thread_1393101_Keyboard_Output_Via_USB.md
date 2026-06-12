---
title: "Keyboard Output Via USB?"
date: 2010-01-28
forum: Hardware
---

### Post by Genkakuzai on 2010-01-28
Hello Forums,

I have an HP Mini with both Windows XP and Ubuntu on it. 

I also have a PlayStation 3 with an alternate Ubuntu installer CD running with kboot and I don't have my USB keyboard anymore.

So I'm wondering if there's a way I can basically use my laptop VIA USB to type on my PlayStation 3?

Hope it's possible...

---

### Post by IcarusR on 2010-01-29
Never heard of this being done. Try googling.

Easier to buy new USB keyboard, they are cheep enough.

Good luck !!!!!

---

### Post by Grenage on 2010-01-29
Hmm, maybe:

```
dd if=/dev/stdin | ssh -C username@ps3 dd of=/dev/stdin
```

From the PC with the keyboard.

---

### Post by Genkakuzai on 2010-01-29
I'll give it a shot. That'd be "bahdass" if I could get it to work. I'm at school right now, I will try it later.

Thanks

---

### Post by Genkakuzai on 2010-01-30
I still haven't tried this code yet but I wanted to make sure all know, that I do not have Ubuntu installed on my PS3 yet, just a Live Installer (Not CD), with Kboot Prompt. 

I will try the code soon and let you know what happens.

---

