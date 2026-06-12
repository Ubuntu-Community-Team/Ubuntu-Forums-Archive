---
title: "RAID 1 mdadm array - partitions failing"
date: 2008-09-08
forum: General Help
---

### Post by jonface on 2008-09-08
I've got two drives setup as raid 1 with two partitions. One for '/' and one for 'swap'.

I don't know why but the drive partitions keep 'failing', normally after a reboot (maybe not). I've got;

/dev/md0 - '/' , made up of sda1 sdb1
/dev/md1 - 'swap', made up of sda2 sdb2

```

cat /prov/mdstat

md1 : active raid1 sda2[0] sdb2[1]
      3951872 blocks [2/2] [UU]
      
md0 : active raid1 sdb1[1]
      191406336 blocks [2/1] [_U]
      
unused devices: <none>


```

Now if it was the drive, surely in the above case, sda should be completely gone? But sometimes md0 will be complete (after I've rebuilt it) and then on the next boot, md1 will be missing a drive. I just don't get it.

The only change I've made to mdadm setup (I followed the instructions [https://help.ubuntu.com/community/Installation/SoftwareRAID]("https://help.ubuntu.com/community/Installation/SoftwareRAID")) is this: 

[http://hightechsorcery.com/2008/08/howto-enable-degraded-software-mdadm-raid-arrays-boot-under-ubuntu]("http://hightechsorcery.com/2008/08/howto-enable-degraded-software-mdadm-raid-arrays-boot-under-ubuntu")


On my last boot sdb1 was missing with sda1 active. I didn't think at the time but now they've swapped over so all the changes I made since then have gone. So now I'm off to swap them back over and leave one unplugged, until someone can explain what's going on.

I can't seem to find a log for mdadm? All I can find is from dmesg,


```

dmesg | grep md
[    0.000000] Kernel command line: root=/dev/md0 ro
[   22.758666] md: linear personality registered for level -1
[   22.763504] md: multipath personality registered for level -4
[   22.768213] md: raid0 personality registered for level 0
[   22.773440] md: raid1 personality registered for level 1
[   23.477676] md: raid6 personality registered for level 6
[   23.477740] md: raid5 personality registered for level 5
[   23.477804] md: raid4 personality registered for level 4
[   23.504893] md: raid10 personality registered for level 10
[   28.195622] md: md0 stopped.
[   28.202864] md: bind<sdb1>
[   28.212716] raid1: raid set md0 active with 1 out of 2 mirrors
[   28.212916] md: md1 stopped.
[   28.241733] md: md1 stopped.
[   28.247255] md: bind<sdb2>
[   28.247519] md: bind<sda2>
[   28.257619] raid1: raid set md1 active with 2 out of 2 mirrors
[   42.342063] Adding 3951864k swap on /dev/md1.  Priority:-1 extents:1 across:3951864k
[   42.725085] EXT3 FS on md0, internal journal

```


Thanks for any help you can provide.

Jon.

---

### Post by jonface on 2008-09-09
And today,

```

jonathan@yserv:~$ cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md1 : active raid1 sda2[0]
      3951872 blocks [2/1] [U_]
      
md0 : active raid1 sda1[0]
      191406336 blocks [2/1] [U_]

```

Also,

```

jonathan@yserv:~$ sudo mdadm -v --assemble --scan
mdadm: looking for devices for further assembly
mdadm: cannot open device /dev/disk/by-uuid/26a9e46f-0ae6-40aa-a2ad-92ecba69b10c: Device or resource busy
mdadm: cannot open device /dev/disk/by-uuid/55808dce-2590-466a-a9d7-6ad72b6a89b3: Device or resource busy
mdadm: /dev/sdb2 is not built for host yserv.
mdadm: /dev/sdb1 is not built for host yserv.
mdadm: no recogniseable superblock on /dev/sdb
mdadm: cannot open device /dev/sda2: Device or resource busy
mdadm: cannot open device /dev/sda1: Device or resource busy
mdadm: cannot open device /dev/sda: Device or resource busy

```

```

lrwxrwxrwx 1 root root   9 2008-09-09 11:35 26a9e46f-0ae6-40aa-a2ad-92ecba69b10c -> ../../md1
lrwxrwxrwx 1 root root   9 2008-09-09 11:35 55808dce-2590-466a-a9d7-6ad72b6a89b3 -> ../../md0

```

```

mdadm.conf

ARRAY /dev/md0 level=raid1 num-devices=2 UUID=e430a0c7:2c20eee3:52db37f0:01884521
ARRAY /dev/md1 level=raid1 num-devices=2 UUID=4e4aa4fd:b6bd58ec:9cade498:5d9a8e0e

```


Hmph just noticed, "HOMEHOST <system>" in mdadm.conf, maybe it should be the hostname of the system instead O_o. We'll see.

EDIT: changed HOMEHOST to yserv, no affect.
EDIT2: changed mdadm.conf, added 'devices=/dev/sdaX,/dev/sdbX1' for each array line. No affect.

EDIT3: Maybe the effects don't happen straight away. I'm rebuilding the array then I'll reboot it a few times.

EDIT4: No joy. Upgraded to mdadm v2.6.7 - 6th June 2008. Rebuilding array, again.

---

### Post by fjgaude on 2008-09-09
The issue may be hardware going bad... can't say for sure.

One thing you might try is one that works most of the time: delete the mdadm.conf file. uninstall mdadm, reboot, then re-install mdadm. Finally run:

```
sudo mdadm --assemble --scan
```

Just like that, nothing more. The mdadm.conf file will be auto-generated correctly, and the two arrays should mount, based on your /etc/fstab file.

---

### Post by jonface on 2008-09-10
OK I've checked the drives with a program from Seagate (they're Seagate drives, heh) and they both passed, short and long tests and SMART.

I'm on the livecd at the min and using smartctl to run a self test on the drives, even though it's most likely the same as the 'long' test from the Seagate program. So far so good. 

Is there any other way to test the drives?

I've also removed mdadm and I'll put it back on once the drive tests have finished.

I really don't think it's the drives as it seems as long as I don't reboot, everything is fine.

Anyway, I'll post back once the tests have finished.

Thanks for your time and help.

---

### Post by jonface on 2008-09-10
EDIT: At bottom.

Both drives passed all the tests, they're working fine.

In the live cd I,
- mounted the array
- chroot on the mount point
- apt-get remove mdadm and removed mdadm.conf.

I then reinstalled mdadm which also did that rebuilt thing of initramfs. Problem is now it hangs at the part where it normally says 'reading files needed to boot' or something like that, just hangs, then drops into the (initramfs) shell. Tried running 'mdadm --assemble --scan' and I get,

```

mdadm: CREATE user root not found
mdadm: CREATE group disk not found
mdadm: No disk found in config file or automatically

```

Now I know it's not the drives/array as they run fine from the live cd, so, what is it? 

I checked that in '/etc/udev/rules.d/85-mdadm.rules' it still read,
```

SUBSYSTEM=="block", ACTION=="add|change", ENV{IDFSTYPE}=="linux_raid*", \
       RUN+="watershed /sbin/mdadm --assemble --scan --run"

```

and it does. I even tried from the live cd (after chrooting) update-initramfs -v -k -c all.

Argh I'm confused. Help please! 

Thanks again.

EDIT1: I remembered seeing an initramfs image ending in .bak, so I changed the initrd line to use this and it booted. I'm just going to swap the images over and leave the damn thing alone. Still doesn't explain why the drives take it in turn to disappear.

---

### Post by jonface on 2008-09-11
ARGH

Ok it won't boot after I thought it was working. The only thing I did was mv the initramfs image ending in .bak (which booted) to overwrite the one which didn't work. The filename doesn't matter does it? There's no harm in just renaming an image? 

I've lost the plot, no idea what to do. Boots into the (initramfs) shell then I try,

```

mdadm --assemble --scan

mdadm: CREATE user root not found
mdadm: CREATE group disk not found
mdadm: No disk found in config file or automatically

```

and now I'm stuck. Like I said, the array works fine with the live cd so lets assume I've messed something up. I don't really want to format and start again as it's not really the answer.

I'll do anything, ideas? I just want it to work :(.

---

### Post by fjgaude on 2008-09-11
I've never tried to do what you are trying... boot off a raid1.

Likely the grub is not on the right drive... you see for mdadm to work the array has to be assembed by md in the kernel, but the kernel is on the raid1... likely you have a race problem or the grub file, memu.lst, is not being pointed to.

Since you have to use the liveCD to do anything, you might study up on grub useage. And use it to place grub on both the drives' MBR.

It would go something like this:

```
#grub
grub> find /boot/grub/stage1
>root (hd0,0)
>setup (hd0)
>quit
```

Then do the same for hd1,0

I'm weak on remembering it all.

Let us know how you are doing.

---

