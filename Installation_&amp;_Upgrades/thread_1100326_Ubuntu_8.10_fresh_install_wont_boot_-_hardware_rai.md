---
title: "Ubuntu 8.10 fresh install wont boot - hardware raid"
date: 2009-03-19
forum: Installation &amp; Upgrades
---

### Post by ale1981 on 2009-03-19
I have a HP Compaq DL380 G4 with a Smart Array 6i hardware controller. Attached to the controller are 2 x 146GB 15k SCSI drives setup with RAID1+0. 

When attempting to install Ubuntu 8.10 server I get the 

Buffer I/O error on device sr0, logical block 1147534
end_request: I/O error dev sr0, sector9180280

errors but install continues and completes.

Once this install is complete I restart the server but ubuntu fails to boot, the server just stays on "Attempting to boot from hard drive (C:)"

When attempting to boot from the LiveCD the boot just gets stuck on the ubuntu splash screen with the orange bar.

Any help much appreciated!?

---

### Post by ale1981 on 2009-03-19
UPDATE:

After leaving the LiveCD to try and boot for around 15-20 minutes it seems to finally boot to the desktop.

When I go into the Partition Manager it says no devices found!

---

### Post by sahabcse on 2009-03-19
Hi

Try to clear the hardisk using server set-up and installation cd and then try again. Have you installed the same media(ubuntu cd) any other place?

---

### Post by ale1981 on 2009-03-19
This is the second time i have tried to install using 2 different CDs both burnt at different speeds.

The installation detects the RAID but doesnt seem to want to boot from it once the install is complete.

---

### Post by sahabcse on 2009-03-19
Hi

Verify the below url seems to be same issue

[http://ubuntuforums.org/showthread.php?t=1090694&page=2](http://ubuntuforums.org/showthread.php?t=1090694&page=2)

---

### Post by ale1981 on 2009-03-19
No, I am getting those errors before install, but the install still continues and completes fine. 

The problem is after installation has completed, when I attempt to reboot nothing happens, ubuntu just doesnt want to boot of the hard drives.

---

### Post by sahabcse on 2009-03-19
Hi

Try ubuntu 8.04 LTS server addition

---

### Post by ale1981 on 2009-03-19
I have fixed the problem!

After much probing I figured it had to be the grub had not install properly.

After looking at this topic;
[http://ubuntuforums.org/showthread.php?t=1025985](http://ubuntuforums.org/showthread.php?t=1025985)

I decided to launch the rescue mode and re-install the grub loader to the correct partition.

All now works great!

---

### Post by sahabcse on 2009-03-19
Hi
I have already added my blog about grub fix.
Anyway Happy to hear you issue solved.

---

