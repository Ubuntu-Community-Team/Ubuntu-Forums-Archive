---
title: "RAID 5 sometimes not detected on boot"
date: 2010-06-20
forum: Hardware
---

### Post by anty on 2010-06-20
Hi,

I have two SATA-raids:
[LIST=1]
[*]raid 0 which is my / partition and working fine
[*]raid 5 which is my /home partition and fails very often when I boot
[/LIST]
I have to boot up to 10 times until I can log in. I always get the message "/home not ready yet".

When I'm able to boot successfully, I can call dmraid:

anty@anty:~$ sudo dmraid -ay
RAID set "isw_ceghigfjad_zero" already active
RAID set "isw_diebccfhgg_big" already active
RAID set "isw_ceghigfjad_zero1" already active
RAID set "isw_ceghigfjad_zero2" already active
RAID set "isw_ceghigfjad_zero5" already active
RAID set "isw_ceghigfjad_zero6" already active
RAID set "isw_diebccfhgg_big1" already active

big1 is the /home partition, zero is /.

When booting up I get different error messages:
[LIST]
[*]only 2 out of 3 disks are ready, algorithm 2 is used
[*]md0 not found (or something similar, I hope this is accurate enough)
[*]device-mapper: table: 252:6: raid45: RAID device lookup failure
[/LIST]

I've pressed "m" for manual resolution and looked at all log files in /var/log/ but couldn't find anything meaningful.
Can someone point me to the right logfile?

Also, the raid 5 seems to corrupt random files. I think that is because I have to reboot so often while the hdisk-led is on...

Any ideas?

Edit: I've now destroyed and rebuild the raid array and I still get the same error messages...

Thank you,
anty

**Update:**
dmraid -ay displays "device not activated" when I get the boot-error.

But I now know how to boot when I get the "device not ready" error:

press "m" for manual fixing
mdadm --stop /dev/md0
dmraid -ay
Ctrl+D

and now I'm booting. What's happening here and more importantly: How can I fix this?

---

### Post by ronparent on 2010-06-22
Since your results on booting are inconsistent it could be a timing issue. You
could try editing the grub boot line by adding the boot parameter:  rootdelay=90

If it works you can make the change permanent in /etc/default/grub.

---

### Post by anty on 2010-07-07
How do I prevent Ubuntu from loading /dev/md0? I already commented out everything in /etc/mdadm/mdadm.conf but it still loads /dev/md0.

And I still have data loss (or better: I can't access certain files like they are read-protected. I can replace them, though.)

Could it be, that after /dev/md0 is loaded, the algorithm tries to fix the inconsistent array and corrupts my data this way?

---

### Post by ronparent on 2010-07-07
Try uninstalling mdadm? /dev/md0 shouldn't load with mdadm gone.

---

### Post by anty on 2010-07-07
# apt-get remove mdadm
seems to work. I was afraid to just do it, but here I am. It's still booting and this time I didn't have errors. I will post again in case the error reappears.

Thank you ronparent ;)

---

