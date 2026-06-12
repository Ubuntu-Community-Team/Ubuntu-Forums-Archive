---
title: "Moving /home directory"
date: 2008-07-10
forum: General Help
---

### Post by VenisonMogambi on 2008-07-10
I've got Ubuntu and XP dual-booted on my PC, which has two hard drives - one is roughly 160G and the other is 80G. Both the Ubuntu and XP partitions are on the larger drive, while the second drive is mostly unused. My problem is that I allotted 20G for the Ubuntu partition, and now it's full, probably because all my mp3s are on my /home directory. To illustrate, here's my df -h output:

/dev/sda2              20G   19G  145M 100% /
/dev/sda1             120G   76G   44G  64% /media/hda1
/dev/sdb1              75G  5.4G   70G   8% /media/hdb1
/dev/sda4             8.0G  108K  8.0G   1% /osshare

What I'm planning to do is move my /home directory to the extra drive (sdb1). So I guess my questions are:
- Is that a good resolution to solve my maxed-out Linux partition issue?
- Does it matter that sdb1 is on a separate hard drive? Linux just sees it as another partition, so it shouldn't matter, correct?
- Finally, can anyone suggest a simple step-by-step showing how this would be done?

Thanks,

Venison

---

### Post by mkrahmeh on 2008-07-10
> **VenisonMogambi said:**
> - Is that a good resolution to solve my maxed-out Linux partition issue?

this should solve the problem, personally i prefer allocating home directories on a different partition than /

> **VenisonMogambi said:**
> - Does it matter that sdb1 is on a separate hard drive? Linux just sees it as another partition, so it shouldn't matter, correct?

i think yes..

> **VenisonMogambi said:**
> - Finally, can anyone suggest a simple step-by-step showing how this would be done?

generally, to change the home directory for any user, do as root:
```
sudo usermod -d /*new_path* -m *username*
```

which in ur case i guess it would be smthn like
```
sudo -d /media/hdb1/home/venison -m venison
```

actually am running on vista.. but check the -m option for copying ur files to the new home..consult the man page for usermod 

```
man usermod | grep -A 5 -- -m
```

good luck..

---

### Post by carcdrcdr on 2008-07-10
Or you could just edit your home directory in /etc/passwd on your own.  Much more streight foward.
For example 
xian:x:1000:1000:Dr Xian,,,:/home/xian:/usr/bin/zsh
Just change the 6th field.
xian:x:1000:1000:Dr Xian,,,:/my/new/home/xian:/usr/bin/zsh

---

### Post by inteluser on 2008-07-10
Another option is to copy your home directory to sdb1 (so that sdb1 just has /venison, not /home/venison) and then edit your /etc/fstab file to mount /dev/sdb1 under /home.  That way, the location of your home folder on the file system doesn't change.

---

### Post by VenisonMogambi on 2008-07-11
Thanks for all the advice.

I actually got confused with all my options and ended up following this tutorial: [http://www.ibm.com/developerworks/library/l-partplan.html](http://www.ibm.com/developerworks/library/l-partplan.html)

I think it worked, but I'm not sure. My second hard drive now shows as being mounted on /home, and when I got to /media/sdb1, my home directory is in there, but at the same time, when is do an ls for root, I see a home directory in there. 
Any thoughts? Below is my df -h ouptut and my ls / output, respectively.

venison@venison-desktop:/$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2              20G   19G  146M 100% /
/dev/sda1             120G   76G   44G  64% /media/hda1
/dev/sdb1              75G   15G   60G  21% /home
/dev/sda4             8.0G  108K  8.0G   1% /osshare

venison@venison-desktop:/$ ls /
bin    etc         initrd.img.old  mnt      root  tmp      vmlinuz.old
boot   home        lib             opt      sbin  usr
cdrom  initrd      lost+found      osshare  srv   var
dev    initrd.img  media           proc     sys   vmlinuz

---

