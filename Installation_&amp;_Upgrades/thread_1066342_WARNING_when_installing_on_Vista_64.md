---
title: "WARNING when installing on Vista 64"
date: 2009-02-10
forum: Installation &amp; Upgrades
---

### Post by Raze62 on 2009-02-10
I used the Ubuntu iso to install on a USB External drive and my Vista boot record got messed up. Vista does not load.

If you think that installing on a USB External drive is safe?  No way! Your master MBR WILL BE OVERWRITTEN.

Now I am lost with a system that does not boot and I do not have the Vista install DVD with me either.

Users beware that installing Ubuntu will affect your boot disk.

:(

---

### Post by theozzlives on 2009-02-10
It's safe to make a persistent USB, you just burn the ISO to CD, boot up off the live CD, and go to Applications > Accessories > Terminal. Type:
```
wget pendrivelinux.com/downloads/u810/u810.sh
```
then:
```
chmod +x u810.sh && sh u810.sh
```
just follow the prompts, it wont do anything to your HD, BTW you have to have your flash drive in before you start this.

---

