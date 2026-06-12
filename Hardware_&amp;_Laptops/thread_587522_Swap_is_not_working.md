---
title: "Swap is not working"
date: 2007-10-22
forum: Hardware &amp; Laptops
---

### Post by d11 on 2007-10-22
I have mi partition swap in sda5 but is not working. maybe is not mount. anyone can help me????

---

### Post by ramjet_1953 on 2007-10-22
How much RAM do you have?

Quite often, if you have a decent amount of RAM the swapfile is never used, as the system uses your free memory as cache.

Regards,
Roger :cool:

---

### Post by tommcd on 2007-10-23
Open a terminal and type "free -m" this will list RAM and swap in megabytes. If swap is not listed there check your fstab "cat /etc/fstab". You should have a swap partition (dev/sda5) listed there. If it is listed in fstab try "sudo swapon /dev/sda5". Then do "free -m" again to see if it's there. If you still don't see it make /dev/sda5 a swap partition like this:
"sudo mkswap /dev/sda5"
"sudo swapon /dev/sda5"
Make sure that sda5 is indeed the partition you intended for swap.
If it is not listed in fstab, you can enter it like this:

/dev/sda5   none  swap  sw 0 0

---

### Post by noynac on 2007-10-23
I had a similar problem and resolved it by correcting the UUID of the swap partition in the fstab file. If it works, the method suggested by tommcd is easier.

Although it deals with a slightly different topic, there is some useful information in:

[https://launchpad.net/ubuntu/+bug/66637](https://launchpad.net/ubuntu/+bug/66637)

---

### Post by tommcd on 2007-10-23
> **noynac said:**
> I had a similar problem and resolved it by correcting the UUID of the swap partition in the fstab file. If it works, the method suggested by tommcd is easier.

Although it deals with a slightly different topic, there is some useful information in:

[https://launchpad.net/ubuntu/+bug/66637](https://launchpad.net/ubuntu/+bug/66637)

Yes, it could be those darned UUIDs also. If my last suggestions still don't work the back up fstab first:
"sudo cp /etc/fstab /etc/fstab.bak"
Then edit fstab and remove the UUID part of the swap line so it looks something like this, all on 1 line:
/dev/sda5 none swap sw 0 0

Perhaps you could post your fstab here.

---

### Post by d11 on 2007-10-23
thanks noynac. i solved the  problem changing the  UUDI in fstab.
now is working.

---

