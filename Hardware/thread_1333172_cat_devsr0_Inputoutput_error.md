---
title: "cat: /dev/sr0: Input/output error"
date: 2009-11-21
forum: Hardware
---

### Post by zong1 on 2009-11-21
Linux ccd 2.6.28-16-generic #55-Ubuntu SMP Tue Oct 20 19:48:24 UTC 2009 i686 GNU/Linux

# cat /dev/sr0 > randomCD.iso
cat: /dev/sr0: Input/output error


Go figure! Anyone have any useful ideas how to solve.  
From /var/log/messages.


[ 4372.466023] end_request: I/O error, dev sr0, sector 0
[ 4372.466030] Buffer I/O error on device sr0, logical block 0
[ 4372.470497] end_request: I/O error, dev sr0, sector 4
[ 4372.470504] Buffer I/O error on device sr0, logical block 1
[ 4480.572544] end_request: I/O error, dev sr0, sector 0
[ 4480.572554] Buffer I/O error on device sr0, logical block 0
[ 4480.572561] Buffer I/O error on device sr0, logical block 1
[ 4480.572569] Buffer I/O error on device sr0, logical block 2
[ 4480.572574] Buffer I/O error on device sr0, logical block 3
[ 4480.572578] Buffer I/O error on device sr0, logical block 4
[ 4480.572583] Buffer I/O error on device sr0, logical block 5
[ 4480.572588] Buffer I/O error on device sr0, logical block 6
[ 4480.572592] Buffer I/O error on device sr0, logical block 7
[ 4480.578075] end_request: I/O error, dev sr0, sector 0
[ 4480.578085] Buffer I/O error on device sr0, logical block 0
[ 4480.582026] end_request: I/O error, dev sr0, sector 4
[ 4480.582033] Buffer I/O error on device sr0, logical block 1


PS.
Please don't post suggestions such as "use a CD playing programme, or its works well with Amorak, or why are you doing this as root, or cat!  thats not recommended - you know who you are :)

---

