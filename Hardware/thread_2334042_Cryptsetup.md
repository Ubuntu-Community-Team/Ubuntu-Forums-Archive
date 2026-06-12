---
title: "Cryptsetup"
date: 2016-08-15
forum: Hardware
---

### Post by shane_faulkinbury2 on 2016-08-15
I'm trying to format my flash drives to use a password to get into them.  I installed cryptsetup in my Terminal and opened Disk Utility.  I then unmounted my flash drive and then chose to format it to NTFS, but I do not see Encrypt underlying device.  Will it not work formatting to NTFS?  Should I use another format such as extr4?  I did setup another flash drive on my Ubuntu Mate 16.04 laptop and used NTFS, but it will not work on my desktop using Ubuntu 16.04.:confused:

---

### Post by howefield on 2016-08-16
You can't encrypt your drive with NTFS, so choose something else.

Were you hoping to use your encrypted flash drive also in Windows ?

---

### Post by shane_faulkinbury2 on 2016-08-16
Thanks for the information!

---

### Post by shane_faulkinbury2 on 2016-08-23
I switched to Ext4 and the Type:  Encrypted, compatible with Linux systems (LUKS and Ext4) never shows up.  So I want to start over, reinstall the cryptsetup and start over.  So how do I uninstall it?  I know it's sudo apt-get remove something, but not sure what it is.  Is it sudo apt-get remove crpytsetup or something else?

---

### Post by howefield on 2016-08-24
> **shane_faulkinbury2 said:**
>  So how do I uninstall it?  I know it's sudo apt-get remove something, but not sure what it is.  Is it sudo apt-get remove crpytsetup or something else?

Remove the package cryptsetup ? Yes, this should do it..

```
sudo apt-get purge cryptsetup
```

Sounds like overkill but it won't harm anything by reinstalling.

---

