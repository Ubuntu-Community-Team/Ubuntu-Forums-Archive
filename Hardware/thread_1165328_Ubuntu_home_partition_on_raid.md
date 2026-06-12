---
title: "Ubuntu home partition on raid"
date: 2009-05-20
forum: Hardware
---

### Post by whoop on 2009-05-20
I recently had a hard-disk failure (thank god for backups), and therefore I am looking for possible and affordable raid configurations for one of my current machines.

I have an Asus p5b motherboard which has one internal sata_raid slot and one external esata_raid slot, being driven by the Intel ICH8 chip. The motherboard also has 4 (normal) sata slots.
If I am not mistaken this setup is not hardware raid but just hybrid/fake raid that is configurable via the BIOS?
I currently have one hard-disk on sata1 with ubuntu on it. I am thinking about buying two more hard-disks (same brand an model) and setting them up as a RAID1 configuration for my /home partition. So I have some questions:


**Questions:**
1 Should I use these (special) raid slots, or should I just use the regular sata slots (as I believe all raid operations will be done by regular cpu computation anyway and you still require os drivers for the onboard raid solution).

2 For the onboard raid configuration you need the JMB363 driver (for windows anyway). Am I correct if I say that the JMB363 functionality is supported under ubuntu via dmraid?

3 Do I need to reinstall? I want to use the raid1 just for my home (my /home is currently on the / partition). I am wondering if it is possible to just add the disks (make them work using dmraid(faikraid) or mdadm(softwareraid) and move my home to the raid1 without reinstalling.

4 Why does [https://help.ubuntu.com/community/FakeRaidHowto#Set%20Up%20the%20Bootloader%20for%20RAID](https://help.ubuntu.com/community/FakeRaidHowto#Set%20Up%20the%20Bootloader%20for%20RAID) say:
"Warning: FakeRAID is not supported by Ubuntu. Trying to install Ubuntu on such a partition could easily result in the loss of all your data."
Does it mean you shouldn't install the ubuntu OS on a faikeraid or does it also mean you shouldn't use my idea (use faikeraid for the /home partition). How serious is this warning? Is everybody using faikeraid mad? It doesn't realy make sense you (often) use raid to save your data, and this raid solution is dangerous? Does this warning not apply when I use software raid (and just add the two hard-disks to regular sata2 and sata3)?


Well, allot of questions.... I think I know the answers to all of them I just need some reassurance guys:D At least for some of my questions... I only did two raid setups (from scratch) in my life, just one of them was softwareraid (and that was for testing purposes). So I'm not that confident about my knowledge concerning raid yet ;)

---

### Post by ronparent on 2009-05-20
1 It depends on whether you need to dual boot with some version of windows. If you do, then you are dependent on the hardware raid ports to access the raid drives with windows. In that case you would be using the 'fakeraid' setup in ubuntu (dmraid), providing that your motherboard controller is compatible (it probably is). If not you can go with a software raid which will allow you to connect your raid drives to any port.

2  The funtionality is supported in ubuntu through dmraid (in most cases). 

3 It should not be necessary to reinstall.  As a matter of fact, if a partition is formatted so it can be read by either windows or ubuntu, your data should be accessibly by either (using a fakeraid of course.

4 Although the warning applys primarily to prior version of ubuntu, you do have to have enough understanding of what you are doing to avert disaster. Since you are planning to use a raid1 setup, you should generally be safe since data is mirrored on the second drive.  The people who are mad are probably using raid0 and unwittingly destroyed all their raid data.

Checkout these sites if you haven't already seen them:
[http://bbossola.wordpress.com/2008/03/07/dmraid-on-ubuntu-with-sata-fakeraid/](http://bbossola.wordpress.com/2008/03/07/dmraid-on-ubuntu-with-sata-fakeraid/)
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

Hope these short answers are some help. Good luck.

---

### Post by whoop on 2009-05-20
> **ronparent said:**
> 1 It depends on whether you need to dual boot with some version of windows. If you do, then you are dependent on the hardware raid ports to access the raid drives with windows. In that case you would be using the 'fakeraid' setup in ubuntu (dmraid), providing that your motherboard controller is compatible (it probably is). If not you can go with a software raid which will allow you to connect your raid drives to any port.

2  The funtionality is supported in ubuntu through dmraid (in most cases). 

3 It should not be necessary to reinstall.  As a matter of fact, if a partition is formatted so it can be read by either windows or ubuntu, your data should be accessibly by either (using a fakeraid of course.

4 Although the warning applys primarily to prior version of ubuntu, you do have to have enough understanding of what you are doing to avert disaster. Since you are planning to use a raid1 setup, you should generally be safe since data is mirrored on the second drive.  The people who are mad are probably using raid0 and unwittingly destroyed all their raid data.

Checkout these sites if you haven't already seen them:
[http://bbossola.wordpress.com/2008/03/07/dmraid-on-ubuntu-with-sata-fakeraid/](http://bbossola.wordpress.com/2008/03/07/dmraid-on-ubuntu-with-sata-fakeraid/)
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

Hope these short answers are some help. Good luck.

Thanks for your response, it proved quite useful. The second link you provided led me to [http://linux.yyz.us/why-software-raid.html](http://linux.yyz.us/why-software-raid.html). After reading that I am leaning towards using software raid even though I have a hybrid raid controller on my system. There seem to be more advantages in using software raid then using fake raid. I do only dual boot to other *nix os's so I have no real benefit when going for fake raid.

---

### Post by whoop on 2009-05-20
This: [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)
will probably quite useful to create my home partition on the raid1 without having to reinstall ubuntu.

---

### Post by ronparent on 2009-05-24
Thanks for that last reference. I have been puzzling over whether or not to create a separate /home partition. 

As long as you don't plan to dual boot windows, then your decision to use software raid sounds best. Good luck.

---

### Post by hotweiss on 2009-05-26
1) Use the RAID slots

2) Yes, it's supported.

3) Don't know.

4) Don't worry. I've been using RAID 0 without any problems for a year now. The performance increase is notable.

Just remember that the alternate CD supports RAID during installation. And remember to set-up your RAID array first in your RAID BIOS.

---

### Post by whoop on 2009-05-26
> **hotweiss said:**
> 1) Use the RAID slots

2) Yes, it's supported.

3) Don't know.

