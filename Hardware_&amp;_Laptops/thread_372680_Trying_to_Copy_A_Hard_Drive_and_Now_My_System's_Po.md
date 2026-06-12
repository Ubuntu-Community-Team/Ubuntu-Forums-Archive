---
title: "Trying to Copy A Hard Drive and Now My System's Pooched!"
date: 2007-02-28
forum: Hardware &amp; Laptops
---

### Post by itazuki on 2007-02-28
Hey there. I currently have a IDE 40GB drive as /, an 80GB IDE as /home. I just acquired a 200GB SATA drive and I would like to use the SATA as /home and then use the 80GB IDE as a Windows drive.

I ran fdisk on the SATA and made a single primary partition and wrote to the partition table. I then ran mke2fs -j /dev/sda1

I then booted to the command line and did:

mount /home
mount /mnt/temphome
cp -varp /home/* /mnt/temphome/

Then I edited fstab and commented out the 80GB IDE and changed the entry for the SATA drive so it would be mounted at /home and rebooted. As the system loaded it was giving errors about how there's no space left and when the GUI loaded it said it could not write to /tmp and hung. I rebooted to the command line and changed fstab back to how it originally was. When I got to the login screen in KDE I entered my login credentials and pressed enter and the screen went black for a moment and then went right back to the login screen. I cleared out /tmp and rebooted. No change.

Any ideas?
_________________

---

### Post by itazuki on 2007-02-28
So I removed /mnt/temphome and noticed that /etc/fstab is empty. No change in my GUI problem. I do not understand why being low on disk space would remove the contents of system files. 

So yeah, I am at a loss. I didn't think copying files between hard drives would destroy my system.

Any ideas? Am I gonna have to toast this system and reinstall?

---

