---
title: "Can't access Home and bad blocks reported in the partition"
date: 2008-09-21
forum: General Help
---

### Post by Beamvr6 on 2008-09-21
As a matter of routine I restarted Ubuntu after it had been busy overnight and ended up not being able to login.

fsck etc. reports a superblock issue and after reading a lot in the forums mkfs -n /dev/sdb6 gives other superblocks but the couple I tried in fsck -b nnnn /dev/sdb6 all resulted in the "device being mounted or exclusively used by another process" both of which aren't the case to the best of my knowledge.

Some further searches made me launch these 2 commands plus their results:

```
ubuntu@ubuntu:~$ sudo e2fsck -c -c -k -v /dev/sdb6
e2fsck 1.40.8 (13-Mar-2008)
/dev/sdb6: Attempt to read block from filesystem resulted in short read while reading block 1546

/dev/sdb6: Attempt to read block from filesystem resulted in short read reading journal superblock

e2fsck: Attempt to read block from filesystem resulted in short read while checking ext3 journal for /dev/sdb6
ubuntu@ubuntu:~$ sudo badblocks -sv /dev/sdb6
Checking blocks 0 to 32676177
Checking for bad blocks (read-only test): 6144       6144/       32676177
6184       6184/       32676177
6185       6185/       32676177
6186       6186/       32676177
6187       6187/       32676177
6188
6189
6190
6191
6192
6193
6194
6195
6196
6197
6198
6199
6200
6201
6202
6203
6204
6205
6206
6207
6208
6209
6210
6211
6212
6213
6214
6215
6216
6217
6218
6219
6220
6221
6222
6223
6224
6225
6226
6227
6228
6229
6230
6231
done                                
Pass completed, 49 bad blocks found.

```

So obviously there are bad blocks and the HD has to be replaced. But my Home folder is there! Anyway to recover data on it? Or something else to try first?

Physically the partition is on a HD with three other partitions that all are fine. The Linux installation also is on another HD.

TIA

---

### Post by Beamvr6 on 2008-10-14
Bump!

I've been using XP for the past three weeks but really want to fix this and go back to my Ubuntu.

Apart from the issues in the first post it also gives a problem replacing a superblock.

```
ubuntu@ubuntu:~$ sudo dumpe2fs /dev/sdb6 | grep -i superblock
dumpe2fs 1.40.8 (13-Mar-2008)
  Primary superblock at 0, Group descriptors at 1-2
  Backup superblock at 32768, Group descriptors at 32769-32770
  Backup superblock at 98304, Group descriptors at 98305-98306
  Backup superblock at 163840, Group descriptors at 163841-163842
  Backup superblock at 229376, Group descriptors at 229377-229378
  Backup superblock at 294912, Group descriptors at 294913-294914
  Backup superblock at 819200, Group descriptors at 819201-819202
  Backup superblock at 884736, Group descriptors at 884737-884738
  Backup superblock at 1605632, Group descriptors at 1605633-1605634
  Backup superblock at 2654208, Group descriptors at 2654209-2654210
  Backup superblock at 4096000, Group descriptors at 4096001-4096002
  Backup superblock at 7962624, Group descriptors at 7962625-7962626
ubuntu@ubuntu:~$ sudo e2fsck -b 32768 /dev/sdb6
e2fsck 1.40.8 (13-Mar-2008)
e2fsck: Device or resource busy while trying to open /dev/sdb6
Filesystem mounted or opened exclusively by another program?
ubuntu@ubuntu:~$ umount /dev/sdb6
umount: /dev/sdb6 is not mounted (according to mtab)
ubuntu@ubuntu:~$ sudo e2fsck -b 32768 /dev/sdb6
e2fsck 1.40.8 (13-Mar-2008)
e2fsck: Device or resource busy while trying to open /dev/sdb6
Filesystem mounted or opened exclusively by another program?

```

Can somebody give advise please.

---

