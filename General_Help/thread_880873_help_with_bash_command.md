---
title: "help with bash command"
date: 2008-08-05
forum: General Help
---

### Post by huggy77 on 2008-08-05
basically need " du -hs /var/ftp"
to not display the path...


Doing some karumba programming and i am trying to get folder sizes.

---

### Post by y@w on 2008-08-05
I don't think there's a built-in way to do that with du. Awk is probably the way to go. Here's an awk primer. You'll probably want to start with the examples:

[http://www.vectorsite.net/tsawk.html](http://www.vectorsite.net/tsawk.html)

---

### Post by ghostdog74 on 2008-08-05
```

du -sh /path | awk '{print $1}'

```

---

### Post by ibuclaw on 2008-08-05
```
du -sh /path | cut -f 1
```

Regards
Iain

---

