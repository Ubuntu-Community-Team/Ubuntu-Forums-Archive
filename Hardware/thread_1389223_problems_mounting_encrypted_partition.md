---
title: "problems mounting encrypted partition"
date: 2010-01-24
forum: Hardware
---

### Post by nicolasdiogo on 2010-01-24
hi folks,

i have got myself in a bit of a situation here.
my encrypted home partition can no longer being mounted.

i have used **cryptsetup** to encrypt the contents of my home partition which used to be mounted aumatically by using instruction that i have found on lars website:

[http://blog.larsstrand.org/article.php?story=EncryptedSwapAndHomeUbuntu](http://blog.larsstrand.org/article.php?story=EncryptedSwapAndHomeUbuntu)

while troubleshooting the problem i tried mounting the partition manually and here is the output:

```

root@laptopPC:~# cryptsetup luksOpen /dev/sda2 myHome
Enter LUKS passphrase: 
key slot 0 unlocked.
Command successful.

root@laptopPC:~# mount -text4 /dev/mapper/myHome myHomeMounted/
mount: wrong fs type, bad option, bad superblock on /dev/mapper/myHome,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

i have found a bug that describes a similar problem which is said to be corrected in Karmic:

[https://bugs.launchpad.net/ubuntu/karmic/+source/cryptsetup/+bug/473615](https://bugs.launchpad.net/ubuntu/karmic/+source/cryptsetup/+bug/473615)

could somebody with experience with cryptsetup help me out here please??

many thanks,

Nicolas

---

### Post by IcarusR on 2010-01-24
> root@laptopPC:~# mount -text4 /dev/mapper/myHome myHomeMounted/


I believe it should be "-t ext4"

```
 mount -t ext4 /dev/mapper/myHome myHomeMounted/

```

What version of Ubuntu ?

---

### Post by nicolasdiogo on 2010-01-25
thanks IcarusR,

but that did not help.
i still get the same error message.

Nicolas

---

### Post by nicolasdiogo on 2010-01-25
hi,

just bumping to see if anyone could help..

thanks

---

