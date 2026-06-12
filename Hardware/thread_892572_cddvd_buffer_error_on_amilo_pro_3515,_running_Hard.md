---
title: "cd/dvd buffer error on amilo pro 3515, running Hardy Heron"
date: 2008-08-17
forum: Hardware
---

### Post by lambdapants on 2008-08-17
Repeating the subject; I get a buffer error when trying to play a dvd in mplayer , using hardy heron, on my amilo pro 3515 laptop:

heres some dmesges

[28383.799097] Buffer I/O error on device sr0, logical block 212218
[28383.799102] Buffer I/O error on device sr0, logical block 212219
[28383.799105] Buffer I/O error on device sr0, logical block 212220
[28383.799108] Buffer I/O error on device sr0, logical block 212221
[28383.799111] Buffer I/O error on device sr0, logical block 212222
[28383.799113] Buffer I/O error on device sr0, logical block 212223
[28383.799116] Buffer I/O error on device sr0, logical block 212224
[28384.120843] end_request: I/O error, dev sr0, sector 852052
[28384.535036] end_request: I/O error, dev sr0, sector 882648
[28384.701613] end_request: I/O error, dev sr0, sector 882652
[28384.826764] end_request: I/O error, dev sr0, sector 882648

also I cannot play cds, but dmesg shows no errors when i try to play them.

spoon@utensil:~$ uname -r
2.6.24-19-generic

Strangely though, I can mount and read the contents of dvds.
Any thoughts?

---

