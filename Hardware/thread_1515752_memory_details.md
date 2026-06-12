---
title: "memory details"
date: 2010-06-22
forum: Hardware
---

### Post by boondocks on 2010-06-22
I only have ssh access to a remote system.
I need to find out:
[LIST=1]
[*]The number of memory slots on the motherboard.
[*]The number of used and available memory slots.
[*]The type of memory modules being used.
[/LIST]
How can I do this from just the command line?

---

### Post by lifeSum on 2010-06-22
Use this:
```
sudo dmidecode --type 17
```This will output information for each memory stick installed in the system, including the type. 

However, I'm unsure how to find out the # of slots on the motherboard via command line.

---

### Post by boondocks on 2010-06-23
> **lifeSum said:**
> Use this:
```
sudo dmidecode --type 17
```This will output information for each memory stick installed in the system, including the type. 

However, I'm unsure how to find out the # of slots on the motherboard via command line.

Thank you for this suggestion.  It helped.

---

### Post by dino99 on 2010-06-23
lspci -vv

---

