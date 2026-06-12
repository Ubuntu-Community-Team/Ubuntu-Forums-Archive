---
title: "Help: can't mount my linux root partition"
date: 2009-10-15
forum: Hardware
---

### Post by earthmumma on 2009-10-15
Hi,

I get the following error:

> mount: mounting /dev/sdc1 on /media/rt failed: Input/output error

Other drives can mount fine to the '/media/rt' folder but not that one

wassappinin?

cheers

Ms Mumma :confused:

---

### Post by dabl on 2009-10-15
I suspect your mount command is not quite right, for the /dev/sdc1 filesystem.

Can you do two things, please:

1. From your Live CD session, open the Konsole and enter ```
sudo fdisk -lu
``` and post the output here.

2. Also post the mount command that you are attempting to use to mount that partition.

---

### Post by earthmumma on 2009-10-15
it's working now!

before when i fdisk i couldn't see sdc1 - the linux root

now I can and I can mount it.

it's still unstable - I've entered:

sudo fsck /dev/sdc1 -f -v

which I hope makes it stable

---

### Post by fdrake on 2009-10-15
you should check your fstab file

---

