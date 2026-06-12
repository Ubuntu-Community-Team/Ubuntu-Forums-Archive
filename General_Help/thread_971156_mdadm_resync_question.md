---
title: "mdadm resync question"
date: 2008-11-04
forum: General Help
---

### Post by reggler on 2008-11-04
Hi There,

I have a Promise Fasttrack TX2000 RAID controller that I used in an older system to access my RAID-1 array. Now this old machine broke down and i wanted to move the raid controller incl. disks into my workstation to have all data locally. Unfortunately seems as if my acer main board doesn't play with the promise raid controller.... 
#1 i can't access the raid controller's bios on boot up
#2 instead of one disk array /dev/sdX I see two single drives and if i write data on one disk, it's not written to the other one automatically.
So I though I'd setup a linux software raid-1 array with mdadm....but I can't lose the data that's existing on these two disks.... so now, how should i go about this? 
I figured out following:
```
Create a RAID 1 volume from two drives.

 mdadm --create /dev/md0 --level=1 --raid-devices=2 /dev/sdc /dev/sde

To add RAID device md0 to /etc/mdadm.conf so that it is recognized the next time you boot.

mdadm -Es | grep md0  >>/etc/mdadm.conf

View the status of a multi disk array.

 mdadm --detail /dev/md0

View the status of all multi disk arrays.

 cat /proc/mdstat

```

But the problem is, when it's resyncing (it does this automaticaly, yes???) i don't know if it's taking data from /dev/sdc or /dev/sde (in this example) as source data.
Any one able to help me please?
Thanks a lot!

---

### Post by fjgaude on 2008-11-05
Well, from what I know what you are doing will not save your data, if you think one of the two drives has good data.

When you "create" an array with **mdadm** you have to then install a filesystem, and that removes any data on drives in the array.

Thus we think of backups... always have backups of important data, I have three, one online, another near-line, and finally, one off-line.

Here's some stuff to study, read:

[http://shsc.info/LinuxSoftwareRAID](http://shsc.info/LinuxSoftwareRAID)
/usr/share/doc/mdadm/FAQ.gz  and md.txt.gz
[http://blog.tcg.com/tcg/2006/04/recovering_raid.html](http://blog.tcg.com/tcg/2006/04/recovering_raid.html)
[http://tldp.org/HOWTO/Software-RAID-HOWTO.html](http://tldp.org/HOWTO/Software-RAID-HOWTO.html)

Let us know what you decide to do.

---

### Post by psusi on 2008-11-05
Pick one disk that you think has the "good" data still and mount it.  Take the other disk and use mdadm to add it to a single disk raid1.  Format a filesystem on the raid array, then mount it, then copy all of the files from the good single disk to the array.  Unmount the single disk and add it to the array.

Also since you were using these disks in a fake raid array, the metadata is still on the disks which will be recognized and confuse some parts of the system.  If you do not plan on using them this way any more, then you will want to get rid of that metadata.  Install the dmraid package then run sudo dmraid -rE /dev/sdX for each disk in the array.

---

### Post by reggler on 2008-11-07
> **psusi said:**
> Pick one disk that you think has the "good" data still and mount it.  Take the other disk and use mdadm to add it to a single disk raid1.  Format a filesystem on the raid array, then mount it, then copy all of the files from the good single disk to the array.  Unmount the single disk and add it to the array.

Also since you were using these disks in a fake raid array, the metadata is still on the disks which will be recognized and confuse some parts of the system.  If you do not plan on using them this way any more, then you will want to get rid of that metadata.  Install the dmraid package then run sudo dmraid -rE /dev/sdX for each disk in the array.

Huh,

Do I really need to create a new file system? Wouldn't this work:
Insert just one disk with good data:
```
mdadm --create /dev/md0 --level=mirror --force --raid-devices=2 /dev/sdc --spare-devices=1 /dev/sdb
```
Then insert the second disk and issue a:
```
mdadm --assamble --uuid=/dev/md0 --update resync
``` 
Wouldn't this work? 
Regarding meta data, since I can read the data from a single disk with no raid controller without any problems, couldn't it justs be that there's no meta data on the partition and instead the array was handeled by the controller itself, not writing any additional stuff to the disk?
I'm not sure tho....but....is this an option at all?

---

### Post by psusi on 2008-11-07
In theory it is best to format after building the raid array since mdadm adds its own metadata to the disk, and depending on where it puts it, it might corrupt any existing filesystem.

The fake raid controller definitely writes metadata to the disk.  Some other controller isn't going to recognize it of course, which is why it works like a single disk, but the data is still there, and there are parts of Ubuntu that will recognize it and think the disks should not be used directly because they are part of a fakeraid set.

Also you don't ever need to use --assemble.  As soon as you add the second disk to the active array it should start resyncing.

---

### Post by reggler on 2008-11-07
So okay, I'm getting that now lets see if I understood this right: assume I create my disk array with this command ```
mdadm --create /dev/md0 --level=mirror --force --raid-devices=2 /dev/sdc --spare-devices=1 /dev/sdb
```
when /dev/sdc is connected but not /dev/sdb.
Then I'll create a new file system on /dev/md0 with following command ```
mke2fs -j /dev/md0

```
Then I'll mount my harddisk that's gonna be /dev/sdb into my external USB disk housing and copy all the data from /dev/sdX (USB) to /dev/md0 using ```
cp -r /mountpoint/USB /mountpoint/md0
```(just saying this cause I'm not supposed to use dd - am I?)
Once this has been completed I put the USB disk down into my system - on bootup it's gonna appear as /dev/sdb to the raid array and synchronizing is gonna start automatically.
Did I get this right? Would my system be rocking like that?:guitar:

Thanks for taking the time to explain me how it's going so I won't lose my data :)

Ron

---

### Post by psusi on 2008-11-09
No need to muck around with external USB enclosures, and you can't add a spare device that isn't connected.  Just create the array initially with only a single device, then once you copy the data to it, you add the second disk later, and let it sync up.

mdadm --create /dev/md0 --level=mirror --force --raid-devices=1 /dev/sdc

Then later ( once you have moved the data from sdb to md0 ):

mdadm /dev/md0 --add /dev/sdb

---

### Post by reggler on 2008-11-10
> **psusi said:**
> No need to muck around with external USB enclosures, and you can't add a spare device that isn't connected.  Just create the array initially with only a single device, then once you copy the data to it, you add the second disk later, and let it sync up.

mdadm --create /dev/md0 --level=mirror --force --raid-devices=1 /dev/sdc

Then later ( once you have moved the data from sdb to md0 ):

For this, last step I need my usb adapter (to copy the data from the single disk to the array).

---

### Post by psusi on 2008-11-10
> **reggler said:**
> For this, last step I need my usb adapter (to copy the data from the single disk to the array).

Why?  Just connect the disk normally inside the computer.

---

### Post by reggler on 2008-11-10
> **psusi said:**
> Why?  Just connect the disk normally inside the computer.
lol, cause it's an ATA disk and i don't have any spare ATA connectors on the main board other than that one - yes i know, i just could connectd it as a slave.... there's different solutions to get the data copied over lol :KS

---

