---
title: "Problem burning DVD"
date: 2008-07-14
forum: Hardware
---

### Post by kag on 2008-07-14
Hi,
Up until today, I never had any problem with my DVD burner. When I try to burn an .ISO image (right-click | Write to disc), it goes all the way up to 100% (and I can see by looking at the disk that data was really burned), but I always get an "Unhandled error" before it finishes.

I tried with two different brand of disk (tried twice with a DVD-R and once with a DVD+R) and both Maximum speed and 2.0x. Same result.

Out of curiosity, I placed one of those DVD in my drive and got logged out of my session almost instantly.

When I go in System | Administration | System Log, and I select "messages", this line:
> Jul 14 18:01:04 strider kernel: [ 3524.346305] cdrom: This disc doesn't have any tracks I recognize!
And also these lines:
> Jul 14 18:08:08 strider kernel: [ 3947.740753] UDF-fs: No VRS found
Jul 14 18:08:08 strider kernel: [ 3947.850129] isofs_fill_super: root inode is not a directory. Corrupted media?

But they don't give much information about the error itself. I'm not sure where else I should look.

Thanks!

---

### Post by stchman on 2008-07-14
What program are you using?  I personally use K3b for burning DVDs.

```

```

Brasero is decent burning program as well.

Hardy install:
```
sudo apt-get -y install k3b libk3b2-extracodecs
```

Also when you burn a .iso file K3b auto computes the MD5 checksum.  If you can verify the checksum with the iso originator.

---

### Post by kag on 2008-07-14
Like I said, I was using the built-in burning software (right-click on the .ISO file and "Write to disc").

I just tried with Brasero and the burning process didn't return any problem. When the DVD was ejected, Brasero asked to put it back in to check the checksum, so I did and got the following message:
> Cannot mount volume
Invalid mount option when attempting to mount the volume.

When I check back in System Log, I have the exact same errors as in the original post.

---

### Post by ppoteete on 2008-08-20
I'm having a similar problem with a cdrom iso.  My new ISO's burn and mount fine, but my old redhat 9 iso returns an error.


Mounting as sudo root:

root@netfoo:/home/data/ISO/redhat# mount -o loop -t iso9660 redhat9-2.iso /mnt/cdrom/
mount: wrong fs type, bad option, bad superblock on /dev/loop1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

root@netfoo:/home/data/ISO/redhat# dmesg | tail
[135278.820484] UDF-fs: No VRS found
[135278.840583] ISO 9660 Extensions: Microsoft Joliet Level 3
[135278.841391] ISOFS: Interleaved files not (yet) supported.
[135278.841394] ISOFS: File unit size != 0 for ISO file (1856).
[135278.841397] ISOFS: changing to secondary root
[135278.863376] isofs_fill_super: root inode is not a directory. Corrupted media?
[135469.419153] ISO 9660 Extensions: Microsoft Joliet Level 3
[135469.419184] ISOFS: File unit size != 0 for ISO file (1792).
[135469.419187] ISOFS: changing to secondary root
[135469.419201] isofs_fill_super: root inode is not a directory. Corrupted media?

All of my newer (1-2 years old) iso's work fine.  I can even burn the iso to a CDROM, but I still can't mount the cdrom.

---

