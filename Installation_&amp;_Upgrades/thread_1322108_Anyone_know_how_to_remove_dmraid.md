---
title: "Anyone know how to remove dmraid?"
date: 2009-11-10
forum: Installation &amp; Upgrades
---

### Post by b0b138 on 2009-11-10
LOL! and before you say duh, sudo apt-get remove dmraid, thats not quite what i meant. :D

Once upon a time I had mirrored drives. One died, decided not to mess with it anymore and keep a backup like I probably really should anyways (mirrors don't protect against human error ;) )

Well I had problems installing karmic and after checking the logs, noticed that the drive that was part of that mirror, is still being seen as part of that mirror. Like when you create the array, theres some metadata somewhere so the drive so it can go "hey, I'm part of a raid array!)

So how do I completely remove/erase/demote this labeling?

and just in case...
```
:~$ sudo dmraid -r
/dev/sdb: pdc, "pdc_bfehaige", mirror, ok, 976562500 sectors, data@ 0
```


Oh, I had tried this before but get an error
```
:~$ sudo dmraid -x

About to delete RAID set pdc_bfehaige

WARNING: The metadata stored on the raidset(s) will not be accessible after deletion
Do you want to continue ? [y/n] :y
ERROR: Raid set deletion is not supported in "pdc" format
```

---

### Post by sjarman on 2009-11-21
I had exactly the same problem with an Nvidia RAID - the only difference being the error message:

[FONT="Courier New"]ERROR: Raid set deletion is not supported in "nvidia" format[/FONT]

I managed to work around as follows:

Booted the 9.10 LiveCD
Removed dmraid using [FONT="Courier New"]> apt-get purge dmraid[/FONT]
It complained about the RO nature of the disk but removed dmraid anyway
Clicked the install icon
The partition editor now showed me my /dev/sd* partitions

Good luck!

---

### Post by trostr on 2009-11-21
I also have the same problem, purge dmraid only removes the program for me, when I install it again it will still read the metadata from the disks:
 
sudo dmraid -r
/dev/sdc: pdc, "pdc-fdiagdeb", mirror, ok, 2929687488 sectors, data@ 0
/dev/sdb: pdc, "pdc-fdiagdeb", mirror, ok, 2929687488 sectors, data@ 0
 
And same problem as thread starter when doing 
sudo dmraid -x 
 
Have tried to delete all arrays in the rocket raid 1742 controller bios but still the metadata is there.
 
testdisk show there is one extra disk named /dev/mapper/pdc_fdiagdeb
 
Is there a way to completely remove everything on the disks ? Tried dban but it didn't find the disks.

---

### Post by trostr on 2009-11-22
DBAN ([www.dban.org]("http://www.dban.org")) quick wipe of all HDD solved problem for me :)

---

### Post by oldfred on 2009-11-22
I saw in this thread the same issue and how to fix it. See Presence's comments:

Presence1960 on remove old raid setting from HD
[http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650)

---

### Post by b0b138 on 2009-11-30
Finally figured out how to remove the metadata :rolleyes:

```
sudo dmraid -rE
```

And it didn't mess with any data ;)  I did have to fsck it though

---

### Post by kkoechel on 2010-02-27
> **b0b138 said:**
> Finally figured out how to remove the metadata :rolleyes:

```
sudo dmraid -rE
```

And it didn't mess with any data ;)  I did have to fsck it though

thanks Bob, this worked for me without the fsck, cheers

---

### Post by jkest on 2011-04-29
> **trostr said:**
> I also have the same problem, purge dmraid only removes the program for me, when I install it again it will still read the metadata from the disks:
 
sudo dmraid -r
/dev/sdc: pdc, "pdc-fdiagdeb", mirror, ok, 2929687488 sectors, data@ 0
/dev/sdb: pdc, "pdc-fdiagdeb", mirror, ok, 2929687488 sectors, data@ 0
 
And same problem as thread starter when doing 
sudo dmraid -x 
 
Have tried to delete all arrays in the rocket raid 1742 controller bios but still the metadata is there.
 
testdisk show there is one extra disk named /dev/mapper/pdc_fdiagdeb
 
Is there a way to completely remove everything on the disks ? Tried dban but it didn't find the disks.

This is what I used to install Ubuntu 11.04.  Load live cd, open terminal and give the command.

ubuntu@ubuntu:~$ sudo apt-get remove dmraid

Than click the icon on desktop Install Ubuntu 11.04.  Should be able to do install, will read all of your partition. Worked for me.  Also worked the same in Ubuntu 10.10

---

### Post by phatmack18 on 2011-05-21
> **b0b138 said:**
> Finally figured out how to remove the metadata :rolleyes:

```
sudo dmraid -rE
```

And it didn't mess with any data ;)  I did have to fsck it though

Double props to b0b for posting this.  I'm running CentOS 5.6 (blasphemy?) and had been trying to mount an old failed nvidia raid hdd that had come from an old windows box and this kept causing it to fail. Thank you thank you thank you!!

---

