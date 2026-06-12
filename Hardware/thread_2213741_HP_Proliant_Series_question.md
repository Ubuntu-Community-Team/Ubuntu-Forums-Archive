---
title: "HP Proliant Series question"
date: 2014-03-28
forum: Hardware
---

### Post by citaliano on 2014-03-28
Hello,

I'm speccing out a new server and I noticed that all of the HP 1RU servers use the HP Embedded 4-Port B120i SATA Controller which according to this site [http://h17007.www1.hp.com/us/en/enterprise/servers/supportmatrix/exceptions/ubuntu_exceptions.aspx#.UzR8PvldXTo](http://h17007.www1.hp.com/us/en/enterprise/servers/supportmatrix/exceptions/ubuntu_exceptions.aspx#.UzR8PvldXTo) has are no drivers for Ubuntu. I am looking to use the RAID 1 settings with two drives and I want to make sure that it will work with Ubuntu. Does anyone use these systems and know if there's a 3rd party driver somewhere that will work? Or if HPs site is just wrong and it will work?

---

### Post by lukeiamyourfather on 2014-03-28
From what I understand, it'll work as a SATA controller but not as HP's proprietary fake RAID. So you could just treat it as a SATA controller and use mdadm for RAID 1 (or something else like Btrfs, ZFS, etc.).

---

### Post by citaliano on 2014-03-28
Thanks for the reply. While I'm not new to server software administration, I AM new to server hardware administration. I don't have much experience with these types of things...

So I've read that I can set it to be a SATA controller from the BIOS, I am just not familiar with what the process would be after that. So, I install Ubuntu and then do an apt-get install for mdadm and then just run this? :

```

mdadm --create --verbose /dev/md0 --level=1 /dev/sda1 /dev/sdb2

```

It seems too simple for that to be the way to do it haha. I appreciate your help with this, I'd like to know exactly what is involved with this before I make any purchases so I don't end up with something I can't use.

---

### Post by lukeiamyourfather on 2014-03-31
I have never needed to use mdadm in that kind of scenario but a little searching revealed this.

[https://help.ubuntu.com/lts/serverguide/advanced-installation.html](https://help.ubuntu.com/lts/serverguide/advanced-installation.html)

Looks like it'll cover what you want to do (bootable mirror).

---

### Post by lukeiamyourfather on 2014-04-02
I tried it in a virtual machine for fun, it's very straight forward. Just like the instructions say in the Server Guide. After doing it once it's super easy to do again if you've ever setup RAID on anything else before (a lot easier than most controller firmware interfaces!).

---

