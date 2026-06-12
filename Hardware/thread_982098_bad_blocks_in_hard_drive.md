---
title: "bad blocks in hard drive"
date: 2008-11-14
forum: Hardware
---

### Post by glok_twen on 2008-11-14
the simple version of the question would be what is the equivalent of scandisk in the linux world?

the more specific version is i have 4 disks in a 3ware raid unit. one of them has bad blocks. once i figure it out, 3ware says that i need to find a way to get it to "fix its own bad blocks". never done that before. is there something like scandisk that he says will do such a thing in the MS world?

thanks.

---

### Post by taurus on 2008-11-14
You can use fsck if it's a Linux filesystem.

```
man fsck
```

---

