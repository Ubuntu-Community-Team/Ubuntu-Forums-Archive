---
title: "Apt-get update failed with 111"
date: 2009-10-07
forum: Installation &amp; Upgrades
---

### Post by sombertattoo on 2009-10-07
```
Err http://mirror.cpsc.ucalgary.ca karmic Release.gpg
  Could not connect to skunk.ocunix.on.ca:3142 (192.168.0.2). - connect (111: Connection refused)
Err http://mirror.cpsc.ucalgary.ca karmic/main Translation-en_US
  Could not connect to skunk.ocunix.on.ca:3142 (192.168.0.2). - connect (111: Connection refused)
Err http://mirror.cpsc.ucalgary.ca karmic/restricted Translation-en_US
  Could not connect to skunk.ocunix.on.ca:3142 (192.168.0.2). - connect (111: Connection refused)
Err http://mirror.cpsc.ucalgary.ca karmic/universe Translation-en_US
  Could not connect to skunk.ocunix.on.ca:3142 (192.168.0.2). - connect (111: Connection refused)
Err http://mirror.cpsc.ucalgary.ca karmic/multiverse Translation-en_US
  Could not connect to skunk.ocunix.on.ca:3142 (192.168.0.2). - connect (111: Connection refused)
Err http://mirror.cpsc.ucalgary.ca karmic-updates Release.gpg
  Could not connect to skunk.ocunix.on.ca:3142 (192.168.0.2). - connect (111: Connection refused)
Err http://mirror.cpsc.ucalgary.ca karmic-updates/main Translation-en_US
  Could not connect to skunk.ocunix.on.ca:3142 (192.168.0.2). - connect (111: Connection refused)
Err http://mirror.cpsc.ucalgary.ca karmic-updates/restricted Translation-en_US
  Could not connect to skunk.ocunix.on.ca:3142 (192.168.0.2). - connect (111: Connection refused)
Err http://mirror.cpsc.ucalgary.ca karmic-updates/universe Translation-en_US
  Could not connect to skunk.ocunix.on.ca:3142 (192.168.0.2). - connect (111: Connection refused)
Err http://mirror.cpsc.ucalgary.ca karmic-updates/multiverse Translation-en_US
  Could not connect to skunk.ocunix.on.ca:3142 (192.168.0.2). - connect (111: Connection refused)
Err http://mirror.cpsc.ucalgary.ca karmic-security Release.gpg
  Could not connect to skunk.ocunix.on.ca:3142 (192.168.0.2). - connect (111: Connection refused)
Err http://mirror.cpsc.ucalgary.ca karmic-security/main Translation-en_US
  Could not connect to skunk.ocunix.on.ca:3142 (192.168.0.2). - connect (111: Connection refused)
Err http://mirror.cpsc.ucalgary.ca karmic-security/restricted Translation-en_US
  Could not connect to skunk.ocunix.on.ca:3142 (192.168.0.2). - connect (111: Connection refused)
Err http://mirror.cpsc.ucalgary.ca karmic-security/universe Translation-en_US
  Could not connect to skunk.ocunix.on.ca:3142 (192.168.0.2). - connect (111: Connection refused)
Err http://mirror.cpsc.ucalgary.ca karmic-security/multiverse Translation-en_US
  Could not connect to skunk.ocunix.on.ca:3142 (192.168.0.2). - connect (111: Connection refused)
Reading package lists... Done
W: Failed to fetch http://mirror.cpsc.ucalgary.ca/mirror/ubuntu.com/packages/dists/karmic/Release.gpg  Could not connect to skunk.ocunix.on.ca:3142 (192.168.0.2). - connect (111: Connection refused)

W: Failed to fetch http://mirror.cpsc.ucalgary.ca/mirror/ubuntu.com/packages/dists/karmic/main/i18n/Translation-en_US.bz2  Could not connect to skunk.ocunix.on.ca:3142 (192.168.0.2). - connect (111: Connection refused)

W: Failed to fetch http://mirror.cpsc.ucalgary.ca/mirror/ubuntu.com/packages/dists/karmic/restricted/i18n/Translation-en_US.bz2  Could not connect to skunk.ocunix.on.ca:3142 (192.168.0.2). - connect (111: Connection refused)

W: Failed to fetch http://mirror.cpsc.ucalgary.ca/mirror/ubuntu.com/packages/dists/karmic/universe/i18n/Translation-en_US.bz2  Could not connect to skunk.ocunix.on.ca:3142 (192.168.0.2). - connect (111: Connection refused)

W: Failed to fetch http://mirror.cpsc.ucalgary.ca/mirror/ubuntu.com/packages/dists/karmic/multiverse/i18n/Translation-en_US.bz2  Could not connect to skunk.ocunix.on.ca:3142 (192.168.0.2). - connect (111: Connection refused)

W: Failed to fetch http://mirror.cpsc.ucalgary.ca/mirror/ubuntu.com/packages/dists/karmic-updates/Release.gpg  Could not connect to skunk.ocunix.on.ca:3142 (192.168.0.2). - connect (111: Connection refused)

W: Failed to fetch http://mirror.cpsc.ucalgary.ca/mirror/ubuntu.com/packages/dists/karmic-updates/main/i18n/Translation-en_US.bz2  Could not connect to skunk.ocunix.on.ca:3142 (192.168.0.2). - connect (111: Connection refused)

W: Failed to fetch http://mirror.cpsc.ucalgary.ca/mirror/ubuntu.com/packages/dists/karmic-updates/restricted/i18n/Translation-en_US.bz2  Could not connect to skunk.ocunix.on.ca:3142 (192.168.0.2). - connect (111: Connection refused)

W: Failed to fetch http://mirror.cpsc.ucalgary.ca/mirror/ubuntu.com/packages/dists/karmic-updates/universe/i18n/Translation-en_US.bz2  Could not connect to skunk.ocunix.on.ca:3142 (192.168.0.2). - connect (111: Connection refused)

W: Failed to fetch http://mirror.cpsc.ucalgary.ca/mirror/ubuntu.com/packages/dists/karmic-updates/multiverse/i18n/Translation-en_US.bz2  Could not connect to skunk.ocunix.on.ca:3142 (192.168.0.2). - connect (111: Connection refused)

W: Failed to fetch http://mirror.cpsc.ucalgary.ca/mirror/ubuntu.com/packages/dists/karmic-security/Release.gpg  Could not connect to skunk.ocunix.on.ca:3142 (192.168.0.2). - connect (111: Connection refused)

W: Failed to fetch http://mirror.cpsc.ucalgary.ca/mirror/ubuntu.com/packages/dists/karmic-security/main/i18n/Translation-en_US.bz2  Could not connect to skunk.ocunix.on.ca:3142 (192.168.0.2). - connect (111: Connection refused)

W: Failed to fetch http://mirror.cpsc.ucalgary.ca/mirror/ubuntu.com/packages/dists/karmic-security/restricted/i18n/Translation-en_US.bz2  Could not connect to skunk.ocunix.on.ca:3142 (192.168.0.2). - connect (111: Connection refused)

W: Failed to fetch http://mirror.cpsc.ucalgary.ca/mirror/ubuntu.com/packages/dists/karmic-security/universe/i18n/Translation-en_US.bz2  Could not connect to skunk.ocunix.on.ca:3142 (192.168.0.2). - connect (111: Connection refused)

W: Failed to fetch http://mirror.cpsc.ucalgary.ca/mirror/ubuntu.com/packages/dists/karmic-security/multiverse/i18n/Translation-en_US.bz2  Could not connect to skunk.ocunix.on.ca:3142 (192.168.0.2). - connect (111: Connection refused)

W: Some index files failed to download, they have been ignored, or old ones used instead.

```

