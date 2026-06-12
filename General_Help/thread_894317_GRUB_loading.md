---
title: "GRUB loading"
date: 2008-08-19
forum: General Help
---

### Post by /////// on 2008-08-19
Is it possible to get grub to load only if a specific button is pressed during boot and if it isn't pressed the default OS (Ubuntu) is loaded?

---

### Post by AndyCee on 2008-08-19
Yes.

In your /boot/grub/menu.lst [note LST, not 1ST] file, find and set the "Timeout" variable to 0.

Grub will load, but the menu will be hidden. While it's loading, you've about 3 seconds to press 'escape' and bring up the GRUB menu.

---

### Post by /////// on 2008-08-19
Yes I know this, but what I mean is that GRUB doesn't load at all (Lol I'm trying to shave off those few seconds it takes GRUB to load at boot time) xD

---

### Post by mcduck on 2008-08-19
> **/////// said:**
> Yes I know this, but what I mean is that GRUB doesn't load at all (Lol I'm trying to shave off those few seconds it takes GRUB to load at boot time) xD

No. Grub (or some other bootloader) is needed to boot Linux. Just like Windows won't load without it's own bootloader (ntldr).

---

### Post by /////// on 2008-08-19
I thought GRUB works like this: When your computer boots it looks into the MBR which will direct it to load GRUB, GRUB then loads the actual bootloader for the OS such as ntldr. So it goes Boot -> MBR -> GRUB -> NTLDR -> Windows. What I want is for the native Ubuntu bootloader (the Ubuntu equivalent of NTLDR) to boot withour GRUB telling it to (like normal windows booting without GRUB) unless a certain key is pressed at boottime which will call GRUB to boot instead of the Ubuntu bootloader.

---

### Post by bigyoy on 2008-08-19
I don't think there is a way around this I'm afraid as the bootloader has to be loaded.

But thinking about it, what are you planning on spending those 3 seconds you save on? :p

---

### Post by Bucky Ball on 2008-08-19
Disregard, posted in error ... :)

---

### Post by /////// on 2008-08-19
Well its like 5 seconds for me O.o and say I boot my computer up once a day 5x365=1825. In a year, I get to save 30 minutes of my life :P Plus I'm interested in how this will work xD

---

### Post by Sorivenul on 2008-08-19
If you haven't already, try "preload".  It's in the repos.  Information is available here:
[http://www.techthrob.com/tech/preload.php]("http://www.techthrob.com/tech/preload.php")
It won't change anything about GRUB itself, but does a good job of speeding up a system in general.  

EDIT:  More general ideas...
[http://www.linuxdevcenter.com/pub/a/linux/2000/06/29/hdparm.html]("http://www.linuxdevcenter.com/pub/a/linux/2000/06/29/hdparm.html") - hdparm
[http://ubuntuforums.org/showthread.php?t=565651]("http://ubuntuforums.org/showthread.php?t=565651") - readahead
[http://ubuntuforums.org/showthread.php?t=292961]("http://ubuntuforums.org/showthread.php?t=292961") - concurrency
[http://ubuntuforums.org/showthread.php?t=254263]("http://ubuntuforums.org/showthread.php?t=254263") - reprofile your boot
[http://ubuntuforums.org/showpost.php?p=1255511&postcount=43]("http://ubuntuforums.org/showpost.php?p=1255511&postcount=43") - adjust swappiness
[https://help.ubuntu.com/community/SwapFaq]("https://help.ubuntu.com/community/SwapFaq") - more on swap and swappiness
[http://kerneltrap.org/node/14148]("http://kerneltrap.org/node/14148") - noatime and relatime boot options
Good luck.

---

### Post by mcduck on 2008-08-19
> **/////// said:**
> I thought GRUB works like this: When your computer boots it looks into the MBR which will direct it to load GRUB, GRUB then loads the actual bootloader for the OS such as ntldr. So it goes Boot -> MBR -> GRUB -> NTLDR -> Windows. What I want is for the native Ubuntu bootloader (the Ubuntu equivalent of NTLDR) to boot withour GRUB telling it to (like normal windows booting without GRUB) unless a certain key is pressed at boottime which will call GRUB to boot instead of the Ubuntu bootloader.

That's how it works for Windows. For Linux, Grub _is_ the bootloader, and loads the Linux kernel.

So, for Linux, Grub *is* the "native bootloader", for Windows, Grub starts ntldr which is the native bootloader for Windows.

POST->MBR(Grub)->Linux
POST->MBR(Grub)->ntldr->Windows
POST->MBR(ntldr)->Windows

---

### Post by AndyCee on 2008-08-23
If you're just looking to boost subsequent boot speeds, add "profile" without quotes to the end of the boot command when grub loads.

---

