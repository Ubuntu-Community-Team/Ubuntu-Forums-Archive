---
title: "Bad upgrade to 9.04"
date: 2009-04-25
forum: Installation &amp; Upgrades
---

### Post by gamewolf on 2009-04-25
I had Ubuntu 8.10 and I decided to upgrade to 9.04. The installation was taking a longtime and I left it to do its thing overnight.

However, someone else in the house thought I left it on by accident and did a hard reset and turned it off while it was upgrading.

Now when I boot I can login, but its just a black screen.

Is there a way to redo the upgrade or continue where I left off? I have Ubuntu Server installed on the same hard drive so I am able to chroot into it if I need to.

Thanks.

---

### Post by LinuxGuy1234 on 2009-04-25
> **gamewolf said:**
> I had Ubuntu 8.10 and I decided to upgrade to 9.04. The installation was taking a longtime and I left it to do its thing overnight.

However, someone else in the house thought I left it on by accident and did a hard reset and turned it off while it was upgrading.

Now when I boot I can login, but its just a black screen.

Is there a way to redo the upgrade or continue where I left off? I have Ubuntu Server installed on the same hard drive so I am able to chroot into it if I need to.

Thanks.

Chroot into the broken Ubuntu and do:
```
dpkg --reconfigure -a
apt-get -f dist-upgrade
```

---

### Post by gamewolf on 2009-04-25
> **LinuxGuy1234 said:**
> Chroot into the broken Ubuntu and do:
```
dpkg --reconfigure -a
apt-get -f dist-upgrade
```

I am upgrading the server right now. After it is done I will try those commands.

Thanks.

---

### Post by gamewolf on 2009-04-25
Ok dpkg --reconfigure -a doesn't work. dpkg-reconfigure -a does so I used that.

Then I type apt-get -f dist-upgrade and all it said was that two packages have been held back. It still doesn't work

---

### Post by gamewolf on 2009-04-25
Nevermind! It works now. Doing dpkg-reconfigure -a fixed it.

Thanks!

---

### Post by ShinHadoken on 2009-04-25
Well, it seems I've gotten in on this a little late in the game, so the only advice I have is to boot into the recovery kernel (from the GRUB boot menu) after everything's finished and do a filesystem check, just to make sure everything's peachy.

---

