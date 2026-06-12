---
title: "Making sure uswsusp uses my swap partition"
date: 2008-08-31
forum: Hardware
---

### Post by LPShred on 2008-08-31
I just setup uswsusp so that I can hibernate without a problem.  However, when I configured the program I wasn't sure what I was doing at half of the prompts.  I created a specific swap partition and I wanted to know if I could check to see if it is being used.

---

### Post by VMC on 2008-08-31
> **LPShred said:**
> I just setup uswsusp so that I can hibernate without a problem.  However, when I configured the program I wasn't sure what I was doing at half of the prompts.  I created a specific swap partition and I wanted to know if I could check to see if it is being used.

From a terminal type "swapon -s" , it will show swap info. If size is zero then you need to turn swap on.

---

