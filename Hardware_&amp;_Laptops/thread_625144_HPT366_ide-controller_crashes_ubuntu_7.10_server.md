---
title: "HPT366 ide-controller crashes ubuntu 7.10 server"
date: 2007-11-27
forum: Hardware &amp; Laptops
---

### Post by svennils on 2007-11-27
Hi folks, (WARNING- long-winded explanation coming up....)

I have a server running ubuntu 7.10 server, serving as a multipurpose box (nat router, www/samba/ssh/storage server).
It has 3 nic's, (1 double intel 100mbit pci card, 1 10mbit pci card,)
and a HPT366 dual channel ide controller.
Everything works fine, just upgraded the box from slack 10 to ubuntu to get mysql&php without too much hassle.
Boot disk is connected to onboard ide port 1
Onboard ide 2 port 2 is not used atm.
HPT366 has 2x 200Gb drives on port 1, these have been working fine on slack and ubuntu for ages. these are hde&hdf, both ext2.

An now the fun part. I recently recieved a 250gb ide disk with 190gb of data. Connected it to the second ide port on the hpt(hdg), and copied the data on to hdf (HPT port 1). No problem. Returned the disk, and bought a 500Gb drive today, to get more space. Hooked it to the same port, hdg, and started copying the data from hdf(port 1) to hdg(port 2). After some 30 seconds of copying, the machine freezes totally. Power cycled, and tried again. Same result. Connected the drive to onboad ide port 2, and it works. Copying as i am writing this, and it serves my internet connection as well. The strange part: it was partitioned and mkfs'ed on the hpt port 2...... Seems the hpt is using irq11 for both ports on the card, and always has. The dual ethernet card has 2 irq's. Syslog does not even mention the crash, it never gets to write anything aboyt it there. Just some status info on the HPT while booting. I'm planning to add more drives to the box soon, and would appreciate any idea on the cause of this. Never tried more than 1 channel under slackware, so i don't know if it is a ubuntu-specific problem.
Syslog available on request.

Hints, anyone?

---

