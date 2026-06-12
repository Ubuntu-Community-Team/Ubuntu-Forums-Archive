---
title: "close to making speakers work.so close!"
date: 2007-05-02
forum: Hardware &amp; Laptops
---

### Post by Everywhere_at_Once on 2007-05-02
hey im trying to get my speakers to work on an lg p1, and i've seen on howto's that i have to take a  little file with one string in it, and copy it into /etc/modprobe.d BUT
i cant copy into modprobe.d, it wont let me.
it could be because my /home is on a seperate partition...

I have already tried sudo cp and sudo mv, to no avail.

suggestions are welcome!

---

### Post by josephus on 2007-05-02
what command are you using?   you can try either:

```
sudo cp <filename> /etc/modprobe.d/
sudo pico /etc/modprobe.d/<filename>
```

---

