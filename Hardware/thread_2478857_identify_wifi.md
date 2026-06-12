---
title: "identify wifi"
date: 2022-09-06
forum: Hardware
---

### Post by bjlockie on 2022-09-06
How do I identify what wifi chipset I have?
I bough a Mediatek 7921k (wifi 6E) but I think I got a Mediatek 7921e (wifi6).
I don't have router that uses 6GHz anyways but still.

```
$ iw list
...
                VHT Capabilities (0x339071b1):
                        Max MPDU length: 7991
                        Supported Channel Width: neither 160 nor 80+80
```

---

### Post by &amp;KyT$0P# on 2022-09-07
Try
```
inxi -Nxxx
```
If you don't have inxi, you can install it with [FONT=Courier New]sudo apt-get install inxi[/FONT]

---

### Post by bjlockie on 2022-09-07
Thanks.

```
Network:
  Device-1: MEDIATEK driver: mt7921e
```

So it's a regular 7921 with no wifi 6e?
It is faster than my Intel AX200 I gave away so I'll keep it.

---

### Post by Yellow Pasque on 2022-09-08
> **bjlockie said:**
> ```
Network:
  Device-1: MEDIATEK driver: mt7921e
```

So it's a regular 7921 with no wifi 6e?

You can't tell just by looking at what kernel module is loaded. Give the full output of iw list.

---

