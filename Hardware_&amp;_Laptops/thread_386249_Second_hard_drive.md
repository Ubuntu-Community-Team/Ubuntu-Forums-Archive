---
title: "Second hard drive"
date: 2007-03-16
forum: Hardware &amp; Laptops
---

### Post by Family_Guy on 2007-03-16
I have a second IDE hard drive that wasn't auto detected, i'm not sure how Ubuntu handles this. I was using it with windows and it has quite a bit of data on it, is there any way to mount it?

---

### Post by taurus on 2007-03-16
You can edit /etc/fstab and mount it from there.  Here's a guide.

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

Otherwise, post the output of this command from a terminal.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by esaym on 2007-03-16
I see this question come up ALL the time.  I know in kubuntu there is a manager for this that will automatically update fstab and stuff.  Ubuntu does not have something like this??? 

[[img]http://la.gg/thmb/screenshot6_1.png[/img]]("http://la.gg/upl/screenshot6_1.png")

---

### Post by esaym on 2007-03-18
> **esaym said:**
> I see this question come up ALL the time.  I know in kubuntu there is a manager for this that will automatically update fstab and stuff.  Ubuntu does not have something like this??? 

[[img]http://la.gg/thmb/screenshot6_1.png[/img]]("http://la.gg/upl/screenshot6_1.png")

Anyone?

---

