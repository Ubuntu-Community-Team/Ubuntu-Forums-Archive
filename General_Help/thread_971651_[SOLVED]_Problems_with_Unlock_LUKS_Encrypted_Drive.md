---
title: "[SOLVED] Problems with Unlock LUKS Encrypted Drives With A Keyfile"
date: 2008-11-05
forum: General Help
---

### Post by hopelessone on 2008-11-05
Hi All,

i recently followed from Step 3 as i already made the keyfile used it to unlock the /home dir (working)
```

```
[http://ubuntuforums.org/showthread.php?t=837416&highlight=Unlock+LUKS+Encrypted+Drives+Keyfile](http://ubuntuforums.org/showthread.php?t=837416&highlight=Unlock+LUKS+Encrypted+Drives+Keyfile)



everything is as said until i try to mount it:

```
some@box:~$ sudo mount -a 
[sudo] password for some: 
mount: special device /dev/mapper/crypt-hdd_2 does not exist

```

crypttab:
```
crypt-hdd_2 /dev/disk/by-uuid/ac212449-9edc-4871-b78d-b059523d2fff /root/keyfile  luks
```

fstab:
```
/dev/mapper/crypt-hdd_2  /mnt/hdd_2     ext3    defaults        0       0
```

what are some steps i can do to find out whats wrong?

Thanks...

p.s.

I can mount it from this:
```
cryptsetup luksOpen /dev/sdb1 crypt-hdd_2
mount /dev/mapper/crypt-hdd_2
```

---

### Post by hyper_ch on 2008-11-05
well

```

sudo mount -a

```

only reloads everything in /etc/fstab. That means when you have a running system and you alter the crypttab, then crypttab will not be affected by the mount -a comment and hence the device mapper is missing. You'd first need to manually create it or reboot.

Have a look at Step VI here for manually mounting: [http://www.howtoforge.com/ubuntu_dm_crypt_luks](http://www.howtoforge.com/ubuntu_dm_crypt_luks)

You should use somethign like this:
```

sudo cryptsetup luksOpen /dev/DEVICE MAPPERNAME --key-file /path/to/key

```

---

### Post by hopelessone on 2008-11-05
wow hyper_ch thanks...!! I'll reboot n see

p.s. do you ever sleep?

---

### Post by hyper_ch on 2008-11-05
Sure I do ;) but as we are in different timezones it may not appear to you :)

---

### Post by hopelessone on 2008-11-05
is this right for a manual unlock before i reboot:

```
some@box:~$ sudo cryptsetup luksOpen /dev/sdb1 /dev/mapper/crypt-hdd_2 --key-file /root/keyfile
key slot 1 unlocked.
Command failed: dm_task_set_name: Device /dev/mapper/crypt-hdd_2 not found
some@box:~$ 

```

thanks..

---

### Post by hyper_ch on 2008-11-05
what's the output of
```

ls -al /dev/mapper

```

---

### Post by hopelessone on 2008-11-05
```
some@box:~$ ls -al /dev/mapper
total 0
drwxr-xr-x  2 root root     140 2008-11-05 21:21 .
drwxr-xr-x 15 root root   14280 2008-11-05 08:48 ..
crw-rw----  1 root root  10, 60 2008-11-05 01:25 control
brw-rw----  1 root disk 254,  3 2008-11-05 01:36 crypt-hdd_1
brw-rw----  1 root disk 254,  2 2008-11-05 01:26 cswap
brw-rw----  1 root disk 254,  0 2008-11-05 01:26 sda3_crypt
brw-rw----  1 root disk 254,  1 2008-11-05 01:26 sda4_crypt
some@box:~$ 

```
]
try again from step 3?

---

### Post by hyper_ch on 2008-11-05
what happens if you use another mapper name:

```

sudo cryptsetup luksOpen /dev/sdb1 /dev/mapper/hdd2 --key-file /root/keyfile

```

---

### Post by hopelessone on 2008-11-05
```
some@box:~$ sudo cryptsetup luksOpen /dev/sdb1 /dev/mapper/hdd2 --key-file /root/keyfile
key slot 1 unlocked.
Command failed: dm_task_set_name: Device /dev/mapper/hdd2 not found
some@box:~$ 

```

---

### Post by hopelessone on 2008-11-05
you know what i think i did this a while ago:

```
sudo chown -R some:some /dev/mapper/crypt-hdd_3
```

to create folders...was that right?

---

### Post by hyper_ch on 2008-11-05
no clue what that means. do you use LVM?

---

