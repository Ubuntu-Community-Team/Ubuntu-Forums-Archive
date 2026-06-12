---
title: "Where is my mounted drives ?"
date: 2008-08-31
forum: General Help
---

### Post by Dreamerman on 2008-08-31
I've used guides in this forum to mount my physical drives using the following:-

sudo mkdir /home/500G_2
sudo mkdir /home/300G_1
sudo mkdir /home/300G_2
sudo mkdir /home/160G_1

sudo mount /dev/sda1 /home/300G_1
sudo mount /dev/sdb1 /home/300G_2
sudo mount /dev/sdc1 /home/160G_1
sudo mount /dev/sde1 /home/500G_2

My newly mounted drives sits under /home as it should. After reboot, it disappeared. New folders created by mkdir are all there but hard drives are not mounted. Then I sudo nautilus & changed permissions to /home & everything under /home from root to master. Owner & Group from root to master with folder access create & delete files. I repeated the above sudo mount process & reboot. Same result.

I am sure I am missing a step or overlooked something. Can anyone help ?

Thanks

---

### Post by aloshbennett on 2008-08-31
If you mount from commandline, it wouldnt persist and would go off every time you reboot. Add the entries to /etc/fstab if you want the drives to be mounted verytime

---

### Post by Dreamerman on 2008-08-31
> **aloshbennett said:**
> If you mount from commandline, it wouldnt persist and would go off every time you reboot. Add the entries to /etc/fstab if you want the drives to be mounted verytime

Stupid me ! Thanks very much. Just trying to be friendly with Ubuntu.

---

