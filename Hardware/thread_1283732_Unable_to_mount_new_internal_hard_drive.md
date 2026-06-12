---
title: "Unable to mount new internal hard drive"
date: 2009-10-05
forum: Hardware
---

### Post by the aftermath on 2009-10-05
I have a 250gb hard drive in my PC and just put in a new 2tb hitachi hard drive into the 2nd bay. When I turn on the system Ubuntu (9.04) is unable to mount the new hard drive. Everything is connected properly it's just not mounting for whatever reason :confused: What do I need to do to get it mounted? Thanks.

---

### Post by scragar on 2009-10-05
Install Gparted and check it's partitioned.
```
sudo apt-get install gparted
sudo gparted
```

---

### Post by miegiel on 2009-10-05
> **the aftermath said:**
> I have a 250gb hard drive in my PC and just put in a new 2tb hitachi hard drive into the 2nd bay. When I turn on the system Ubuntu (9.04) is unable to mount the new hard drive. Everything is connected properly it's just not mounting for whatever reason :confused: What do I need to do to get it mounted? Thanks.

New drives are empty of anything and need to be partitioned and formatted before use.

---

### Post by shaunsmith_99 on 2009-10-06
> **the aftermath said:**
> I have a 250gb hard drive in my PC and just put in a new 2tb hitachi hard drive into the 2nd bay. When I turn on the system Ubuntu (9.04) is unable to mount the new hard drive. Everything is connected properly it's just not mounting for whatever reason :confused: What do I need to do to get it mounted? Thanks.

 I don't have any useful tech help - but what kind of crazy stuff are you going to fill that 2TB HD with? Lots an lots of MP3s? Every movie ever made?:popcorn:

---

