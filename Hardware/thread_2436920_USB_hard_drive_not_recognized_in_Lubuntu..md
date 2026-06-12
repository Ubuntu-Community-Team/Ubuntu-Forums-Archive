---
title: "USB hard drive not recognized in Lubuntu."
date: 2020-02-15
forum: Hardware
---

### Post by BADGER.BRAD on 2020-02-15
Hello all,

I have purchased a USB 3,0 hard drive but Lubuntu does not see it at all when I go to file manager. Have you any ideas ? please note I'm only a user of Lubuntu and other than that have no technical knowledge. One thing I do noticed is that when plugged in to the PC's USB'S the light on the hardrive flash's and in the other it remains constant ,not sure if that is relavent.

Thanks all.

Brad

---

### Post by sudodus on 2020-02-15
Are you willing to try some command lines in a terminal window? In that case I can suggest that you start with

```

lsusb

```
and
```

sudo lsblk -f

```

Copy and paste the output into a reply here.

[hr][/hr]
Please post the output between code tags like this
 
[noparse]```

output

```[/noparse]
 
to get output like this
 
```

output

```

Edit: You can also try with

```

sudo lsblk -o name,fstype,size,label,vendor,model

```

and edit the output into a reply.

---