### Post by hyper_ch on 2008-11-05
> **hopelessone said:**
> you know what i think i did this a while ago:

```
sudo chown -R some:some /dev/mapper/crypt-hdd_3
```

to create folders...was that right?

Not really, but it has no effect.... /dev/mapper is only temporary mapping to devices... they aren't perpetuated if you reboot.

---

### Post by hopelessone on 2008-11-05
ok thanks..

i followed this for the HDD's:

[http://www.g-loaded.eu/2005/11/10/encrypt-devices-using-dm-crypt-and-luks/](http://www.g-loaded.eu/2005/11/10/encrypt-devices-using-dm-crypt-and-luks/)

woah..... LVM? LUKS...?

---

### Post by hyper_ch on 2008-11-05
stupid me!!! run:

```

sudo cryptsetup luksOpen /dev/sdb1 crypt-hdd_2 --key-file /root/keyfile

```

---

### Post by hopelessone on 2008-11-05
```
some@box:~$ sudo cryptsetup luksOpen /dev/sdb1 crypt-hdd_2 --key-file /root/keyfile
key slot 1 unlocked.
Command successful.
some@box:~$ 

```

I await you next holy command Oh hyper one..

p.s. swiss are never stupid...just the rest of us..

---

### Post by hopelessone on 2008-11-05
good news...it appeared:
```
some@box:~$ ls -al /dev/mapper
total 0
drwxr-xr-x  2 root root     160 2008-11-05 21:43 .
drwxr-xr-x 15 root root   14280 2008-11-05 21:43 ..
crw-rw----  1 root root  10, 60 2008-11-05 01:25 control
brw-rw----  1 root disk 254,  3 2008-11-05 01:36 crypt-hdd_1
brw-rw----  1 root disk 254,  4 2008-11-05 21:43 crypt-hdd_2
brw-rw----  1 root disk 254,  2 2008-11-05 01:26 cswap
brw-rw----  1 root disk 254,  0 2008-11-05 01:26 sda3_crypt
brw-rw----  1 root disk 254,  1 2008-11-05 01:26 sda4_crypt
some@box:~$ 
vv
```

```
sudo mount -a
```

whooooo!!!!!! it appeared...

gettin ready to reboot...

---

### Post by hyper_ch on 2008-11-05
:) just make sure the UUID in the /etc/crypttab file is also correct. If so, then it should work.

---

### Post by hopelessone on 2008-11-05
ok rebooted and none are mounted:

tried:

```
some@box:~$ sudo mount -a
[sudo] password for some: 
mount: special device /dev/mapper/crypt-hdd_1 does not exist
mount: special device /dev/mapper/crypt-hdd_2 does not exist
mount: special device /dev/mapper/crypt-hdd_3 does not exist
some@box:~$ v
```

---

### Post by hopelessone on 2008-11-05
if i do the following;

```
sudo cryptsetup luksOpen /dev/sda1 crypt-hdd_1 --key-file /root/keyfile
sudo cryptsetup luksOpen /dev/sdb1 crypt-hdd_2 --key-file /root/keyfile
sudo cryptsetup luksOpen /dev/sdd1 crypt-hdd_3 --key-file /root/keyfile
```

no probs...

what am i doing wrong to automate this?

---

### Post by hyper_ch on 2008-11-05
What does your /etc/crypttab file look like?

---

### Post by hyper_ch on 2008-11-05
I assume it works now?

---

### Post by hopelessone on 2008-11-05
Sorry went to sleep...

here is the crypttab:
```
sda3_crypt /dev/disk/by-uuid/1fc9c758-5b2a-41cf-9781-31a9f6ca7ff4 none luks
sda4_crypt /dev/disk/by-uuid/64bf6482-30e9-416a-8afb-4aa0d680998c /root/keyfile  luks

crypt-hdd_1 /dev/disk/by-uuid/ac212449-9edc-4871-b78d-b059523d2fff /root/keyfile  luks
crypt-hdd_2 /dev/disk/by-uuid/b8fa5c09-2e10-492a-a934-8865b94be5cb /root/keyfile  luks
crypt-hdd_3 /dev/disk/by-uuid/a7075aa9-4b84-4057-aac1-d446f83ab1fd /root/keyfile  luks

cswap /dev/sdc2  /dev/urandom	swap
```

gotta go to work back later..

---

### Post by hyper_ch on 2008-11-06
and your fstab and
```

ls -al /dev/disk/by-uuid

```
?

---

### Post by hopelessone on 2008-11-06
ok

