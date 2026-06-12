---
title: "Continuous filesystem corruption"
date: 2010-05-19
forum: Hardware
---

### Post by thomas430 on 2010-05-19
Hi everyone,

I'm running ubuntu 10.04 on a Dell Studio 17. Every 3 or 4 days since I installed 10.04, there has been filesystem corruption, and I can't boot. I have tried using fsck, and it makes so many changes while fixing that the system doesn't load anymore (or once the system loaded, but gnome was corrupted in some way... )

The first fs corruption, I thought it was because I had to force power down. The second time was random, and I thought that it might be because I was using the ext4 filesystem *or* that suspend/resume wasn't working properly. I then reinstalled using ext3, and made sure I didn't suspend or hibernate at all. But I've woken up this morning and it has happened again! I'm running the live CD to pick up a couple of uni assignments and post this, but don't have time to reinstall this morning. It's making me sad..

Is there any chance that it may be a damaged hard disk? Blegh.. I don't want to call Dell.

Finally... I have ubuntu on a 304 GB partition, and windows on about 180GB, and I used the GParted liveCD to resize the windows partition and create a new one for ubuntu. Don't know if that is of any significance.


Thanks for any help!


Tom.

---

### Post by thomas430 on 2010-05-20
I just checked the SMART data.. I hadn't seen this tool before. The reallocated sector count entry is red and it says that there are 3 bad sectors. I guess that because they are reallocated that this shouldn't be the problem?

On a side note.. It has a power-on value of 1.3 years. This is a new disk.. so is this value the expected life of the disk?

**New development:** I booted again, (actually by accident pressing enter in grub by reflex), and ubuntu loaded to the login screen :confused:. Note: no fsck has been carried out since the file system broke, because the previous times this just corrupted things worse. When I logged in, I got an error message saying that some file could not be accessed... I think it was something to do with an authorisation file or something. ..Might be because of the filesystem errors, or because I used chown from the liveCD this morning to get my uni assignments? Anyway, it then loaded the desktop as usual.

So do I have file system errors or not??! I'm currently doing an extended scan using the disk utility (the quick scan said there were no surface errors). 'Check filesystem' in the disk utility when I ran the liveCD said that there were file system errors.


I don't like not knowing if my computer will turn on when I sit down ready to do some work :-( and even while it won't load I find Ubuntu more functional and user friendly than windows... so I'm lost for what to do.

OH! I meant to ask: I have a 64 bit system, and the 32 bit version of Ubuntu installed. Is that okay?

---

### Post by Ravernomina on 2010-05-20
> **thomas430 said:**
> I just checked the SMART data.. I hadn't seen this tool before. The reallocated sector count entry is red and it says that there are 3 bad sectors. I guess that because they are reallocated that this shouldn't be the problem?

On a side note.. It has a power-on value of 1.3 years. This is a new disk.. so is this value the expected life of the disk?

**New development:** I booted again, (actually by accident pressing enter in grub by reflex), and ubuntu loaded to the login screen :confused:. Note: no fsck has been carried out since the file system broke, because the previous times this just corrupted things worse. When I logged in, I got an error message saying that some file could not be accessed... I think it was something to do with an authorisation file or something. ..Might be because of the filesystem errors, or because I used chown from the liveCD this morning to get my uni assignments? Anyway, it then loaded the desktop as usual.

So do I have file system errors or not??! I'm currently doing an extended scan using the disk utility (the quick scan said there were no surface errors). 'Check filesystem' in the disk utility when I ran the liveCD said that there were file system errors.


I don't like not knowing if my computer will turn on when I sit down ready to do some work :-( and even while it won't load I find Ubuntu more functional and user friendly than windows... so I'm lost for what to do.

OH! I meant to ask: I have a 64 bit system, and the 32 bit version of Ubuntu installed. Is that okay?

Yeah that is Totally Fine. I think you Better Call ur Computer Manu, or Ware you got the HD from. they owe you a new one. And it Seems like you HD is Dyeing.... back-up everything

---

### Post by thomas430 on 2010-05-20
Yeah, it seems that way.. and I'm sure there are still problems with the file system. I just tried to load open office, and got a message saying "The application cannot be started. An internal error occurred".

I find it weird that the disk says Powered On: 1.3 years... have Dell been dodgy?

---

### Post by thomas430 on 2010-05-20
Alright - the assessment for the SMART data for power on time is N/A... so I guess that means the value of 1.3 years is meaningless? Also, the surface scan of the disk detected no errors.

This laptop is only 3 weeks old!

Does anyone have any ideas for where to go from here?

---

### Post by thomas430 on 2010-05-26
Solution: swap to Fedora.

Hurray! Clean, crisp operating system that doesn't **** my file system.

---

