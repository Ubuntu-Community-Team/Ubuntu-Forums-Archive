---
title: "Keep same working directory after splitting in gnu screen"
date: 2013-09-28
forum: Hardware
---

### Post by CkDGTAT on 2013-09-28
Hi

I usually need to work in the same pwd after splitting. All I have found was

```
bindkey ^s eval stuff pwd > ~/.pwd^m split focus screen zsh stuff cd $(<~/.pwd)^m
```

which is far too slow for a long term use.

Thank you

---

