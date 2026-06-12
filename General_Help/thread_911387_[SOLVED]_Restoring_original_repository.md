---
title: "[SOLVED] Restoring original repository"
date: 2008-09-05
forum: General Help
---

### Post by LonelyTraveler on 2008-09-05
How do I go about restoring my repository to the original one? Like it is upon installing.

Thanks.

---

### Post by ~LoKe on 2008-09-05
Which version of ubuntu are you using?

---

### Post by jerome1232 on 2008-09-05
You should be able to grab a live cd (of the same version) boot off of it and copy it's sources.list over. So say your / is /dev/sda1 this is what you would do to copy it off of the live cd, and store a backup copy so that in the future you always have an original lying around.
```
sudo -i
mkdir /mnt/root
mount /dev/sda1 /mnt/root
cp /etc/apt/sources.list /mnt/root/etc/apt/sources.list
cp /mnt/root/etc/apt/sources.list /mnt/root/etc/apt/sources.list.backup
exit
```

---

### Post by LonelyTraveler on 2008-09-06
Thanks to both of you. I'm using Hardy by the way. I'm sure that will work Jerome. I'll do that when I get home today. I'm at work at the moment, but luckily running Ubuntu here too! Not that my boss knows about it. Lol!

---

### Post by ~LoKe on 2008-09-06
Eh.
> deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main restricted

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates main restricted

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates universe

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates multiverse

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-security main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-security universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-security multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-security multiverse

---

### Post by LonelyTraveler on 2008-09-07
> **~LoKe said:**
> Eh.

Thanks Loke

---

### Post by LonelyTraveler on 2008-09-07
> **~LoKe said:**
> Eh.

After running sudo apt-get update I get this:
```
W: GPG error: http://archive.canonical.com hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: http://archive.ubuntu.com hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: http://us.archive.ubuntu.com hardy-backports Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: http://archive.ubuntu.com hardy-updates Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: http://archive.ubuntu.com hardy-security Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: You may want to run apt-get update to correct these problems
```

This is why I wanted to restore my repository. Is there something wrong on my end or on the servers?

Thanks

---

### Post by LonelyTraveler on 2008-09-07
I guess the actual question here was answered so I'm going to start a new thread.

Thanks.

---

