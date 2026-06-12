---
title: "CD reader error"
date: 2014-05-20
forum: Hardware
---

### Post by The musmula on 2014-05-20
Not sure if this has anything to do with ubuntu, but here it is:

I have an old HP Compaq 6720s and I am trying to load CDs on it, the problem is that he wont recogniye any cd that I input.
I first noticed it when I was trying to install ubuntu on it, now I am on a live usb, but when I input a data dvd (or cd) it wont load it.... Is that because it is on a simlated live cd (just a wild theory of mine) or because its broken?

---

### Post by sudodus on 2014-05-20
Usually the CD drive is recognized and works well unless it is broken.

Check and post the output of the following command

```
sudo lshw -short|grep disk
```

It should list one line with something like '/dev/cdrom' and data about the brand name or model or both. Otherwise the system does not see it properly.

---

### Post by The musmula on 2014-05-23
em, It is not running at all anymore... doesent matter I1ll switch to usbe then, thanks for the help anyway

---

