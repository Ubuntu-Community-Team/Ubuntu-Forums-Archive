---
title: "How can I find out what my netmask is?"
date: 2008-10-15
forum: General Help
---

### Post by sstecken on 2008-10-15
How can I find out what my netmask is?

---

### Post by brian_p on 2008-10-15
> **sstecken said:**
> How can I find out what my netmask is?

```
ifconfig
```

---

### Post by sstecken on 2008-10-15
Here's my reason:
Change "var HOME_NET any" to "var HOME_NET 192.168.0.0/16" (use your netmask here).

This is what ifconfig gives me.
inet addr:192.168.2.3  Bcast:192.168.2.255  Mask:255.255.255.0

Which of the three is the netmask winner?

---

### Post by issih on 2008-10-15
last one... 255.255.255.0

For home networks it is that 99.99% of the time

Hope that helps

---

### Post by Iowan on 2008-10-15
BTW, Mask:255.255.255.0 would translate (in your example) to 192.168.0.0/24 (255 decimal being binary 11111111)
[http://www.wolske.us/internet_tools/subnets_en.php]("http://www.wolske.us/internet_tools/subnets_en.php")

---

### Post by issih on 2008-10-15
Yes, I should have said that bit....thanks for following up :)

its 24 because the binary representation of 255.255.255.0 is 24 1's in a row (followed by 8 0's).netmask's are always 32 bits long in length and consist of a sequence of 1's then 0's to the end. The length of the sequence of 1's gives the number like 16 in your example.

In the case of 255.255.255.0 it is 24 ones in a row.

Hope that helps

---

