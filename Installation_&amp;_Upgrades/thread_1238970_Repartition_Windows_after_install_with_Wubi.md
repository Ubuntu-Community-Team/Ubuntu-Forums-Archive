---
title: "Repartition Windows after install with Wubi"
date: 2009-08-13
forum: Installation &amp; Upgrades
---

### Post by wackzingo on 2009-08-13
I just installed the latest version of Ubuntu on a Dell Latitude from within Windows XP Pro using Wubi on a thumb drive. I used this method because I don't have a working CD/DVD drive and can't boot from USB. 

My filesystem now looks like this:

```
/host/ubuntu/disks/root.disk        /        ext3         4.6GiB
/host/ubuntu/disks/boot             /boot    none        37.3GiB 
/dev/sda1                           /host    fuseblk     37.3GiB
```

I can't use a live or other disk where I must boot from that media since my CD/DVD doesn't work and I can't boot from USB. From this point how can I erase Windows and expand the current ubuntu partition. In other words, I want the entire drive to to be used by ubuntu. Any help would be greatly appreciated.

---

### Post by raymondh on 2009-08-13
> **wackzingo said:**
> I just installed the latest version of Ubuntu on a Dell Latitude from within Windows XP Pro using Wubi on a thumb drive. I used this method because I don't have a working CD/DVD drive and can't boot from USB. 

My filesystem now looks like this:

```
/host/ubuntu/disks/root.disk        /        ext3         4.6GiB
/host/ubuntu/disks/boot             /boot    none        37.3GiB 
/dev/sda1                           /host    fuseblk     37.3GiB
```

I can't use a live or other disk where I must boot from that media since my CD/DVD doesn't work and I can't boot from USB. From this point how can I erase Windows and expand the current ubuntu partition. In other words, I want the entire drive to to be used by ubuntu. Any help would be greatly appreciated.

It being wubi, when you erase windows, you erase ubuntu as well.  

From the [wubi guide]("https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20migrate%20to%20a%20real%20partition,%20and/or%20get%20rid%20of%20Windows%20entirely?").

Back-up, pls. :)  I have not done migrating and cannot guarantee its' success.

Raymond

---

