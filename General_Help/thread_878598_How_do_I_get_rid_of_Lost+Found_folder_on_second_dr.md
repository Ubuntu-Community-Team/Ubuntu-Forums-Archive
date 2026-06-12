---
title: "How do I get rid of Lost+Found folder on second drive?"
date: 2008-08-03
forum: General Help
---

### Post by b9k9kiwi on 2008-08-03
I built a new PC and installed Ubuntu (Hardy Heron) on a used 160Gb Sata HD.

After a couple of weeks playing around I decided that I was going to keep Ubuntu as the OS for this PC and purchased a new 500Gb Sata HD for it, and did a fresh install.

I then reconnected the 160Gb drive as the second drive and repartitioned it and formatted it with Gparted.  Initially I had boot menu, mounting and write access problems, but a trawl of the forums provided me with the info to fix these.

I can write to and read from the 160Gb disk but a Lost+Found folder also resides there apparently occupying some 20Gb, which I cannot read or send to trash.  How can I get rid of this folder?

(Note: Gparted tells me that the 160Gb drive is /Dev/Sdb1 mounted at /Media/Disk and formatted to ext3)

---

### Post by dexter.deepak on 2008-08-03
cant you access it as root ? have you tried something like :
```
sudo rm -rf Lost+Found
```

---

### Post by b9k9kiwi on 2008-08-03
> **dexter.deepak said:**
> cant you access it as root ? have you tried something like :
```
sudo rm -rf Lost+Found
```

I do not have sufficient Sudoese to ensure that I am accessing sdb1 rather than sda1 (bearing in mind that there is also a Lost+Found folder on sdba1).  Anyway, just as an indicator of the general setup I executed the following;

tony@MusicMachine:~$ sudo df -h
sudo: unable to resolve host MusicMachine
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             460G   44G  394G  10% /
varrun                506M  924K  505M   1% /var/run
varlock               506M     0  506M   0% /var/lock
udev                  506M   60K  506M   1% /dev
devshm                506M  372K  506M   1% /dev/shm
lrm                   506M   39M  467M   8% /lib/modules/2.6.24-19-generic/volatile
/dev/sdb1             148G  3.3G  138G   3% /media/disk
/dev/sdc1             3.7G  2.9G  781M  79% /media/TONY'S IPOD

... you will note the "sudo: unable to resolve host MusicMachine" which has really thrown me.

Lost+Found on sdb1 is flagged as 'read only' and 'unreadable' The above would indicate that Lost+Found is occupying about 13Gb (the 3.3Gb used is a backup from one of the other PCs on the network) as the drive is definately a 160Gb (equiv. to about 163.7G).

---

### Post by Elfy on 2008-08-03
You need to deal with the host thing first, there should be enough info here to help with that.

[https://answers.launchpad.net/ubuntu/+question/32783](https://answers.launchpad.net/ubuntu/+question/32783)

Once you've sorted that use nautilus as root to check what is actulally in the LOst and Found, afaik files get put there if there is a problem when doing boot disc checks.

```
gksudo nautilus
```

You can check the content of the folders as root then - if you delete content you need to make sure to empty the root trash - or use Shift+Delete

---

### Post by geirha on 2008-08-03
160GB is that the capacity listed on the harddrive? harddrive manufacturers list drive capacity in si-units. 160*10^9 = 160,000,000,000 bytes. In computers though, it makes more sense to use powers of 2 rather than 10, and that is what df -h uses. 160*10^9/2^30 = 149GiB. You can have df list si-units instead, by using the --si option
```
sudo df --si
```

---

### Post by louieb on 2008-08-03
As others have described you can get rid of it. But like a bad penny it will come back. Its a folder used by **fsck** to store stuff its found. Sort of like those temp#### files windows creates after running chkdsk.

---

### Post by Elfy on 2008-08-03
> **louieb said:**
> As others have described you can get rid of it. But like a bad penny it will come back. Its a folder used by **fsck** to store stuff its found. Sort of like those temp#### files windows creates after running chkdsk.
Thanks - I've reworded my post to make a bit more sense - as I know that it will be back and it's a bit pointless to delete it in itself.

---

### Post by b9k9kiwi on 2008-08-03
> **forestpixie said:**
> You need to deal with the host thing first, there should be enough info here to help with that.

[https://answers.launchpad.net/ubuntu/+question/32783](https://answers.launchpad.net/ubuntu/+question/32783)

Once you've sorted that use nautilus as root to check what is actulally in the LOst and Found, afaik files get put there if there is a problem when doing boot disc checks.

```
gksudo nautilus
```

You can check the folders as root then - if you delete them you need to make sure to empty the root trash - or use Shift+Delete

Thank you.  I have fixed the hostname problem and deleted the Lost+Found on sdb1 (which appeared to be empty by the way).

 sudo df -h returned the same result as before - sdb1 is only a backup disk for other PCs on the network and 140Gb or so is more space than they will ever need, so I don't think that you or I should lie awake worrying about the apparent missing 13Gb :).

thanks again.

---

### Post by Elfy on 2008-08-03
As noted by louieb it will likely be back 

Can you mark thread as solved then please :)

---

