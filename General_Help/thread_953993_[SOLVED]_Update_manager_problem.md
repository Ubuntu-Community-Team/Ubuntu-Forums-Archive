---
title: "[SOLVED] Update manager problem"
date: 2008-10-20
forum: General Help
---

### Post by bexxie30 on 2008-10-20
I keep getting the orange warning triangle, which tells me there may be a problem with update manager. Every time I open update manager and click on check, I get this message:

GPG error: [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263Failed to fetch cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080701)]/dists/hardy/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080701)]/dists/hardy/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.46 80]
Some index files failed to download, they have been ignored, or old ones used instead.


Then the update manager tells me my system was updated 15 days ago, and I cant do anything with it. Help!

---

### Post by mikewhatever on 2008-10-20
You seem to have Edgy Eft's and Hardy Heron's repositories mixed up. How did that happen? Did you know Edgy had reached 'end of support' in April 2008? Which version do you have installed?

Edit: double post [http://ubuntuforums.org/showthread.php?t=953986](http://ubuntuforums.org/showthread.php?t=953986)

---

### Post by bexxie30 on 2008-10-21
I have no idea how it happened, this is my first time using Ubuntu or even a Linux OS come to that. I dont know which version I have, how do I find that out? Sorry if I sound stupid, but I am a Windows baby, and just decided to become an adult....

---

### Post by plucky on 2008-10-21
> **bexxie30 said:**
> I have no idea how it happened, this is my first time using Ubuntu or even a Linux OS come to that. I dont know which version I have, how do I find that out? Sorry if I sound stupid, but I am a Windows baby, and just decided to become an adult....

Open a terminal from **Applications > Accessories > Terminal** and post the output of this command ```
cat /etc/apt/sources.list
```.
This will let us know which repositories you have enabled.

Or

To use a GUI go to **System > Administration > Software Sources**

and (see screenshots) make sure only the right boxes are ticked and the CD-rom is un-ticked and The Wine repository in third party Sources is un-ticked.

Then reload to update the software lists.If this doesn't work,then post the output of the first command.

Good Luck

---

### Post by bexxie30 on 2008-10-22
Thankyou! I followed your screenshots, and it is now working perfectly. Thankyou so much for your help.

---

