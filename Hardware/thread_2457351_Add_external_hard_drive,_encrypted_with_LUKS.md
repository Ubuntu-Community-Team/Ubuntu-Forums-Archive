---
title: "Add external hard drive, encrypted with LUKS"
date: 2021-01-31
forum: Hardware
---

### Post by uacnt83982803 on 2021-01-31
I'm going to add an external hard drive for increased storage.  I want to encrypt it, so that if it is stolen no one will have access to it.

As a test, I tried using a USB flash drive and encrypting it.  But the system would not mount it.  I tried unlocking it using cryptLock (or whatever the actual name is, can't remember) but was still unable to mount it.  

What is the right way to do this, so that my external drive will be encrypted but will mount whenever the system restarts?  Thanks.

---

### Post by TheFu on 2021-01-31
If the system can automatically mount the encrypted storage without waiting for human input, then why bother with any encryption?  Sorta defeats the reason to have it encrypted.  I struggled with this issue too, BTW.

However, some people will place a USB flash drive into the system which contains a LUKS key file which can be referenced at mount time.  I've never done this.  I do encrypt my laptops using a challenge-response code with a yubikey. Without one of the 2 authorized yubikeys and the correct response, the system storage will not unlock.  I do have a backup passphrase - think it is 65 random characters. It could be really hard to type that in correctly. LUKS has 8 "slots" to provide access codes, so 8 different unlock entries are possible. Just need to be selective about which slot gets stored when adding other access codes.

Anyways, [https://www.linuxquestions.org/questions/linux-security-4/unlock-luks-encrypted-root-system-with-keyfile-on-usb-device-4175599442/](https://www.linuxquestions.org/questions/linux-security-4/unlock-luks-encrypted-root-system-with-keyfile-on-usb-device-4175599442/) is for a USB keyfile to unlock LUKS.  Just don't leave the flash drive in the system all the time. ;)

---

### Post by uacnt83982803 on 2021-01-31
TheFu, thanks, you are the man.  Yes, for sure I really don't want it to mount the drive without me needing to enter the encryption password.

Can I do this: when my PC restarts, I am prompted to enter the password to unlock my primary hard drive (it is also encrypted using LUKS).   Is it possible to have the system also prompt me to enter the password to unlock the external drive, at the same time (or after startup)?

Or do I need to plan to manually mount the external drive and enter the unlock password at that time?

---

