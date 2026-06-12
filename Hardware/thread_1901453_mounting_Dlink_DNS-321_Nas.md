---
title: "mounting Dlink DNS-321 Nas"
date: 2011-12-28
forum: Hardware
---

### Post by jpaulb on 2011-12-28
Can someone help with a Dlink DNS-321 NAS. I am at a loss as how to mount this with in fstab.
I am able to connect manually through samba. I want to have it mounted when one of the laptops boots.

If I try mount it with this in fstab
192.168.0.14:/mnt/HD_a2	/mnt/temp       nfs	defaults	0	0
I get warning
> mount.nfs: trying text-based options 'vers=4,addr=192.168.0.14,clientaddr=192.168.0.157'
mount.nfs: mount(2): Protocol not supported
mount.nfs: trying text-based options 'addr=192.168.0.14'
mount.nfs: prog 100003, trying vers=3, prot=6
mount.nfs: trying 192.168.0.14 prog 100003 vers 3 prot TCP port 2049
mount.nfs: prog 100005, trying vers=3, prot=17
mount.nfs: trying 192.168.0.14 prog 100005 vers 3 prot UDP port 32770
mount.nfs: mount(2): Permission denied
mount.nfs: access denied by server while mounting 192.168.0.14:/mnt/HD_a2


this way produces a different wanting
192.168.0.14:/HD_a2		/mnt/temp      cifs  guest,_netdev  0  0 
> 
mount.cifs kernel mount options: ip=192.168.0.14,unc=\\192.168.0.14\HD_a2,_netdev,guest,ver=1,user=,pass=********
Retrying with upper case share name
mount.cifs kernel mount options: ip=192.168.0.14,unc=\\192.168.0.14\HD_A2,_netdev,guest,ver=1,user=,pass=********
mount error(6): No such device or address
Refer to the mount.cifs 8 manual page (e.g. man mount.cifs)


Thanks

Paul

---

### Post by dunkgreen on 2012-01-31
> **jpaulb said:**
> Can someone help with a Dlink DNS-321 NAS. I am at a loss as how to mount this with in fstab.
I am able to connect manually through samba. I want to have it mounted when one of the laptops boots.

If I try mount it with this in fstab
192.168.0.14:/mnt/HD_a2	/mnt/temp       nfs	defaults	0	0
I get warning

this way produces a different wanting
192.168.0.14:/HD_a2		/mnt/temp      cifs  guest,_netdev  0  0 


Thanks

Paul

Hi Paul,

I was able to mount my DNS-321 NAS by using the instructions in the D-Link forum found here:

[http://forums.dlink.com/index.php?topic=7848.0](http://forums.dlink.com/index.php?topic=7848.0)

I hope this helps you.

Regards,

Bill D-G
Toronto ON

---

### Post by Morbius1 on 2012-01-31
>  I am able to connect manually through samba. I want to have it mounted when one of the laptops boots.If by that you mean manually through Nautilus or Connect to Server then there is another way to have this happen automatically when you boot.

There's a tiny little application called Gigolo. It's based on the same mechanism that Nautilus or Connect to Server uses but it's strength is that it allows you to "Auto-Connect" to the share when you boot up. It's even smart enough to wait until the NAS is up and available before it mounts.

Here's a mini HowTo: [http://ubuntuforums.org/showpost.php?p=9941016&postcount=3](http://ubuntuforums.org/showpost.php?p=9941016&postcount=3)

---

