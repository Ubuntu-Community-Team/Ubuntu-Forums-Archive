---
title: "dmraid doesn't activate at startup"
date: 2009-05-10
forum: Installation &amp; Upgrades
---

### Post by Epistaxis on 2009-05-10
Background: I installed Jaunty on a two-disk RAID 0 using the Alternate Install disc (because the live USB install kept giving me [Errno 5], even on a separate non-RAID machine), and I had to activate dmraid and install GRUB manually from the shell since the Alternate Install failed for both things.

Short version: After a while on the splash screen, Ubuntu drops to an initramfs shell because it didn't find my drives. I simply type "dmraid -ay" there and it can continue loading with no problem.


Long version: Here's what I see after the splash screen.
```
Starting up ...
Loading, please wait...
no block devices found
no block devices found
no block devices found
ERROR: either the required RAID set not found or more options required
/dev/sdb: "pdc" and "isw" formats discovered (using isw)!
/dev/sda: "pdc" and "isw" formats discovered (using isw)!
ERROR: either the required RAID set not found or more options required
no raid sets and with names: "no block devices found"
Gave up waiting for root device.  Common problems:
- Boot args (cat /proc/cmdline)
  - Check rootdelay= (did the system wait long enough?)
  - Check root= (did the system wait for the right device?)
- Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/mapper/isw_bddbeigae_Volume02 does not exist. Dropping to a shell!
```

Here's what happens if I try the diagnostics it suggests (truncated to relevant parts):
```
(initramfs) cat /proc/cmdline
root=/dev/mapper/isw_bddbeigae_Volume02 ro quiet splash
(initramfs) cat /proc/modules
...
dm_raid4_5 74768 0 - Live ...
dm_region_hash 20992 1 dm_raid4_5, Live ...
dm_mem_cache 13824 1 dm_raid4_5, Live ...
dm_message 11904 1 dm_raid4_5, Live ...
(initramfs) ls /dev/mapper/
control
```

Here's what I have to do:
```
(initramfs) dmraid -ay
/dev/sdb: "pdc" and "isw" formats discovered (using isw)!
/dev/sda: "pdc" and "isw" formats discovered (using isw)!
RAID set "isw_bddbeigae_Volume0" was activated
RAID set "isw_bddbeigae_Volume01" was activated
RAID set "isw_bddbeigae_Volume02" was activated
RAID set "isw_bddbeigae_Volume03" was activated
```

Verification that the RAID is now activated:
```
(initramfs) ls /dev/mapper/
control                  isw_bddbeigae_Volume01  isw_bddbeigae_Volume03
isw_bddbeigae_Volume0    isw_bddbeigae_Volume02
```

Finish booting:
```
(initramfs) exit
```


It's likely that I did something wrong in installation when I did certain things manually because the installer failed; if anyone can tell me what that was, I'd like to fix it. Otherwise, can I just stick "dmraid -ay" in a batch file somewhere?

---

### Post by ohnoezitasploded on 2009-09-23
I'm also having this problem after an update.  2.6.28.11 boots up fine but 2.6.28.13 gives me a very similar error to above (device names are different, of course).

I'm not as savvy with this stuff as you, how did you resolve the problem?

Thanks!

---

### Post by Epistaxis on 2009-09-23
> **ohnoezitasploded said:**
> I'm also having this problem after an update.  2.6.28.11 boots up fine but 2.6.28.13 gives me a very similar error to above (device names are different, of course).

I'm not as savvy with this stuff as you, how did you resolve the problem?

Thanks!

I haven't resolved the problem. I am sure there is a simple workaround, but no one with the necessary expertise has bothered to answer. So I just type "dmraid -ay; exit" in the BusyBox every time I boot, and try not to boot very often.

---

### Post by ohnoezitasploded on 2009-09-23
I got mine working again.  I tried a bunch of different stuff, including:
--replacing the (hd0,4) options in grub menu.lst with UUID references

