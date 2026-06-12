---
title: "Need to remove a Scanner"
date: 2011-02-13
forum: Hardware
---

### Post by Rasputin69 on 2011-02-13
Here is code I entered in to terminal:

------------------------------------------------------------------

Rasputin@Rasputin:~$ brsaneconfig3 -q | grep Brother
  0 Brother2            "MFC-5490CN"        I:192.168.0.100
  1 Brother             "MFC-5490CN"        I:127.0.0.1
------------------------------------------------------------------

I need to remove  1 Brother because it is assigned to the wrong IP address.

What is the command to remove it?

---

### Post by Rasputin69 on 2011-02-14
Solved:

sudo brsaneconfig3 -r <Name of scanner>

---

### Post by zzcortisone on 2012-04-13
Hey,

I've the problem, how did you solve it ??

Thanks,
Z

---

### Post by coffeecat on 2012-04-14
@zzcortisone, the OP has not logged in for more than a year. Please start your own thread if you need help.

Old thread closed.

---

