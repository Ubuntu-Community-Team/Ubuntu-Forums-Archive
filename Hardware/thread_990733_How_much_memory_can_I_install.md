---
title: "How much memory can I install ?"
date: 2008-11-23
forum: Hardware
---

### Post by stans on 2008-11-23
I'm running 8.04 on a P5NSLI... this motherboard can support 16gb but what is the maximum that Ubuntu will recognize ?

I've done some searching and have found references to versions of Ubuntu that are 64 bit that are capable... but which ones ?

How does one determine what is running ? (32 or 64 bit ).

---

### Post by cariboo on 2008-11-23
If you are using the server kernel it will support up to 64Gb. THe 64bit kernel will support up to 16 exabytes of RAM, so  it shouldn't have any probelm with 16Gb.

To find what version you are running in a Applications-->Accessories--Terminal type:

```
uname -a
```

If you are running a 64bit distribution you should see some thing like this:

```
Linux alexis 2.6.27-8-generic #1 SMP Thu Nov 6 17:38:14 UTC 2008 x86_64 GNU/Linux
```

Jim

---

### Post by IanW on 2008-11-23
The important part in cariboo907's post is the _x86_64_ part. If you have 32-bit Ubuntu, then this will read "i386" or "i686"

If you have Ubuntu32, then it's not worth fitting more than 3GB.
If you have Ubuntu64, then you can fit all the memory your motherboard (and wallet) will allow.

---

### Post by stans on 2008-11-23
Thank you both for the reply. 

Linux stan-desktop 2.6.24-21-generic #1 SMP Tue Oct 21 23:43:45 UTC 2008 i686 GNU/Linux


Looks like I am good to go on the memory increase... now to go bargain hunting !

---

### Post by liquid.silver on 2008-11-23
> **stans said:**
> Thank you both for the reply. 

Linux stan-desktop 2.6.24-21-generic #1 SMP Tue Oct 21 23:43:45 UTC 2008 i686 GNU/Linux


Looks like I am good to go on the memory increase... now to go bargain hunting !

You do realise that it a 32-bit version, right? Don't wanna see you waste your money, just making sure...

---