fstab:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/mapper/sda3_crypt /               ext3    errors=remount-ro 0       1
# /dev/sda1
UUID=51be67d8-a120-4645-9509-faebaf9b0087 /boot           ext3    relatime        0       2
/dev/mapper/sda4_crypt /home           ext3    defaults        0       2
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/mapper/cswap none	swap	sw	0	0

/dev/mapper/crypt-hdd_1  /mnt/hdd_1     ext3    defaults        0       0
/dev/mapper/crypt-hdd_2  /mnt/hdd_2     ext3    defaults        0       0
/dev/mapper/crypt-hdd_3  /mnt/hdd_3     ext3    defaults        0       0

none /proc/bus/usb usbfs devgid=46,devmode=664 0 0
```

```
some@box:~$ ls -al /dev/disk/by-uuid
total 0
drwxr-xr-x 2 root root 260 2008-11-06 08:49 .
drwxr-xr-x 5 root root 100 2008-11-06 08:46 ..
lrwxrwxrwx 1 root root  24 2008-11-06 08:49 16c3750e-9fe1-4b48-85ff-a06862ee1dcd -> ../../mapper/crypt-hdd_3
lrwxrwxrwx 1 root root  10 2008-11-06 08:46 1fc9c758-5b2a-41cf-9781-31a9f6ca7ff4 -> ../../sdc3
lrwxrwxrwx 1 root root  10 2008-11-06 08:46 2664ccc8-518e-4ebd-a7ff-1f652831b451 -> ../../sdd1
lrwxrwxrwx 1 root root  10 2008-11-06 08:46 51be67d8-a120-4645-9509-faebaf9b0087 -> ../../sdc1
lrwxrwxrwx 1 root root  24 2008-11-06 08:49 5b52b851-e4bd-4edd-b41c-c0b142fa2d73 -> ../../mapper/crypt-hdd_1
lrwxrwxrwx 1 root root  10 2008-11-06 08:46 6029d3eb-50ba-46f0-8e1f-4b5cdc09b18c -> ../../sda1
lrwxrwxrwx 1 root root  10 2008-11-06 08:46 64bf6482-30e9-416a-8afb-4aa0d680998c -> ../../sdc4
lrwxrwxrwx 1 root root  23 2008-11-06 08:47 84768477-456c-488e-b364-6eec57b4961d -> ../../mapper/sda3_crypt
lrwxrwxrwx 1 root root  24 2008-11-06 08:49 c626eb47-7211-4413-8955-317467138c01 -> ../../mapper/crypt-hdd_2
lrwxrwxrwx 1 root root  23 2008-11-06 08:47 d5957464-3a5e-4067-8dec-ccc844c7a097 -> ../../mapper/sda4_crypt
lrwxrwxrwx 1 root root  10 2008-11-06 08:46 f57f3906-1089-47f3-8c3f-89fe2ce82434 -> ../../sdb1
some@box:~$ 

```

---

### Post by hopelessone on 2008-11-06
weird?...when i do:

```
some@box:~$ blkid
/dev/sda1: UUID="ac212449-9edc-4871-b78d-b059523d2fff" TYPE="ext3" SEC_TYPE="ext2" 
/dev/mapper/sda3_crypt: UUID="84768477-456c-488e-b364-6eec57b4961d" TYPE="ext3" 
/dev/mapper/sda4_crypt: UUID="d5957464-3a5e-4067-8dec-ccc844c7a097" TYPE="ext3" 
/dev/sdb1: UUID="b8fa5c09-2e10-492a-a934-8865b94be5cb" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc1: UUID="51be67d8-a120-4645-9509-faebaf9b0087" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc3: UUID="1fc9c758-5b2a-41cf-9781-31a9f6ca7ff4" TYPE="crypt_LUKS" 
/dev/sdc4: UUID="64bf6482-30e9-416a-8afb-4aa0d680998c" TYPE="crypt_LUKS" 
/dev/sdd1: UUID="a7075aa9-4b84-4057-aac1-d446f83ab1fd" SEC_TYPE="ext2" TYPE="ext3" 
some@box:~$ 
```

i used that UUID...hmmmm

---

### Post by hopelessone on 2008-11-06
i have no idea why blkid shows a different UUID than the one you gave me...

I changed all the UUID's and it works...

Thank you, Thank you, Thank you, Thank you, Thank you, Thank you, Thank you, Thank you, Thank you, Thank you, Thank you, Thank you, Thank you, Thank you, Thank you, Thank you, Thank you, Thank you, Thank you.

---

### Post by hyper_ch on 2008-11-06
enjoy :)

---

