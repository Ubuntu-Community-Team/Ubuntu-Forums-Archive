---
title: "mount a fakeraid"
date: 2008-01-05
forum: Hardware &amp; Laptops
---

### Post by spotslayer on 2008-01-05
I have built a new server and I have installed a fakeraid array. (system board bios)

david@sGlamp:$ sudo dmraid -r
[sudo] password for david:
/dev/sda: pdc, "pdc_bafgaid-0", stripe, ok, 310546816 sectors, data@ 0
/dev/sdb: pdc, "pdc_bafgaid-0", stripe, ok, 310546816 sectors, data@ 0
/dev/sdc: pdc, "pdc_bafgaid-1", stripe, ok, 310546816 sectors, data@ 0
/dev/sdd: pdc, "pdc_bafgaid-1", stripe, ok, 310546816 sectors, data@ 0

I have not been able to mount it. I have tried using this.
david@sGlamp:/$ sudo mount /dev/mapper/pdc_bafgaid-0 /mnt/var/www
When I do I get this.
mount: /dev/mapper/pdc_bafgaid-0 already mounted or busy
but
david@sGlamp:/$ sudo umount /dev/mapper/pdc_bafgaid-0
umount: /dev/mapper/pdc_bafgaid-0: not mounted

I have tried adding to my fstab like this, but does not mount.
/dev/mapper/pdc_bafgaid-0 /var/www reiserfs defaults 0 1

I have googled a lot of stuff about how to install on a raid. I have installed ubuntu lamp on a separate hard drive that is not part of the array, now I just wan to mount and put my /home and /var/www on it. Can anyone point me in the right direction.

I hope this is not too confusing. I am totally confused.

David :shock:

---

### Post by spotslayer on 2008-01-05
Well guys I think I have found the answer. I had originally set up and formated the array using gparted. I later blew that stuff away and just set up with gparted and did fsck.reiserfs to do the format. I am now able to mount my array and using fstab move directories to it. I am still hackin around with stuff and not sure of what is what, but I guess I am on the right track.

I guess the fakearray and gparted are just no cool together.

David :-k

---

