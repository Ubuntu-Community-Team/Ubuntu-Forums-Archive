---
title: "New install server -newbe- unable to do anything with folders + many other problems"
date: 2008-12-15
forum: Installation &amp; Upgrades
---

### Post by pinkpanther on 2008-12-15
Assembled new computer:
3 drives 80, 200, 80gb
Intention: 1st drive op system and local files. 2nd drive for file storage. 3rd drive for different file storage.
 
(why? early windows install with just one hard drive, a program overwrote some of the op files and destroyed all the files. Had back up using MSBackup, it refused to restore as incompatible with original system, same installation off same disk.Ever since used separate hard drives for storage and backed up copying files on further hard drive)

Partitioned sda as normal 80gb ext3, sdb as single 200gb fat32, & sdc as single 80gb fat32.

sudo mkdir /info and sudo mount /info (chose sdb)
modified smb.conf file to allow windows computers on local network to access and save/delete or modify files only on /info.

Problems:
Can see /info on network but [access denied].
Can cd /info
Cannot chown /info  [Operation not permitted]
Cannot delete /info [Device or resource busy] even with nothing else running and network not connected.
ls -l from root does not show /info

using file system on xfce shows /info as root owner read only so chown's did not work. 

This has been about 2 weeks reading / and trying. Ready to give up. There appears to be too much type this and type that without explaining why and many of the examples from else ware do not match the manuals so making it even more confusing. I have reformatted the whole system twice now so that the many mistakes cannot have corrupted install.But??

Any thoughts

Mike:confused:

---

### Post by joff13 on 2008-12-16
> **pinkpanther said:**
> Assembled new computer:
3 drives 80, 200, 80gb
Intention: 1st drive op system and local files. 2nd drive for file storage. 3rd drive for different file storage.
 
(why? early windows install with just one hard drive, a program overwrote some of the op files and destroyed all the files. Had back up using MSBackup, it refused to restore as incompatible with original system, same installation off same disk.Ever since used separate hard drives for storage and backed up copying files on further hard drive)

Partitioned sda as normal 80gb ext3, sdb as single 200gb fat32, & sdc as single 80gb fat32.

sudo mkdir /info and sudo mount /info (chose sdb)
modified smb.conf file to allow windows computers on local network to access and save/delete or modify files only on /info.

Problems:
Can see /info on network but [access denied].
Can cd /info
Cannot chown /info  [Operation not permitted]
Cannot delete /info [Device or resource busy] even with nothing else running and network not connected.
ls -l from root does not show /info

using file system on xfce shows /info as root owner read only so chown's did not work. 

This has been about 2 weeks reading / and trying. Ready to give up. There appears to be too much type this and type that without explaining why and many of the examples from else ware do not match the manuals so making it even more confusing. I have reformatted the whole system twice now so that the many mistakes cannot have corrupted install.But??

Any thoughts

Mike:confused:

Hi mike
i'm wondering why are you installing server edition and not the desktop one...

anyway, i think it is difficult to chown on a partition... to change permission you need to modify th /etc/fstab and add rw perm to useron the /info mountpoint

and also

```
Cannot delete /info [Device or resource busy]
```

of course, this is a mount point, you have to unmount first and then you can delete the directory, if this is what you want...

---

### Post by pinkpanther on 2008-12-16
Thanks for reply.
Chose server as I will not be using it as desktop and felt the less cluttered the better. I am also using it as a method of learning. 

I regret I have some specialist software running on the windows machines which is not available for Linux otherwise the change would be immediate for all the computers.

Your suggestions have given me some new options which I will try later

Thanks.
Mike

---

