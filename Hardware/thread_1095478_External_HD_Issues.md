---
title: "External HD Issues"
date: 2009-03-13
forum: Hardware
---

### Post by liquidypoo on 2009-03-13
Alright, so I searched before typing up this thread, and I did the three commands that I saw taurus recommend a couple of times, and it didn't do too much.  But, of course, there's a catch here:  my external hard drive is a bit of a special case.  I upgraded my PS3's hard drive, and ordered a Startech Infosafe drive enclosure so I could turn the old drive into an external.  Standard problem, Ubuntu sees it but can't mount it.  Lucky for me, I managed to scrounge up some further info for you!

```
ed@lappy:~$ dmesg | tail
[104941.496389] sd 6:0:0:0: [sdb] Write Protect is off
[104941.496398] sd 6:0:0:0: [sdb] Mode Sense: 38 00 00 00
[104941.496403] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[104941.497762] sd 6:0:0:0: [sdb] 117210240 512-byte hardware sectors (60012 MB)
[104941.500014] sd 6:0:0:0: [sdb] Write Protect is off
[104941.500021] sd 6:0:0:0: [sdb] Mode Sense: 38 00 00 00
[104941.500026] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[104941.500033]  sdb: unknown partition table
[104941.515853] sd 6:0:0:0: [sdb] Attached SCSI disk
[104941.515935] sd 6:0:0:0: Attached scsi generic sg2 type 0
ed@lappy:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2226eb33

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9355    75144006   83  Linux
/dev/sda2            9356        9729     3004155    5  Extended
/dev/sda5            9356        9729     3004123+  82  Linux swap / Solaris

Disk /dev/sdb: 60.0 GB, 60011642880 bytes
64 heads, 32 sectors/track, 57231 cylinders
Units = cylinders of 2048 * 512 = 1048576 bytes
Disk identifier: 0x6cc660a2

Disk /dev/sdb doesn't contain a valid partition table
ed@lappy:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              71G   13G   55G  20% /
varrun                502M  104K  501M   1% /var/run
varlock               502M     0  502M   0% /var/lock
udev                  502M   60K  501M   1% /dev
devshm                502M  908K  501M   1% /dev/shm
lrm                   502M   39M  463M   8% /lib/modules/2.6.24-23-generic/volatile

```

If I have to wipe the disc, then I'm cool with that.  Don't need the PS3's stuff on there anyway.  Also, the enclosure did come with a driver disc, but I naturally have no idea how to install them on Ubuntu, if it's even possible.  I did install them through Wine, thinking I could use Wine's browse function, but then I realized Wine only looks at the c:/ drive it creates.  Anybody know what to do?

---

### Post by taurus on 2009-03-13
Install gparted.  Then, use it to create a partition on your external drive, /dev/sdb1, and format it to whatever filesystem you want.  Once you have done that, you can mount it in Ubuntu and start using it.

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install gparted
gksudo gparted
```

---

### Post by liquidypoo on 2009-03-15
Thanks!

Sorry about replying so late.  After posting my question, I ended up just kind of forgetting about this completely, but I'm glad I remembered to come back and check on this.  I now have a functioning external hard drive that's plug 'n play.  Seriously, thank you!

---

### Post by colintivy on 2009-03-15
Hi Taurus,

Read this post with interest. I have a similar problem, except that my spare HD has the original Win 98SE OS plus a lot of Win-based guff that I do not care about on it. This would seem to prevent my present 8.04 to even to recognise the HD (in an enclosure and with only .exe drivers on) is there. I would like to reformat it to Ext3 and use it to back up the HD in my laptop. I intend to create an extra partition on both HDs to contain my Home folder so that fiddling about with OSs etc is less hazardous. I have downloaded the massive instruction sheets on doing this on the assumption that they are the authorized method, am I right? Now that 9.04 is looming this will be important.

colintivy :-)

---

### Post by taurus on 2009-03-15
> **colintivy said:**
> Hi Taurus,

Read this post with interest. I have a similar problem, except that my spare HD has the original Win 98SE OS plus a lot of Win-based guff that I do not care about on it. This would seem to prevent my present 8.04 to even to recognise the HD (in an enclosure and with only .exe drivers on) is there. I would like to reformat it to Ext3 and use it to back up the HD in my laptop. I intend to create an extra partition on both HDs to contain my Home folder so that fiddling about with OSs etc is less hazardous. I have downloaded the massive instruction sheets on doing this on the assumption that they are the authorized method, am I right? Now that 9.04 is looming this will be important.

colintivy :-)

What happens if you turn on your external drive and plug it in, does it automount?  Otherwise, open a terminal and post the output of this command to see if that drive is even listed.

```
sudo fdisk -l
```

---

### Post by colintivy on 2009-03-17
> **taurus said:**
> What happens if you turn on your external drive and plug it in, does it automount?  Otherwise, open a terminal and post the output of this command to see if that drive is even listed.

```
sudo fdisk -l
```

Hi Taurus,

Thanks for that, Ext USB HD plugged in and no response. I fdisked which shows the same I think:-

Device      Boot   Start    End       Blocks    Id    System
/dev/sda1    *       1     1439      11719386   83     Linux
/dev/sda2          1460    1521       498815    82     Linux Swap/Solaris

How do you lot manage to paste the output of such things into a forum reply??

The HD was working as a Windows-based system on my laptop. Before installing Ubuntu 8.04 I replaced the drive with a brand new one so the installation was entirely clean. Hardy works quite well and fulfills my expectations of it. I will probably migrate to 9.04 in due course especially if some of the odd niggles have been removed in my current version; if not, I will wait for the LTS to come to an end.

Thanks for your time, with that number of posts you must be A Very Busy Person!!

colintivy :)

---

