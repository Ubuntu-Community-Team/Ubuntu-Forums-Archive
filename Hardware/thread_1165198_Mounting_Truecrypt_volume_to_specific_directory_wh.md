---
title: "Mounting Truecrypt volume to specific directory when using many volumes (script)"
date: 2009-05-20
forum: Hardware
---

### Post by starsheeep on 2009-05-20
I use external hard drives that have partitions encrypted with Truecrypt, because they are external, volume path can change from time to time and Truecrypt partitions don't support UUID, so distinguishing each drive and mounting it to a specific folder is a problem.

Here is a script that solved this for me.

Instructions:
Change the variables before using it and if you don't use a keyfile leave the keyfile variable blank.

Open a terminal and type
```
ls -l /dev/disk/by-id
```
write down the id of your hard drive to the volume_id variable in the script
EXAMPLE:
```
lrwxrwxrwx 1 root root 10 2009-05-20 18:28 ieee1394-0090a91f6dde11ae:0:0-part1 -> ../../sdh1
```
write down ieee1394-0090a91f6dde11ae:0:0-part1

```
#!/bin/bash
keyfile=~/Documents/Christophers_TrueCrypt_Keyfiles.txt
where_to_mount=~/MBVideo
volume_id=ieee1394-0090a91f6dde11ae:0:0-part1

vol=`ls -l /dev/disk/by-id | grep $volume_id | cut -d / -f 3`

if [ "$vol" = "" ]; then
unset -v keyfile
unset -v where_to_mount
unset -v volume_id
echo "Volume not present"
else
vol_path="/dev/${vol}"
truecrypt -t $vol_path -k $keyfile $where_to_mount
unset -v keyfile
unset -v where_to_mount
unset -v volume_id
fi
```

---

