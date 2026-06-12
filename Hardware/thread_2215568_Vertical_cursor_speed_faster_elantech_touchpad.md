---
title: "Vertical cursor speed faster elantech touchpad"
date: 2014-04-07
forum: Hardware
---

### Post by pinecone3 on 2014-04-07
I'm running xubuntu 13.10 (currently off a live usb, I'm planning on installing properly if I can fix this issue) on an acer netbook, the touchpad has been detected as "ETPS/2 Elantech Touchpad".
It functions fine as far as I can tell except for the vertical cursor speed being significantly faster than horizontal, I've had this problem on other laptops as well with various distros but never found a fix, any ideas?

---

### Post by Kirboosy on 2014-04-07
I remember back in the 9.04 days you had to run the following command sometimes.

```

sudo modprobe -r psmouse
sudo modprobe psmouse proto=imps**
```**

I'm not sure if its still relevant or not. Its worth a shot though.

Hope that helps!
~Caboose

---

