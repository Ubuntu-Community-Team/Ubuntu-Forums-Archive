---
title: "raid 1 and 9.04?"
date: 2009-04-21
forum: Installation &amp; Upgrades
---

### Post by murphy on 2009-04-21
Hi there,

has anybody tried to install 9.04 on a raid 1 system (MSI P45 with raid controller)? I would like to do so and some hints how to do so would be great. Using the livecd the raid is not detected. Do i have to use the fakeraid?

Best regards,

Nils

---

### Post by ronparent on 2009-04-21
It looks like you would have to use the 'alternate cd'. From what you describe the standard desktop 9.04 is behaving like 8.10 in that respect. If that is the case you would have to use the procedure for installing to a fake raid. Are you starting from scratch or do you have a prior ubuntu version on the raid1 array?

---

### Post by murphy on 2009-04-21
Thank you for your reply. I'm starting from scratch because the complete hardware is just three days old. After downloading i'll test the alternate cd.

---

### Post by ronparent on 2009-04-21
In that case it is your choice whether to use 'fake raid' or 'software raid'. It makes no appreciable difference unless you plan to dual boot with windows. In that case you have to make sure you activate the raid option in bios for the ports you are plugging your disks into, as well as configuring your raid1 in the separate raid bios. That would require you to use the fakeraid proceedure to install ubuntu. If you never intend to install windows as dual boot, then it is your choice on the raid setup. I would advise NOT setting up raid in bios if you intend to install with the software raid.

---

### Post by murphy on 2009-04-23
Hi,

i used the alternate cd to install the system und does what it should do! Thanks for your comments!

Best regards,

Nils

---

