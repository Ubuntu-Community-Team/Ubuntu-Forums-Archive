---
title: "hwclock - BIOS clock not ticking"
date: 2010-03-25
forum: Hardware
---

### Post by steveneddy on 2010-03-25
I know I have asked this before and solved it in other versions of Ubuntu - BUT - again the BIOS clock will not tick, the system won't boot past GRUB (will boot if manually choosing a kernel) 

I just can't remember how I fixed it last time. I just need Intrepid to work until Lucid comes out of Beta.

I remember that it was a simple command, but just can't seem to find it on the forums again.

wish I had bookmarked it last time.

Any help appreciated.

Intrepid - 2.6.27-17-generic - 64 bit - 

consequently - the laptop won't wake from sleep mode either

Thanks in advance

---

### Post by steveneddy on 2010-03-25
Fixed

```
sudo gedit /etc/init.d/hwclock.sh 
```

add --directisa

to the line

```
HWCLOCKPARS=
```

so it looks like this

```
HWCLOCKPARS=[COLOR="Red"]--directisa[/COLOR]
```

I rebooted and seems to be working correctly.

After logging in I checked the hwclock by

```
sudo hwclock
```

and it printed to screen the correct output without timing out.

---

### Post by Sef on 2010-03-26
OP asked for the thread to be closed.

---

