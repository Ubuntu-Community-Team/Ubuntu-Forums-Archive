---
title: "Samsung S6"
date: 2015-09-05
forum: Hardware
---

### Post by PedroPV on 2015-09-05
How can I connect my Samsung S6 phone to my Ubuntu 15.04 computer?
PedroPV

---

### Post by ajgreeny on 2015-09-05
Have a read through the info at [http://ubuntuforums.org/showthread.php?t=2226702](http://ubuntuforums.org/showthread.php?t=2226702) which may work for your S6.

---

### Post by efflandt on 2015-09-05
I never could get mtp to work properly in 12.04, but my Samsung S3 has worked without doing anything special in Ubuntu 13.10 and currently in 14.04. In the output of **lsusb** what shows for the group of hex digits after ID (actually after the 04e8: since I think the first part is the same for all Samsung)? If it is different than mine and not in /lib/udev/rules.d/69-libmtp.rules, maybe yours needs to be added to that file.

Bus 002 Device 006: ID 04e8:6860 Samsung Electronics Co., Ltd GT-I9100 Phone [Galaxy S II], GT-I9300 Phone [Galaxy S III], GT-P7500 [Galaxy Tab 10.1]

---

