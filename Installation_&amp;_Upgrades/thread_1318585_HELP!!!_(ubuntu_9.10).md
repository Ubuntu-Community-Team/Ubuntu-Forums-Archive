---
title: "HELP!!! (ubuntu 9.10)"
date: 2009-11-07
forum: Installation &amp; Upgrades
---

### Post by ferret man on 2009-11-07
I recently upgraded from 9.04 to 9.10, and long story short, all of the permissions got changed on my computer, and I can not log on as anyone (even the superuser). Now, I tried to reprogram ubuntu on my computer, but it doesn't give me the permission to mount my USB drive. I need help. I have a Dell Mini 9 with Ubuntu 9.10 NetBook Remix installed on. If someone could maybe tell me how to maually install the new ubuntu, or uninstall my last one, it would be great.
 
P.S. Please, help me. Thanks for your time.

---

### Post by dhavalbbhatt on 2009-11-07
> **ferret man said:**
> I recently upgraded from 9.04 to 9.10, and long story short, all of the permissions got changed on my computer, and I can not log on as anyone (even the superuser). Now, I tried to reprogram ubuntu on my computer, but it doesn't give me the permission to mount my USB drive. I need help. I have a Dell Mini 9 with Ubuntu 9.10 NetBook Remix installed on. If someone could maybe tell me how to maually install the new ubuntu, or uninstall my last one, it would be great.
 
P.S. Please, help me. Thanks for your time.

Your post is unclear - on the one hand you say you were not able to login, even as the superuser, and then you mention that you re-programmed Ubuntu. What does that mean?

---

### Post by ferret man on 2009-11-07
I apologize. 
Timeline:
1st: Program Ubuntu 9.10, everything is fine.
2nd: Permissions get changed, cannot log on.
3rd: Attempt, but fail to reprogram ubuntu 9.10, because the permission is denied.
4th: I need help.
 
Meaning of all of this: I cannot use my computer, and when I try to reinstall the OS, it is denied. I need to reprogram it so that it can run. Perhaps I can delete the partition and create a new one? I don't know. I am new to Linux and know nothing, in depth, about computer programing. 
 
I do have a "live USB drive" with Ubuntu 9.10 on it, so if I can find out how to install that on my laptop, that would be great.
 
Finally, the OS currently on my computer is not a "healthy", or freshly installed one. It is the damaged, permissions are out of whack, one.

---

### Post by ferret man on 2009-11-07
> **ferret man said:**
> I recently upgraded from 9.04 to 9.10, and long story short, all of the permissions got changed on my computer, and I can not log on as anyone (even the superuser). Now, I tried to reprogram ubuntu on my computer, but it doesn't give me the permission to mount my USB drive. I need help. I have a Dell Mini 9 with Ubuntu 9.10 NetBook Remix installed on. If someone could maybe tell me how to maually install the new ubuntu, or uninstall my last one, it would be great.
 
P.S. Please, help me. Thanks for your time.
 
I apologize. 
Timeline:
1st: Program Ubuntu 9.10, everything is fine.
2nd: Permissions get changed, cannot log on.
3rd: Attempt, but fail to reprogram ubuntu 9.10, because the permission is denied.
4th: I need help.

Meaning of all of this: I cannot use my computer, and when I try to reinstall the OS, it is denied. I need to reprogram it so that it can run. Perhaps I can delete the partition and create a new one? I don't know. I am new to Linux and know nothing, in depth, about computer programing. 

I do have a "live USB drive" with Ubuntu 9.10 on it, so if I can find out how to install that on my laptop, that would be great.

Finally, the OS currently on my computer is not a "healthy", or freshly installed one. It is the damaged, permissions are out of whack, one.

---

### Post by dhavalbbhatt on 2009-11-07
> **ferret man said:**
> I apologize. 

Meaning of all of this: I cannot use my computer, and when I try to reinstall the OS, it is denied. I need to reprogram it so that it can run. Perhaps I can delete the partition and create a new one? I don't know. I am new to Linux and know nothing, in depth, about computer programing. 



Do you have a LiveCD with which you can boot? I don't use a Live USB, so won't be able to help with that. But if you have a LiveCD, then you can use GParted on that to format your HDD. See if that works. That will also allow you to install all over again.

---

### Post by jheaton5 on 2009-11-07
I have a Dell mini9 and it doesn't have an optical drive.  Is yours the same?

Have you entered the BIOS setup and made sure the boot sequence is set to boot from the USB device first?  If not, do so.
If your mini9 will not boot from the usb device, then there is something wrong with the device, either a bad download or a bad burn.  How did you come by the usb live install?

---

