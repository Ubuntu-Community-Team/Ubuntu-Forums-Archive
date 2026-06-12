---
title: "Power Warning on a Mac mini"
date: 2013-07-02
forum: Hardware
---

### Post by raiserramon on 2013-07-02
I am running 12.04 on a Mac mini with an 2.3gb i5.  I keep getting a warning that I have low power and it gives me 3 options.  I shouldn't get a power warning because I am not using a battery.  Why is this happening?

---

### Post by newbie-user on 2013-07-02
Maybe the mac mini is being detected as a laptop? You could try deleting the laptop-detect package:
```
sudo apt-get remove laptop-detect
```

---

### Post by raiserramon on 2013-07-03
That didn't work.  I found this link about upowerd.  

[http://www.semicomplete.com/blog/geekery/disabling-battery-in-ubuntu-vms.html](http://www.semicomplete.com/blog/geekery/disabling-battery-in-ubuntu-vms.html)

---

