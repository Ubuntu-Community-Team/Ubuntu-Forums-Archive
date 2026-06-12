---
title: "usb error (wont mount)"
date: 2008-12-12
forum: Hardware
---

### Post by inxygnuu on 2008-12-12
Just today, when i put in my cruzer micro usb, an error came up saying: 
> Error org.freedesktop.Hal.Device.UnknownError. 
what does this mean and how can i fix it?

Thanks in advance,
3v4n

---

### Post by inxygnuu on 2008-12-27
bump

---

### Post by inxygnuu on 2008-12-28
once again... bump (i know there is an answer)

---

### Post by Rohan Kapoor on 2008-12-29
> **inxygnuu said:**
> once again... bump (i know there is an answer)

[https://bugs.launchpad.net/ubuntu/+source/hal/+bug/292874](https://bugs.launchpad.net/ubuntu/+source/hal/+bug/292874)

This is launchpad bug regarding this. You should use Google, it is your friend. There may be help located there. If not developers are looking into it.

---

### Post by inxygnuu on 2008-12-29
> **darth-vader said:**
> [https://bugs.launchpad.net/ubuntu/+source/hal/+bug/292874](https://bugs.launchpad.net/ubuntu/+source/hal/+bug/292874)

This is launchpad bug regarding this. You should use Google, it is your friend. There may be help located there. If not developers are looking into it.

Actually, i just looked, and there are bugs, but I am the only thread!:(

---

### Post by Rohan Kapoor on 2008-12-29
> **inxygnuu said:**
> Actually, i just looked, and there are bugs, but I am the only thread!:(
Yes you are the only thread. Just watch the bug report and it should eventually (hopefully) be sorted out.

---

### Post by dxdemetriou on 2009-03-24
Anyway, because it seems that this problem it'll not be solved until the next release, I'm posting two scripts I wrote for mounting and unmounting.
They are using the mountpy package and I'm using them with xbindkeys.

Edit: [https://bugs.launchpad.net/ubuntu/+bug/292874/comments/7](https://bugs.launchpad.net/ubuntu/+bug/292874/comments/7)
> 

I found the problem finally
[https://bugs.launchpad.net/ubuntu/+bug/130490/comments/20](https://bugs.launchpad.net/ubuntu/+bug/130490/comments/20)

I started checking in "/etc/dbus-1/system.d/hal.conf" and "/usr/share/hal/fdi/policy/10osvendor/20-storage-methods.fdi", and after I saw that are the same with live CD of Jaunty I removed the "ntfs-config".

I did:
sudo apt-get --purge remove ntfs-config
sudo /etc/init.d/hal restart

It works both on Intrepid and Jaunty. On Intrepid I did 2 times the "sudo /etc/init.d/hal restart" to work. I haven't check it on Hardy.

I don't know if it's the same problem that other ppl have, so before this bug is marked as closed I think is better to see from others that the problem is solved too. I don't know if are there other packages that cause this problem.


---

