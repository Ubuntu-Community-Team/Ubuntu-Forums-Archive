---
title: "Problem with NVIDIA X Server Settings..."
date: 2008-07-31
forum: Hardware
---

### Post by Animeniac on 2008-07-31
Whenever I click 'Save to X Configuration File' under 'X Server Display Configuration', I click save and then I get the error "Unable to create new X config backup file '/etc/X111/xorg.conf.backup'".

How do I fix it?

---

### Post by overdrank on 2008-07-31
> **Animeniac said:**
> Whenever I click 'Save to X Configuration File' under 'X Server Display Configuration', I click save and then I get the error "Unable to create new X config backup file '/etc/X111/xorg.conf.backup'".

How do I fix it?

Hi and are you root with the nvidia-settings   ```
gksu nvidia-settings
```

---

### Post by Animeniac on 2008-07-31
Thanks, overdrank. That solved the problem. I should make a "Tomboy" note of that code.

---

### Post by RuiMMSousa on 2008-08-06
I got exactly the same problem.

Tks overdrank, that works for me too :razz:

---

### Post by sfabel on 2008-08-06
> 
I should make a "Tomboy" note of that code.


No need, just edit the menu entry accordingly.

---

