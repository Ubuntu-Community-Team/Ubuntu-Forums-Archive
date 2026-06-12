---
title: "How do you uninstall drivers on Ubuntu"
date: 2010-08-30
forum: Hardware
---

### Post by garycheng12 on 2010-08-30
Basically, I want to create the perfect system image so that I can restore it on different computers using different hardware. I don't want the system image to be cluttered with useless drivers, so I am looking for a way to search for these automatically installed drivers and uninstall/remove them from the operating system.

Thanks.

Also, I would like to know how to create an encrypted home partition that stores the configuration files of Ubuntu and be able to access this encrypted partition from Windows. 

I want Ubuntu to use NTFS so that I can freely trade files (above 4 GB) with Windows through this encrypted home partition. 

Lastly, I wanted to make sure if NTFS is a safe choice for Ubuntu to be using, because I have heard some issues when Ubuntu deals with NTFS read/write. 

Thanks, guys. Much appreciated, will check this forum first thing in the morning.

---

### Post by Bachstelze on 2010-08-30
> **garycheng12 said:**
> Basically, I want to create the perfect system image so that I can restore it on different computers using different hardware. I don't want the system image to be cluttered with useless drivers, so I am looking for a way to search for these automatically installed drivers and uninstall/remove them from the operating system.

Most drivers are built into the kernel.  If you don't want them, you'll have to build a custom kernel, with the drivers you don't want disabled.

> 
Also, I would like to know how to create an encrypted home partition that stores the configuration files of Ubuntu and be able to access this encrypted partition from Windows. 

TrueCrypt is the only portable filesystem encryption solution I know of. Also, the system configuration files are stored in the /etc directory, that must be on the root filesystem. The /home partition contains only the users' personal settings.

> 
I want Ubuntu to use NTFS so that I can freely trade files (above 4 GB) with Windows through this encrypted home partition. 

It is not possible to use NTFS for the home partition. It is certainly not a requirement to store your data on your home partition, though, but your personal settings must be on it.

> Lastly, I wanted to make sure if NTFS is a safe choice for Ubuntu to be using, because I have heard some issues when Ubuntu deals with NTFS read/write. 

Depends what you mean by "safe". Nothing is 100% afe, but a lot of people (including myself) have been using it for a long time without problems.

---

### Post by garycheng12 on 2010-08-30
What's the difference between system configuration files and personal settings?

---

### Post by Bachstelze on 2010-08-30
> **garycheng12 said:**
> What's the difference between system configuration files and personal settings?

As the name implies, system configuration is system-wide: it applies to all users. A user's personal settings, on the other hand, apply only to that user. Note that personal settings can override system-wide configuration, if allowed by the system's policy.

---

### Post by garycheng12 on 2010-08-30
> **Bachstelze said:**
> As the name implies, system configuration is system-wide: it applies to all users. A user's personal settings, on the other hand, apply only to that user. Note that personal settings can override system-wide configuration, if allowed by the system's policy.

I will be the only user for Ubuntu, so does that mean I don't need to worry about the system configuration settings?

I know how to use TrueCrypt to encrypt files, but I'm wondering how I can create a separate partition that acts like a home partition but can be accessed by both Windows and Ubuntu, while containing the Ubuntu personal settings.


Oh yea, if you have the time can you check your mail, thanks a lot.

---

