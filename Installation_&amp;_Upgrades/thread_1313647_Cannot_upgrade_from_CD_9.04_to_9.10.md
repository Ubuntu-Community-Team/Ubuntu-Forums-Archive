---
title: "Cannot upgrade from CD 9.04 to 9.10"
date: 2009-11-03
forum: Installation &amp; Upgrades
---

### Post by uk2 on 2009-11-03
Hello,

I have tried to upgrade from the CD and by mounting the .ISO. However, all have been unsuccessfull.

I have downloaded the 32 bit version of 9.10. 

I have tried to follow the instructions from this website
[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

First I tried to mount the ubuntu-9.10-desktop-i386.iso
using the following:

```
    sudo mount -o loop ~/Desktop/ubuntu-9.10-desktop-i386.iso /media/cdrom0
```

Which mounted it. But I never got the dialog box that says 'run upgrade'

I then did 'Alt F2' and typed the following:

 ```
   gksu "sh /cdrom/cdromupgrade"
```

Still nothing happened.

I can browse the files from the mounted *.iso and on the burnt CD. However, the dialog doesn't appear.

I can boot from the CD if I restart my computer. However, I just want to do a upgrade and not clean install.

I can't do an upgrade from the update-manager as my Internet is too slow and unreliable.

Many thanks for any advice

---

### Post by MikeMiracle on 2009-11-04
Desktop iso is meant for fresh install only . You can't upgrade from it. Instead use alternate iso.
Rest of the process you followed is correct.One important tip is to say No to the prompt which asks for downloading newer packages on pressing the upgrade button.This was too slow for me. You can do Update once your dist gets updated to Karmic.So better go for offline upgrade.

Link:                [ http://releases.ubuntu.com/9.10/ubuntu-9.10-alternate-i386.iso]("http://releases.ubuntu.com/9.10/ubuntu-9.10-alternate-i386.iso")
Torrent Link:    [http://releases.ubuntu.com/9.10/ubuntu-9.10-alternate-i386.iso.torrent](http://releases.ubuntu.com/9.10/ubuntu-9.10-alternate-i386.iso.torrent)
Official Instructions:    [http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)  (upgrading using alternate cd/dvd section)

All the best ):P

---

