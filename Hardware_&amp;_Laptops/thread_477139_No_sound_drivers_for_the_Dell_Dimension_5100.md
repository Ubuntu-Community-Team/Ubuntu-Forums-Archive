---
title: "No sound drivers for the Dell Dimension 5100"
date: 2007-06-18
forum: Hardware &amp; Laptops
---

### Post by Kzap333 on 2007-06-18
I'm not quit sure about the Ubuntu "Just Works" pholophy maybe it does just work WHEN YOU HAVE FINALY INSTALLED IT AND SET IT UP. I have final set it up and is is sort of working at (look at [http://ubuntuforums.org/showthread.php?t=469863](http://ubuntuforums.org/showthread.php?t=469863)). Now finally the only thing that stands between me and my Ubuntu experiance is sound. I don't hear any thing I think it must be the drivers. So does any one know where I can get some Linux ones my PC (by PC I mean Persnel Computer not Windows like every one is using it for at the moment) is a Dell Dimension 5100 and the sound card is SigmaTel High Definision Audio Codec. I realy need some help as I uses sound for every thing. Is there a genric Linux sound driver I can download that would do the trick.

---

### Post by renzokuken on 2007-06-18
could you post the output of 

```
lspci -v
```

---

### Post by Kzap333 on 2007-06-18
> **renzokuken said:**
> could you post the output of 

```
lspci -v
```

What do I type that into the terminal aplication or what.
*Sorry I'm kind of new to all this.*

---

### Post by renzokuken on 2007-06-18
yeah just open the terminal, type it in, hit enter and copy and paste the output into here

---

### Post by Kzap333 on 2007-06-18
> **renzokuken said:**
> yeah just open the terminal, type it in, hit enter and copy and paste the output into here

Thanks I'll do that when I get home I'm at school at the moment. In a ICT leason.:D

---

### Post by Kzap333 on 2007-06-18
I managed to get it working now thanks anyway.
I changed the setting from ALSD (or whatever you know what I mean) to the other one and took it off mute (I don't know why that was the defult.)

---