No matter which mirror I try, I get nothing. I had these problems pretty close to when I upgraded to 9.10. I could reload the index a few times but it was rare. Usually I just had this error. Now to fix a nautilus bug, I need updates! Any help? I can happily browse the internet.

Thanks!
(Karmic 64 with updates as new as yesterday)

---

### Post by zvacet on 2009-10-08
I think servers are loaded because of new release.Anyway only packages you can not download are language packages.You should be able to download other updates.

---

### Post by diesch on 2009-10-08
Use "Software Sources" to find a server:

At "Download from" select  "Other" and click the "Select Best Server" button.

---

### Post by sombertattoo on 2009-10-08
Thanks for the reply, I've tried numerous servers and different "Best Servers" with no change. Hate being stuck in beta!

Any way to download newest updates for a base karmic install without using apt-get? Don't think so but might as well ask

---

### Post by sombertattoo on 2009-10-09
*bump*

Thanks in advance

---

### Post by sombertattoo on 2009-10-09
Anyways, I managed to fix my nautilus bug manually so I don't need to get any updates. Finally looked through and figured out it was all translations as mentioned. Just surprised to not see the bug fix I was waiting for or any other updates for that matter in the pipes.

Thanks!
Greg

Edit: Oh...feature freeze..I feel dumb

---

### Post by diesch on 2009-10-09
de.archive.ubuntu.com works for me

---

### Post by sombertattoo on 2009-10-09
Same error, just different source. A simple browser check to say for example -> [http://de.archive.ubuntu.com/ubuntu/dists/karmic-proposed/universe/i18n/Translation-en_US.bz2](http://de.archive.ubuntu.com/ubuntu/dists/karmic-proposed/universe/i18n/Translation-en_US.bz2) shows it's not there. So that's fine

But, if I navigate to [http://de.archive.ubuntu.com/ubuntu/dists/karmic/Release.gpg](http://de.archive.ubuntu.com/ubuntu/dists/karmic/Release.gpg), that exists. That according to the error is not there. But it's definitely there.

My concern is somehow I'm running through a proxy. I checked network configuration and I'm indeed Direct-connect (as I should be) I'm a simple hop to the switch, to the router, to wireless dish to the internet yonder. At the router level I'm given a local static IP which is correct according to ifconfig

---

