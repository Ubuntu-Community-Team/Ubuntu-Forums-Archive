---
title: "[SOLVED] Conky v1.5.2 doesn't work with XMMS2 v0.5 DrLecter"
date: 2008-07-14
forum: General Help
---

### Post by LinuX-M@n1@k on 2008-07-14
I have just compiled XMMS2 0.5 DrLecter from git and conky-1.5.2_pre01116 from source.

When I start conky it says
> ...
Conky: xmms2 connection failed. Bad protocol version
Conky: xmms2 connection failed. Bad protocol version
Conky: xmms2 connection failed. Bad protocol version
...
and I can't monitor XMMS2.


During the installation of XMMS2, during ./configure I saw this warning messages, but I don't think it has something to do with conky:
```
xmms2.c: In function ‘handle_curent_id’:
xmms2.c:133: warning: passing argument 3 of ‘xmmsc_result_get_dict_entry_string’ from incompatible pointer type
xmms2.c:140: warning: passing argument 3 of ‘xmmsc_result_get_dict_entry_string’ from incompatible pointer type
xmms2.c:147: warning: passing argument 3 of ‘xmmsc_result_get_dict_entry_string’ from incompatible pointer type
xmms2.c:154: warning: passing argument 3 of ‘xmmsc_result_get_dict_entry_string’ from incompatible pointer type
xmms2.c:162: warning: passing argument 3 of ‘xmmsc_result_get_dict_entry_string’ from incompatible pointer type
xmms2.c:169: warning: passing argument 3 of ‘xmmsc_result_get_dict_entry_string’ from incompatible pointer type
xmms2.c:176: warning: passing argument 3 of ‘xmmsc_result_get_dict_entry_string’ from incompatible pointer type
xmms2.c: In function ‘handle_playlist_loaded’:
xmms2.c:261: warning: passing argument 2 of ‘xmmsc_result_get_string’ from incompatible pointer type
```

---

### Post by LinuX-M@n1@k on 2008-07-14
Need help solving it.

---

### Post by LinuX-M@n1@k on 2008-07-14
Can anyone reproduce this?

---

### Post by LinuX-M@n1@k on 2008-07-16
> **LinuX-M@n1@k said:**
> Can anyone reproduce this?

I guess no :///

---

### Post by LinuX-M@n1@k on 2008-07-19
This is another useless thread..................................

---

