---
title: "I can't remove printers"
date: 2012-11-02
forum: Hardware
---

### Post by reginaldodr on 2012-11-02
Hello,

I'm using ubuntu 12.10. When I try to add or remove printer it's required login and password that it isn't root. The same occur in [http://localhost:631/](http://localhost:631/). How can I remove this login requirement?

---

### Post by dannyboy79 on 2012-11-02
are you a member of the lpadmin group?

```
sudo usermod -aG lpadmin yourusername
```

---

### Post by reginaldodr on 2012-11-08
Thanks dannyboy79, it's resolved my problem.

---

