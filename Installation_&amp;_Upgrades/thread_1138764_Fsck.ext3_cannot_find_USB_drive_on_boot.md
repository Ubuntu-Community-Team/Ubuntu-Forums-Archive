---
title: "Fsck.ext3 cannot find USB drive on boot"
date: 2009-04-26
forum: Installation &amp; Upgrades
---

### Post by G4HZA on 2009-04-26
I am having difficulty with a usb drive which in the past has mounted error free on boot.

In order to get the drive recognised on boot I have added 'usb_storage' to /etc/modules

I then added the following information into /etc/fstab "UUID=23bc03de-1a4f-4c91-bd45-37dc48a39d56 /mnt/documents  ext3    relatime".  Once the system is fully booted this works correctly and I can access /mnt/documents.

However I get an error from fsck on boot as follows.  "fsck.ext3: Unable to resolve 'UUID etc'".  /var/log/fsck/checkfs contains the following:-

 Log of fsck -C3 -R -A -a
Sun Apr 26 19:30:42 2009

fsck 1.41.4 (27-Jan-2009)
/dev/sda6: clean, 7431/17489920 files, 6524460/69953026 blocks (check in 2 mounts)
fsck.ext3: Unable to resolve 'UUID=23bc03de-1a4f-4c91-bd45-37dc48a39d56'
fsck died with exit status 8

Sun Apr 26 19:30:42 2009
----------------

I'm at a bit of a loss as where to go from here.  Does anyone have any suggestions?

Roger

---

