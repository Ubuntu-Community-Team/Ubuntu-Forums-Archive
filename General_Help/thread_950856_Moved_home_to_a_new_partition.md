---
title: "Moved /home to a new partition"
date: 2008-10-17
forum: General Help
---

### Post by visio159 on 2008-10-17
I moved the /home to another partition by just copying it on another ext3 partition.
Previously I had only / and swap. but now I have /, /home and swap.

All is working fine but there is one doubt. How do I delete the /home content from / partition. I think its just lost and consuming space. Any advice ?


Another short quirk is that how to remove old version packages from cache in /var after updating.

Is it apt-get unclean or something like this. But will i be sure that there will be no effect on some proggies requiring older versions ?

Thanks you all :lolflag:

---

### Post by ilrudie on 2008-10-17
Fisrt run a df -kh to make sure the drive you think you are using as home is actually mounted as /home.  Then boot into single user mode (logs you in as root which shouldn't require /home).  umount /home.  df -kh to verify that /home is no longer mounted.  Then remove the files from the /home directory and reboot*.  

*I assume you already added the /home partition to /etc/fstab but if you have trouble rebooting after cleaning out the /home directory it probably means that /home is not in /etc/fstab so you might want to research how to use fstab and verify that its setup to automount /home before booting into recovery mode.  As always its a good idea to backup anything you can't stand to lose in case something goes wrong.

---

### Post by bodhi.zazen on 2008-10-17
Yes, take care that the old home is not being used and you have copied everything before you remove it.

IMO you should mount the root partition from a live CD, move the old /home directory ot a back up location such as /home_old, and reboot.

If the new home is working you can then :

```
rm -rf /home_old
```

This is a great reference :

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by jerome1232 on 2008-10-17
Along with what ilrude is saying. The way to delete anything that might be present there is to boot into a live cd, mount your / partition, then delete anything under /home.  I'll give an example using /dev/sda1 as your root partition. So long as /home isn't mounted there (as in my example) this will remove any lingering files on your root partition.

edit: Also bodhi.zazen's approach is more cautious than mine. It ensures you are in fact removing the old files beyond a doubt.

```
sudo mkdir /media/root
sudo mount /dev/sda1 /media/root
sudo rm -rf /media/root/home/*
sudo umount /dev/sda1
sudo reboot
```

---

### Post by visio159 on 2008-10-17
Yes, I have confirmed that the new partition is mounted as /home (I checked it in Gparted)

I have also added fstab entries using UUID for new /home partition, its working fine.

I guess I have to pop in live cd to remove the stray space occupied by lost /home partition :p

Thanks a lot for your time :)

Can someone tell me to about the second problem too ?

---

### Post by jerome1232 on 2008-10-17
This will remove the old versions from cache, the second one I believe completly clears the cache

```
sudo apt-get autoclean
sudo apt-get clean
```

---

