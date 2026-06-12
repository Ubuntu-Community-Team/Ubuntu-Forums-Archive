---
title: "Hard disk read only"
date: 2006-01-26
forum: Hardware &amp; Laptops
---

### Post by christooss on 2006-01-26
Yesterday I was deliting some things from a disk. I forcely stoped with unpluging the cabel of the computer. I know very stupid thing but it was taking to damn long :) And I m tired of waiting. So I think there is only one porblem that I have to solve. That is to remove .Trash-xxx from this disk.

this is out put of # ls -la
```

drwxr-xr-x  7 matic matic      4096 2006-01-26 02:18 .
drwxr-xr-x 14 root  root       4096 2006-01-24 19:44 ..
drwxr-xr-x  4 matic root       4096 2006-01-25 12:50 dsslive
drwx------  2 root  root      16384 2006-01-19 00:18 lost+found
-?---------  ? ?     ?             ?                ? .Trash-matic

```

You se there is no group and user ownig that dir

---

### Post by fmo on 2006-01-26
I suggest that you reboot you machine and force a fsck to check the integrity of your disk by doing a "shutdown -F now" without the brackets.

---

