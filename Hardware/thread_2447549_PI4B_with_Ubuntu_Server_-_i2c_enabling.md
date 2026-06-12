---
title: "PI4B with Ubuntu Server - i2c enabling"
date: 2020-07-21
forum: Hardware
---

### Post by ottavio2 on 2020-07-21
Hi all,
I'm struggling why I'm not able to enable i2c on my Raspy 4B.
It is with Ubuntu server last version.
I googled and googled, I try all, but I don't understand how to.
Peraphs I need to enable a particular kernel module?
If yes, how can I do it?
Thank you very very much.
bye.

---

### Post by ottavio2 on 2020-07-22
I resolved :

 Added to /boot/config.txt  the following line:

  ```

dtparam=i2c_arm=on

```
  and to /etc/modules   the following line

  ```

i2c-dev 

```  So rebooted.
Now i2c is on.

---

