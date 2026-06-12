---
title: "USB Hotplug Problem"
date: 2005-06-16
forum: Hardware &amp; Laptops
---

### Post by Marmal on 2005-06-16
Hi,

i have a little problem with my USB Stick wich was normally automounted.
I dont know why but its not mounted automaticly anymore.

# sudo mount /dev/sda1 /mnt/usb

works, but i can only access as root.
Please help me to fix it mounts automaticly, because it was so good as i put it in and can access asap.

Thx, marc.

---

### Post by WakkiTabakki on 2005-06-16
Try:
# sudo mount -o users,umask=000  /dev/sda1 /mnt/usb

-o = options
users = allow users to mount and unmount the filesystem
umask = tells which user rights to unmask, 000 = unmask nothing, i.e keep rwx for owner, group and world.


BTW, whats in your /etc/fstab (the file that contains information on how file systems are to be mounted)

Good luck
N

---

### Post by Marmal on 2005-06-18
Thanks a lot.

i dont know what was my fault but after i had my PC turned off (complete power down not reset as before) it all worked perfectly.

Thx anyway.

Best regards, Marc

---

