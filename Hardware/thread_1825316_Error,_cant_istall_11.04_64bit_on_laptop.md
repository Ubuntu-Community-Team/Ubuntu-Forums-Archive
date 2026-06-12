---
title: "Error, cant istall 11.04 64bit on laptop"
date: 2011-08-15
forum: Hardware
---

### Post by thahgr on 2011-08-15
Hello everyone, Its not a new problem, but searching through everything still havent found the solution.

When booting from flash disk or cd with 11.04 I get the message "error, prefix is not set", afterwards I get to the menu. Whichever option I choose (try, istall, check disk) I get black screen.
This happens only with the 64bit version. With the 32bit everything is normal (with 2,6 out of 4 giga of ram). The same happens with latest fedora 32 and 64 bit.

I have tried some suggestions, use the alternate cd installation(same result), use the f something keys others suggest (nothing happens), write several lines i dont even remember now.

My laptop is brand new, Samsung qx-511
i5 2410
4 Gb ram
nvidia optimus gt525m and intel hd 
(I thought optimus was the origin of the error)

I need to use both windows and linux. 
Can install the 32bit version and when the issue is fixed format the linux part only and install the 64bit version? without tempering with windows?

Thank you in advance

---

### Post by thahgr on 2011-08-15
Hello, please read this thread and answer if you can..

[http://ubuntuforums.org/showthread.php?t=1825316](http://ubuntuforums.org/showthread.php?t=1825316)

---

### Post by s.fox on 2011-08-15
Threads merged.

---

### Post by varunendra on 2011-08-15
> **thahgr said:**
> 
When booting from flash disk or cd with 11.04 I get the message "error, prefix is not set", afterwards I get to the menu. Whichever option I choose (try, istall, check disk) I get black screen.
This happens only with the 64bit version. With the 32bit everything is normal (with 2,6 out of 4 giga of ram). The same happens with latest fedora 32 and 64 bit.
....
....
Can install the 32bit version and when the issue is fixed format the linux part only and install the 64bit version? without tempering with windows?
Hi, and welcome to the forums!

This error message has been often reported with WUBI installations, although it doesn't seem to be wubi specific. Anyway, it is said to be ignorable and the black screen problem seems to be graphics card related. Check this thread out for more info: [http://ubuntuforums.org/showthread.php?t=1757213](http://ubuntuforums.org/showthread.php?t=1757213)

Accordingly, have you tried to boot with failsafeX option in recovery mode in the advance grub menu?

In case of live booting, the advance menu can be brought up by pressing any key while booting from the CD/USB, then press F6 and select 'nomodeset' option.


As for installing 32 bit now and upgrading to 64 bit later, I don't see any possible problem. Ubuntu will be installed on a separate partition and won't interfere with windows anyway. It is only the Grub MBR that interferes with windows booting and reinstalling/upgrading grub is not a problem.

---

### Post by thahgr on 2011-08-15
Thanks for the welcoming,

Well, I havent tried WUBI installation, I just boot from flash disk.

You suggest its vga card oriented, but why is there no problem with the 32bit version? This drives me to say its an 64bit problem installation.

The f6 key doesnt work..

I havent tried the "failsafeX option in recovery mode in the advance grub menu**" **how is this done?

---

### Post by varunendra on 2011-08-15
> **thahgr said:**
> Well, I havent tried WUBI installation, I just boot from flash disk.
So may we assume now that we are talking about a live session not an installed version?

> **thahgr said:**
> You suggest its vga card oriented, but why is there no problem with the 32bit version? This drives me to say its an 64bit problem installation.
When we say some 'device' related, we do not necessarily mean that the device is defective, while it (rarely) may be, most often it means there's a 'driver' issue with that device, causing that device not work properly. :)

There has been a history of drivers not working correctly with 64bit kernel, and although this has been improved to a great extent in modern kernel/drivers, this kind of issue still occurs sometimes with some specific models.

> **thahgr said:**
> The f6 key doesnt work..

I havent tried the "failsafeX option in recovery mode in the advance grub menu**" **how is this done?
If it is a live session, you won't get advance Grub menu. It is created for installed version only. For a live session, when you press any key while booting from the flash disk, do you get a menu asking you to select language? The F6 option is accessible just after that language selection step. So, does the option appear but doesn't work or doesn't it appear at all?


**_EDIT_:** 
If nothing works and you have to fall back to 32bit, you may install pae-enabled kernel to use full amount of RAM. It automatically gets installed in 10.04 (and later) if 4GB or more RAM is available.

---

