---
title: "can't install ecryptfs"
date: 2008-10-02
forum: General Help
---

### Post by helai on 2008-10-02
I try to use ecryptfs,but I got

lenovo@ubuntu:~$ uname -r
2.6.24-21-generic

lenovo@ubuntu:~$ sudo mount -t ecryptfs ~/Private ~/Private

Unable to get the version number of the kernel
module. Please make sure that you have the eCryptfs
kernel module loaded, you have sysfs mounted, and
the sysfs mount point is in /etc/mtab. This is
necessary so that the mount helper knows which 
kernel options are supported.

Make sure that your system is set up to auto-load
your filesystem kernel module on mount.

Enabling passphrase-mode only for now.

Select key type to use for newly created files: 
 1) passphrase
 2) openssl
 3) pkcs11-helper
 4) tspi
Selection: 1
Passphrase: 
Verify Passphrase: 
Select cipher: 
 1) aes: blocksize = 16; min keysize = 16; max keysize = 32 (not loaded)
 2) blowfish: blocksize = 16; min keysize = 16; max keysize = 32 (not loaded)
 3) des3_ede: blocksize = 8; min keysize = 24; max keysize = 24 (not loaded)
 4) twofish: blocksize = 16; min keysize = 16; max keysize = 32 (not loaded)
 5) cast6: blocksize = 16; min keysize = 16; max keysize = 32 (not loaded)
 6) cast5: blocksize = 8; min keysize = 5; max keysize = 16 (not loaded)
Selection [aes]: 
Select key bytes: 
 1) 16
 2) 32
 3) 24
Selection [16]: 
Attempting to mount with the following options:
  ecryptfs_key_bytes=16
  ecryptfs_cipher=aes
  ecryptfs_sig=1f1d353f42d4eea4
WARNING: Based on the contents of [/root/.ecryptfs/sig-cache.txt],
it looks like you have never mounted with this key 
before. This could mean that you have typed your 
passphrase wrong.

Would you like to proceed with the mount (yes/no)? y
Aborting mount.
Error processing sig; rc = [-22]
Error mounting eCryptfs; rc = [-22]; strerr = [Invalid argument]. Check your system logs; visit <http://ecryptfs.sourceforge.net/ecryptfs-faq.html>.

any suggestions are welcome!
helai

---

