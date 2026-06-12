---
title: "xp/ubuntu 5.10 internet connection problem"
date: 2006-02-11
forum: Hardware &amp; Laptops
---

### Post by ianed on 2006-02-11
running duel boot xp/ ubuntu 5.10 on the same hd.
xp connects to net ok thru a via rhine2 ethernet adaptor.
restart xp to get into grub boot loader,ubuntu starts loading modules.
it hangs quite awhile at configuring network adaptors,when it does continue to load it fails to syncronize clock to ubuntu .org.
check network settings ETHO is showing as active is there a problem with xp/ubuntu sharng the same connection.
i suppose one out of two operating systems working is better than none.
would like to get the badger up and running to explore it deeper

---

### Post by coolclassic on 2006-02-12
You may have a dhcp problem can you open a terminal and run "ifconfig" and post the response.

---

### Post by ianed on 2006-02-17
ran ifconfig got etho / lo  it did not show any errors,i suspect it is normal with a good   connection.the conflict i think lies in the grub boot loader,i would image thats  where the connection priorities are set btween the two operating systems.any thoughts especially configuring the grub loader                            ianed

---

### Post by coolclassic on 2006-02-18
I didn't expect any errors to be shown, what I am intrested in is the address numbers given.

---

### Post by coolclassic on 2006-02-18
Also:
Your grub settings don't have anything to do with this.

---

