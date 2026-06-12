---
title: "Blocking two small ranges on memory"
date: 2009-12-31
forum: Hardware
---

### Post by Jordanwb on 2009-12-31
In a 1 Gig stick of RAM I have, there are four bad address in one very close spot, then another 2 in another close spot. Using this: [http://gquigs.blogspot.com/2009/01/bad-memory-howto.html](http://gquigs.blogspot.com/2009/01/bad-memory-howto.html) I can block the first section:

```
memmap=1M$542M
```

but how would I add another range? Can I use the actual memory addresses themselves?

---

