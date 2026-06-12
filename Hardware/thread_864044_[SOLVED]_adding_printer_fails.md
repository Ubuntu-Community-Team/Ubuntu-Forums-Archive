---
title: "[SOLVED] adding printer fails"
date: 2008-07-19
forum: Hardware
---

### Post by nikosm on 2008-07-19
Dear community,

I installed ubuntu at my parent's computer a while ago and upgraded yesterday to hardy. The upgrade was a bit of an adventure (locales generation getting stuck, which seemed to be quite a common problem...) but I will post that separately.

I tried to install the old epson stylus color 440 and found that gutenprint had drivers for it, which I installed. I then went to System>Administration>Printing and tried to add a new printer, the "searching..." dialog showed up and then crashed. The /var/log/messages says

Jul 19 11:49:22 Platon kernel: [  253.248884] python[6260]: segfault at eba1eec0 eip eba1eec0 esp bfad431c error 5

Any ideas? Could it have something to do with the messy upgrade?

Thank you for your time,
Nikos

---

### Post by Vivaldi Gloria on 2008-07-19
> **nikosm said:**
> I then went to System>Administration>Printing and tried to add a new printer, the "searching..." dialog showed up and then crashed. 

That piece of crap always crashes. Try installing

```
gnome-cups-manager
```

or put the following adress 

```
http://127.0.0.1:631
```

in a webbrowser.

---

### Post by nikosm on 2008-07-19
> **Vivaldi Gloria said:**
> 

or put the following adress 

```
http://127.0.0.1:631
```

in a webbrowser.

Thanks! That did it.

Cheers,
Nikos

---

