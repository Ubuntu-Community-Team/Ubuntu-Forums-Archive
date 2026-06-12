---
title: "unmount  /dev/sda5"
date: 2009-09-25
forum: Installation &amp; Upgrades
---

### Post by manojpawar on 2009-09-25
Thank you for Reply,
   I have executed following command according to your reply, 

(parted) resize 5 176136723 381575941

But I am getting following error:

Error: Partition /dev/sda5 is being used. You must unmount it before you modify
it with Parted.

again i have given command as
root@Crayom:/home/crayom# sudo umount /dev/sda5
then i got
umount: /: device is busy.

 please help

---

### Post by junke1990 on 2009-09-25
i dont know what reply you are talking about so...

is sda5 your / partition, aka your partition where Ubuntu is installed?

---

