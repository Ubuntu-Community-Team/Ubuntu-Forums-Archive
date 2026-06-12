---
title: "Reinstall /boot partition on fakeRAID0"
date: 2009-07-17
forum: Installation &amp; Upgrades
---

### Post by WIGGMPk on 2009-07-17
To save the gory details of inexperience and lack of sleep, I will just cut to the chase.

I have 3 paritions on a fakeRAID setup on Jaunty amd64:

/boot - Originally configured as ext4
/     - Has not been touched so should still be ext4
/home - Has not been touched so should still be ext4

As far as I can tell, my /boot parition is 100% borked. It is only configured for 512 MB of space and it seems its pretty much free lol.

My question is how do I reinstall (I think its too late to 'repair' the parition at this point) the /boot partition? Is it as easy as just popping in the Jaunty alternative CD and just installing /boot to the available space?

I have tried several times to mount the /boot partition in the LiveCD with no luck. It complains about Wrong FS type or bad sectors or bad superblock. Despite using the "mount -t ext4" options. I have tried mounting like this:

```
sudo mount -t ext4 /dev/sda1 /media/BOOT
```
And I have tried like this:
```
sudo mount -t ext4 /dev/mapper/icw_&(#(&(%_MobileRaid1 /media/BOOT
```

I dont remember what the icw_&(#(&(%_MobileRaid1 is actually called but you get the picture. I have also tried both of the above mount options wihtout the -t ext4 flag.

I am just not experienced enough to figure things out. Hence this post. I desperatly need to reinstall my /boot parition.

(Please spare me the details on why fakeRAID sucks and why I should be using the softRAID built into Ubuntu. I didnt do a lot of research when I first set things up and its too far along to start over for me)

---

