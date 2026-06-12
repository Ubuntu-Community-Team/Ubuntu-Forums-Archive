---
title: "RAM reading"
date: 2008-07-06
forum: Hardware
---

### Post by Red-Shield on 2008-07-06
is there a way to read what is stored in a stick of ram ddr1 ddr2 ddr3

---

### Post by sdennie on 2008-07-06
Try either:

```

sudo dmidecode --type memory

```

Or

```

sudo lshw -C memory

```

---

