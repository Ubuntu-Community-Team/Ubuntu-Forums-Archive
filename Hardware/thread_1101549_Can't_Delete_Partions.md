---
title: "Can't Delete Partions"
date: 2009-03-20
forum: Hardware
---

### Post by orc_dragoon on 2009-03-20
I f*** up ubuntu the other day. So now Im trying to delete all partions so I can try another linux ( Ubuntu Got boring), 

So I booted live with Puppy and Im using gparted to remove partions and Format drive, the problem 

is that 2 partions are locked. Can you help me.

---

### Post by taurus on 2009-03-20
You need to unmount your swap partition, /dev/sda5, first so the extended partition, /dev/sda2, can be unlocked.  Click the right button when /dev/sda5 is highlight and use the swapoff option.

---