--rebuilding initramfs as outlined in post #8 of this thread:
[https://bugs.launchpad.net/ubuntu/+source/devmapper/+bug/358654](https://bugs.launchpad.net/ubuntu/+source/devmapper/+bug/358654)

But I think what finally did it was doing a 'sudo update-grub'

I don't really know what the f@ck I did, to be honest, I just tried stuff from threads with similar error messages to mine until I found something that worked.  It seems like Ubuntu error messages can be caused by two or three different things each, and that makes troubleshooting them very difficult and time consuming, imho.

---

### Post by Epistaxis on 2009-10-20
> **ohnoezitasploded said:**
> I got mine working again.  I tried a bunch of different stuff, including:
--replacing the (hd0,4) options in grub menu.lst with UUID references

--rebuilding initramfs as outlined in post #8 of this thread:
[https://bugs.launchpad.net/ubuntu/+source/devmapper/+bug/358654](https://bugs.launchpad.net/ubuntu/+source/devmapper/+bug/358654)

But I think what finally did it was doing a 'sudo update-grub'

I don't really know what the f@ck I did, to be honest, I just tried stuff from threads with similar error messages to mine until I found something that worked.  It seems like Ubuntu error messages can be caused by two or three different things each, and that makes troubleshooting them very difficult and time consuming, imho.

None of these things worked for me. After glancing at the thread you cited, I also tried "sudo aptitude reinstall udev" and "sudo update-initramfs -u -k all", but those did not help either. I'm still stuck typing "dmraid -ay" every time I boot. If you think of anything else you might have tried, I'd be very interested to know.

It would be nice if fakeRAID support "just worked." I thought it did in a previous version. But I'm definitely not going to attempt a clean install anytime soon.

---

### Post by Epistaxis on 2009-11-04
I upgraded to 9.10 and this was fixed. It broke other things, but it solved this problem.

---

### Post by quequotion on 2010-04-06
Getting a problem like this once again, now in Karmic with backported kernel 2.6.32-19....

When I try dmraid -ay at iniramfs I get several:

"ERROR: abc reading /dev/sde to ###long number##"

there are about a dozen of these messages, with abc representing several different things (none of which I've heard of, but I believe they are processes)

and then it says my array is already activated, but none of the volumes were activated. It lists out all the volumes and says each one will not be activated...

---

### Post by skliarie on 2010-12-20
> **Epistaxis said:**
> None of these things worked for me. After glancing at the thread you cited, I also tried "sudo aptitude reinstall udev" and "sudo update-initramfs -u -k all", but those did not help either. I'm still stuck typing "dmraid -ay" every time I boot. If you think of anything else you might have tried, I'd be very interested to know.

It would be nice if fakeRAID support "just worked." I thought it did in a previous version. But I'm definitely not going to attempt a clean install anytime soon.

This might happen if the disks already have foreign RAID signature that either dmraid on Intel driver take into account:
[http://skliarie.blogspot.com/2010/12/buggy-intel-raid.html](http://skliarie.blogspot.com/2010/12/buggy-intel-raid.html)

---

### Post by sheph on 2011-01-08
This is kind of a hack, but it works for now, and it's certainly better than having to manually type dmraid -ay everytime (especially for those who do remote admin).  

Note that this will only work if your raid is not your system drive.  Mine is a repository for virtual images.

I edited /etc/fstab and added the noauto option like this...
```
/dev/mapper/isw_efjbicbga_R01           /kvmimg         ntfs    relatime,noauto 0       0
```

Then I added the following lines to /etc/rc.local ....
```

dmraid -ay
mount /kvmimg

```

Obviously you will want to replace /kvmimg with whatever you're trying to mount.

I tried update-initramfs and update-grub.  Neither one provided joy.  Seems like everytime I patch the kernel I have this issue.  If anyone has a better way to fix this I'd sure like to hear it.

---

### Post by garnettxd on 2012-11-17
> **sheph said:**
> This is kind of a hack, but it works for now, and it's certainly better than having to manually type dmraid -ay everytime (especially for those who do remote admin).  

Note that this will only work if your raid is not your system drive.  Mine is a repository for virtual images.

I edited /etc/fstab and added the noauto option like this...
```
/dev/mapper/isw_efjbicbga_R01           /kvmimg         ntfs    relatime,noauto 0       0
```

Then I added the following lines to /etc/rc.local ....
```

dmraid -ay
mount /kvmimg

```

Obviously you will want to replace /kvmimg with whatever you're trying to mount.

I tried update-initramfs and update-grub.  Neither one provided joy.  Seems like everytime I patch the kernel I have this issue.  If anyone has a better way to fix this I'd sure like to hear it.

This is nice work around. For raid drive shared by both linux and windows this is all I want. I don't have to digg into 'dmraid raid 0+1 fakeraid no automount' any more
Thank you so much

---

