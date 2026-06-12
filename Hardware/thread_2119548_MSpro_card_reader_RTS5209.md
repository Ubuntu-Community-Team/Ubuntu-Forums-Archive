---
title: "MSpro card reader RTS5209"
date: 2013-02-24
forum: Hardware
---

### Post by rufus.wilson on 2013-02-24
Hi everybody,

I have ubuntu 12.10 installed on a sony vaio sv1312c5e and I have troubles to get my internal card reader to actually read sony memory stick pro duo. With stock ubuntu kernel the card reader is not recognized but it was with the 12.04.1 live cd. I currently have the latest kernel (3.8) installed and when I insert the card this is what I obtain:

```

# dmesg | tail -n 20
[  350.943209] memstick0: switching to 4-bit parallel mode
[  352.950500] mspro_block: probe of memstick0 failed with error -110

```Do you have any ideas how to get this thing working?

Thank you for your help,
Rufus

---

