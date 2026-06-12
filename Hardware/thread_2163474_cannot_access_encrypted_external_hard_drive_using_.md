---
title: "cannot access encrypted external hard drive using luks"
date: 2013-07-18
forum: Hardware
---

### Post by brucezepplin on 2013-07-18
Hi, I have been given an encrpyted hard drive with a password to unencrypt. I am, and have been advised to use LUKS to do this. when I try

```
sudo cryptsetup luksOpen /dev/hd1 encrypted_disk
```

I get the following:

```
Cannot open device /dev/hd1 for read access only. 
```

Looking at the permissions it says "I am not the owner so cannot change the permissions"

I have tried chown to aqcuire ownership but this hasn't worked. 

any ideas?

---

