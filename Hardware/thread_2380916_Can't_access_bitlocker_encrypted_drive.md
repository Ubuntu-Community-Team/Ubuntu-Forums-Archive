---
title: "Can't access bitlocker encrypted drive"
date: 2017-12-23
forum: Hardware
---

### Post by murbina on 2017-12-23
So, my girlfriend's windows laptop died, the screen doesn't even turn on.  It's still under warranty, so I don't want to do anything that might void that.  But, we are trying to recover her files and delete anything sensitive before sending it back to them for repair.  The drive is an SSD, when I plug it in to my Ubuntu machine it auto-mounts three different partitions, but not the one which has the user data.  I can see the partition with GParted, it is a bitlocker encrypted volume.  I followed the instructions here:

[https://askubuntu.com/questions/617950/use-windows-bitlocker-encrypted-drive-on-ubuntu-14-04-lts](https://askubuntu.com/questions/617950/use-windows-bitlocker-encrypted-drive-on-ubuntu-14-04-lts)

That worked great, until I tried to mount, and I got the following error:

Sat Dec 23 13:51:28 2017 [CRITICAL] None of the provided decryption mean is decrypting the keys. Abort.
Sat Dec 23 13:51:28 2017 [CRITICAL] Unable to grab VMK or FVEK. Abort.

And that is where I hit a dead end.  Some googling tells me that this error might be due to the drive using something called "TPM" which is not supported by dislocker.

Does anyone have any ideas?  If dislocker doesn't support it, are there any other alternate means to get access?

---

### Post by kurt18947 on 2017-12-23
I'm pretty much clueless when it comes to current Windows stuff so take this for what it's worth. The only TPM I've ever heard of is "Trusted Platform Module". You might google that term and see where it takes you.

Edit: I reread your post and see you've googled TPM. I wonder if you'll need a working Windows install with the proper drivers in order to decrypt the bitlocker partition.

---

### Post by ian-weisser on 2017-12-23
The 'dislocker' application is in the Ubuntu repositories

```
Description: read/write encrypted BitLocker volumes
 Dislocker has been designed to read BitLocker encrypted partitions under
 a Linux system. The driver used to read volumes encrypted in Windows system
 versions of the Vista to 10 and BitLocker-To-Go encrypted partitions,that's
 USB/FAT32 partitions.
 .
 The software works with driver composed of a library, with multiple binaries
 using this library. Decrypting the partition, you have to give it a mount
 point where, once keys are decrypted, a file named dislocker-file appears.
 This file is a virtual NTFS partition, so you can mount it as any NTFS
 partition and then read from or write to it. Writing to the NTFS virtual
 file will change the underlying BitLocker partition content.
 .
 This tool is useful in cryptography managing and forensics investigations.
```

---

### Post by murbina on 2017-12-25
Well, I think I figured out what was going on, but it just means I'm stuck.  I think the bitlocker drive is encrypted using a 48 digit key that is hard-coded on the (non-functioning) motherboard.  The drive can only be decrypted using this key (not the user password).  Of course we don't have it.  So, I guess we are out of luck.  Hopefully the repair will actually fix the motherboard, rather than replace it, but that seems unlikely.  The data may be gone forever.

---

### Post by kurt18947 on 2017-12-25
I hope there are unencrypted backups of any important data. Surely your situation is not unique. I wonder what the Microsoft solution is? Restore from backup?

---

