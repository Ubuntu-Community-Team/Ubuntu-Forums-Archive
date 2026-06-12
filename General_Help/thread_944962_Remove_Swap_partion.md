---
title: "Remove Swap partion"
date: 2008-10-11
forum: General Help
---

### Post by kramdish on 2008-10-11
Hello,

I was wondering if there is a way to totaly remove the swap partion from a kubuntu instalation.
I have a dual boot with win vista and kubuntu 8.04.

Could someone help me out with a handy guide? Thanks

---

### Post by bodhi.zazen on 2008-10-11
First edit fstab ;

```
kdesu kate /etc/fstab
```

Remove the line with swap on it.

the boot a live CD, start gpared and delete the swap partition. Next add the new free space to another partition (two steps with gparted).

---