4) Don't worry. I've been using RAID 0 without any problems for a year now. The performance increase is notable.

Just remember that the alternate CD supports RAID during installation. And remember to set-up your RAID array first in your RAID BIOS.

How is your stand on:[http://linux.yyz.us/why-software-raid.html](http://linux.yyz.us/why-software-raid.html)
After reading that I felt the urge for software raid over fake raid...

---

### Post by hotweiss on 2009-05-27
> **whoop said:**
> How is your stand on:[http://linux.yyz.us/why-software-raid.html](http://linux.yyz.us/why-software-raid.html)
After reading that I felt the urge for software raid over fake raid...

Well I use dmraid (the one that comes on the alternate CD). It's a combination of fake raid and software raid. No problems what so ever...

---

### Post by whoop on 2009-06-02
OK, I have a basic plan how to set up two new hard disks for raid1 and put my existing home folder on there:

1:
Connect two hard disks

2:
boot jaunty
```

apt-get install mdadm

```
Select Internet Site leave rest default (for postfix)

3:
create identical partitions with cfdisk on sdb1 and sdc1

4:
create raid
```

mdadm --create --verbose /dev/md0 --level=1 --raid-devices=2 /dev/sdb1 /dev/sdc1

```

5:
make file system
```

mkfs.ext3 /dev/md0

```

6:
edit /etc/mdadm/mdadm.conf
```

DEVICE        /dev/sdb1 /dev/sdc1
ARRAY        /dev/md0 devices=/dev/sdb1,/dev/sdc1

```
Create temporary homedir
```

mkdir /home_tmp

```
edit fstab
```

/dev/md0 /home_tmp ext3 defaults,errors=remount-ro 0 1

```

7:
Reboot the check if raid array is properly mounted.
Copy contents of home folder to raid1
```

sudo bash
cd /home
find . -depth -print0 | cpio --null --sparse -pvd /home_tmp/

```

8:
reboot in recovery mode to finalize new home raid1 set up
```

mv /home /home_backup

```
edit /mnt/etc/fstab
```

/dev/md0 /home ext3 nodev,nosuid 0 2

``````

chown -R username:username /home/username
chmod 644 /home/username/.dmrc
chmod 644 /home/username/.ICEauthority
exit

```
do a normal resume

Check status of raid array:
```

sudo mdadm --query --detail /dev/md0

```

Requests:
*I think this will work; if anybody sees any caveats please let me know.

*With this set-up I believe errors will go to /var/mail/root (if I am not mistaken). Is there anyway I could get this in my own mailbox (cause postfix times out using my isp's server, or maybe I am doing something wrong)?

*If anybody knows any nice/cool/handy monitoring tools (concerning this topic) please let me know.

---

### Post by whoop on 2009-06-04
Well, I went ahead and did it. It works great, and I am pleased with the performance :D After I configured everything a came to the conclusion that my md0 raid partition was to small. I was able to enlarge it while I was running the system (in the actual account) :shock: Amazing!

Here's what I did:

```

sudo bash
mdadm --manage /dev/md0 --fail /dev/sdb1
mdadm --manage /dev/md0 --remove /dev/sdb1

```
Start up gparted and resize /dev/sdb1 to new size.
```

mdadm --manage /dev/md0 --add /dev/sdb1
cat /proc/mdstat

```
Keep running cat /proc/mdstat until raid array is fully recovered.
```

mdadm --manage /dev/md0 --fail /dev/sdc1
mdadm --manage /dev/md0 --remove /dev/sdc1

```
Start up gparted and resize /dev/sdc1 to the same size as /dev/sdb1.
```

mdadm --manage /dev/md0 --add /dev/sdc1
cat /proc/mdstat

```
Keep running cat /proc/mdstat until raid array is fully recovered.
```

mdadm --grow /dev/md0 --size=max
resize2fs /dev/md0
cat /proc/mdstat

```
Keep running cat /proc/mdstat until raid array is fully recovered.
done...

---

### Post by whoop on 2010-01-15
To recreate raid array:
Install mdadm

run:
```

mdadm --assemble /dev/md3 /dev/sda4 /dev/sdb4

```

Continue with step 8.

---

