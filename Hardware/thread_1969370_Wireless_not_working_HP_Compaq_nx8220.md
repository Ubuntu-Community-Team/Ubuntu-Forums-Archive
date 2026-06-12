---
title: "Wireless not working HP Compaq nx8220"
date: 2012-04-30
forum: Hardware
---

### Post by Ghost_Mazal on 2012-04-30
Morning all ,
 
As topic states , wireless doesn't work at all on 12.04. Worked on 11.10
There isn't even an option for "enable wireless" , it is greyd out.
 
Can someone help please ?
 
Thank you
 
Ubuntu 12.04 32 bit
HP Campaq nx8220 laptop

---

### Post by Ghost_Mazal on 2012-04-30
Some more information , at the top when I click on the network indicator it says:
 
"Wireless network disabled by hardware switch"
 
The "enable wireless" is greyed out.

---

### Post by Ghost_Mazal on 2012-04-30
Got it working with
 
```
 
sudo rfkill unblock all

```
 
:P

---

