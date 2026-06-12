---
title: "RAID without superblock"
date: 2008-08-31
forum: General Help
---

### Post by valadil on 2008-08-31
Hi.  My raid is failing.  I'd rather not lose any data, but I'm all out of ideas and nothing on google has helped so far.

I have a raid5 array on my amd64.  It has 4 sata disks.  The raid will assemble, but not mount.  Here's some command output (which may be slightly paraphrased as I'm on another machine):

```

root@box: mount /dev/md0
VFS: Can't find ext3 filesystem on dev md0
mount: wrong fs type, bad option, bad superblock on dev md0, missing codepage or helper program, or other error.  In some cases useful info is found in syslog - try dmesg | tail or so

```

```

root@box: fsck /dev/md0
fsck.ext3: Superblock invalid, trying backup blocks...
fsck.ext3: Bad magic number in super-block while trying to open /dev/md0
...

```

It suggested trying an alternate superblock, so I tried the one it suggested:
```

root@box: fsck -b 8193 /dev/md0
fsck.ext3: Device or resource busy while trying to open /dev/md0
Filesystem mounted or opened exclusively by another program?

```

No idea if that's normal on a raid.  I did mke2fs -n to find the other backup superblocks.  They all gave the previous message.

mdstat looks normal:
```

root@box: cat /proc/mdstat
...
md0: active raid5 sda[0] sdb1[3] sdd1[2] sdc1[1]
     1172125208 blocks level 5, 64k chunk, algorithm 2 [4/4] [UUUU]
...

```

I tried stopping the device and doing --create on it again.  The netterwebs told me it would rebuild the superblocks.  Here's some output done after that point.

```

root@box: mdadm-Q --detail /dev/md0
/dev/md0:
  Version: 00.90.03
  Creation Time: Sun Aug 31 10:04:10 2008
  Raid level: raid5
  Array size: 1172126208 (1117GB 1200GB)
  Use Dev Size: 390708736 (372GB 400GB)
  Raid devices: 4
  Total devices: 4
  Preferred minor: 0
  Persistence: Superblock is persistent

  Update time: Sun Aug 31 18:16:07 2008
  State: clean
  Active devices: 4
  Working devices: 4
  Failed devices: 0
  Spare devices: 0

  Layout: left-symmetric
  Chunk size: 64k

  UUID: I'm not typing all that...
  Events: 0.6

  Number    Major   Minor   Raiddevices  State
  0         8       0       0            active sync /dev/sda
  1         8       33      1            active sync /dev/sdc1
  2         8       49      2            active sync /dev/sdd1
  3         8       17      3            active sync /dev/sdb1

```

Querying individual drives gives similar results.  Finally...

```

root@box: mdadm --examine /dev/md0
mdadm: No md superblock detected on /dev/md0

```

In retrospect I should have piped all that into text files and scp'ed it to my other machine.  My carpal tunnels would thank me.

Anyway, part of what I'm not getting is if this is an ext3 error or a raid error.  I'm inclined to think that it's ext3, except that --examine tells me there's no md superblock.  Is an md superblock the same as a regular superblock?  Either way, what can I do about it?

---

### Post by valadil on 2008-09-01
Help us shameless self-bump, you are our only hope.

---

### Post by valadil on 2008-09-01
Tried doing mdadm --assemble --update-resync.  That caused sdb1 to fail.  I guess the drive was failing before, but mdadm hadn't noticed.

This is my last self bump for this thread.  If I can't figure it out by the time the RMA replacement arrives I'll give up and reformat.  Le sigh.

---

### Post by fjgaude on 2008-09-02
Here's my only suggestion: delete the **/etc/mdadm/mdadm.conf** file. Then uninstall **mdadm**.

Reboot.

Re-install mdadm. Then run this command:

```
sudo mdadm --assemble --scan
```

Just like that. A new .conf file will be created and the array should be back up ready to be mounted, etc.

---

### Post by valadil on 2008-09-02
fjgaude,

I tried that and took it one step further.  I booted off the live cd and tried to assemble.  I need to use --force to get it to start, but the raid does assemble.  Still can't mount it and I'm getting the same errors before from fsck:

```

root@ubuntu:/# fsck /dev/md0 
fsck 1.40.8 (13-Mar-2008)
e2fsck 1.40.8 (13-Mar-2008)
fsck.ext2: Superblock invalid, trying backup blocks...
fsck.ext2: Bad magic number in super-block while trying to open /dev/md0

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

```

and 

```

root@ubuntu:/# fsck -b 8193 /dev/md0 
fsck 1.40.8 (13-Mar-2008)
e2fsck 1.40.8 (13-Mar-2008)
fsck.ext2: Device or resource busy while trying to open /dev/md0
Filesystem mounted or opened exclusively by another program?

```

I was hoping the LiveCD would fix the device/resource busy error.  That doesn't seem like the sort of error I'd get from using the wrong superblock, but I haven't tried before so I don't know.

I'm *this* close to running "for b in `seq $TOTAL_BLOCKS_ON_DISK` ; do fsck -b $b ; done".  I know it could ruin data, but I'm not seeing a lot of other options here.

---

### Post by valadil on 2008-09-02
On the off chance that I was creating/assembling the raid out of order I tried creating and mounting it in each possible order of disks.  Surprisingly, 5 of the permutations mounted.  Unsurprisingly none of them had any useful data.  Each one was 24gb (the original raid was 1.1tb) and had 9.4-10gb used up.

---

### Post by fjgaude on 2008-09-03
For one thing, the create and build commands in **mdadm** will kill on the data in the array. The assemble will not.

I trust you never ever used the fsck command on a mounted array or even a drive of the array?

---

### Post by valadil on 2008-09-03
Nope, never fscked anything mounted or the individual raid drives.

I'd read that create was smart about not destroying data if it looked like a drive could be part of a RAID.  It seemed like a reasonable way to rebuild the raid superblocks.  I'm not expecting to get the data back at this point, so desperate ideas that could work but may destroy data don't seem so bad anymore.

---

### Post by megadream20 on 2008-09-03
Free sites with weekly updated movies and pics:[**** team five](http://www.fuckteamfiveblog.com/),[big tits round asses](http://www.bigtits-round-asses.com/),[*** parade](http://www.assparadediary.com/),[milf lessons](http://www.milflessons69.com/),[Teen Slut Bus](http://www.paysitespy.com/teen-slut-bus/).

---

### Post by don_xvi on 2008-09-14
Hey, I think I can help here, finally !
I have a similar set of error messages when there are system problems, so I poked through my old commands in terminal and here's what I found:
```
sudo mdadm -Af /dev/md0 /dev/1TB_VG/pseudo_1TB /dev/sda1 /dev/sdd1
```
(obviously, those last 3 arguments are the names of my individual drives)
After that, I was able to use
```
sudo mount -a
```

and the my /dev/md0 was back !

P.S.- I just did this tonight (I came here searching for what to do once again) as I had a power outage over the weekend that made my RAID not re-mount.  I wish all this stuff worked all by itself.

---

### Post by fjgaude on 2008-09-15
Seems there is a bug in mdadm v2.6.3 and an update fixes it. You might wish to look at this link:

[http://ph.ubuntuforums.com/showpost.php?p=5338861&postcount=6](http://ph.ubuntuforums.com/showpost.php?p=5338861&postcount=6)

Also 2.6.7 is out:

[http://packages.debian.org/sid/i386/mdadm/download](http://packages.debian.org/sid/i386/mdadm/download)

You might be able to save your data... let us know how things come along.

---

