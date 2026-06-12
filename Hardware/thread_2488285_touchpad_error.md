---
title: "touchpad error"
date: 2023-06-29
forum: Hardware
---

### Post by pyonecho86 on 2023-06-29
My laptop is Lenovo Thinkbook 15 G3 ACL. I installed Ubuntu 22.04. I am facing touchpad error. Touchpad is hot and not working sometime.

---

### Post by #&amp;thj^% on 2023-06-29
Ok this is not an easy magic bullet fix. (if at all)
Please show:
```
 xinput list

```
Mine shows an ID:16 
```
&#8627; MSFT0001:00 04F3:3140 Touchpad          	id=16	[slave  pointer  (2)
```
Now lets see if your using the right driver (also this is the hard part):
```
 xinput list-props 16 

```
Please wrap both of those in code tags to preserve the formatting.
If your unfamilar with Code Tags see my Signature.

---

