---
title: "how to turn on sound"
date: 2005-09-11
forum: Hardware &amp; Laptops
---

### Post by faisalloe on 2005-09-11
how to turn on sound card.
i just install its not working ?

---

### Post by heimo on 2005-09-11
Run this on terminal (and show us the output):
 ```
lspci | grep -i 'audio\|snd'
``` 

Also same for this command:
 ```
lsmod | grep snd
``` 

Check that levels are up in volume contoller (should be on top panel, double click on it), also check and experiment with values in System->Preferences->Multimedia selector. Post your findings. 

Thanks!

---

