---
title: "Laptop won't boot - sometimes"
date: 2007-11-27
forum: Hardware &amp; Laptops
---

### Post by igknighted on 2007-11-27
Ok, weird issue here.

I recently bought a new laptop, which I am currently dual booting (vista and linux... of a rotating variety).  The laptop is an Acer Aspire 4520, it has an nvidia chipset and graphics card, amd athlon64m processor, blah blah blah.  I can get everything to work properly (sound, wifi, etc.) when installed.  The problem is, sometimes it just doesn't boot.  And there doesn't seem to be any rhyme or reason to why.  Sometimes it boots, sometimes it doesn't.  Removing the usplash in ubuntu/mint seems to help decrease the frequency of failure, and similarly with rhgb in Fedora and whatever Mandriva's bootsplash is called.  But not all the time.  And even without the splash and silent boot options, I see no error message that would cause a failure to boot.  Fedora tells me that /proc could not be mounted, and Ubuntu/Mint tells me nothing.

I have found that OpenSuse 10.3 boots every time so far (but I just installed it last night and have only rebooted about 10 times... granted on every other distro that would equal about 5 boot failures).  Vista also boots every time, no issues (25+ boots), so I am fairly confident to rule out hardware failure.

I would like to find a solution, because I'm not a huge opensuse fan (and I have sound issues there...).  So if anyone has any ideas as to what could be causing this, please let me know, I'm all ears.

PS... if there are any logs/config files you need to see, just let me know.

Thanks for the help.

---

### Post by edm1 on 2007-11-27
have you tried removing 'quiet splash' from the entry in /boot/grub/menu.lst?

---

### Post by igknighted on 2007-11-27
> **edm1 said:**
> have you tried removing 'quiet splash' from the entry in /boot/grub/menu.lst?

Yes, that seems to be the equivalent of not having removed it at all (with quiet and splash still there)... incidentally when I do remove them in menu.lst I seem to have more success booting when I change it back to the grub prompt... almost seeming that editing the line at boot time increases the likelihood that it will boot... which makes no sense at all to me.  So I am left to assume that it just happens by chance... which is the strangest thing.  Computers shouldn't just do things on chance, but I am struggling to find any commonalities between the times it boots, and the times it doesn't boot.

---

### Post by igknighted on 2007-11-29
Bump...

Anybody have any ideas?

---

### Post by igknighted on 2007-12-05
One final bump for good luck?

Just to note, I have been using Suse since the first post and have not had one issue with boot failure.. so it's possible.

---

### Post by Yellow Pasque on 2007-12-05
IIRC, people reporting this symptom (~50% boot rate) find that disabling acpi (with acpi=0 in boot) fixes this problem.

---

### Post by igknighted on 2007-12-18
> **Temüjin said:**
> IIRC, people reporting this symptom (~50% boot rate) find that disabling acpi (with acpi=0 in boot) fixes this problem.

This does in fact seem to resolve the booting issue.  However, booting with acpi=off (and noapic as well, as it requires the two go hand in hand on my system) means that I lose track of battery life and other rather critical laptop functions, so it's not really an option.

The fact that it works in Suse gives me some hope.  If I were to compile my own kernel from vanilla sources, could I add in support for something that Suse has that Ubuntu et. al. did not include?  Or are there some additional packages out there that would include a fix for me?  It has to be possible, as both Suse and Ubuntu use a 2.6.22 kernel and I don't have any acpi issues with Suse, I'm just curious whether it is a kernel issue or somewhere else.

---

### Post by foppeh on 2007-12-18
I tried with acer-acpi with no luck
Open Synaptic -> Add sources -> Third party software -> add
```
deb http://www.mumblyworld.info/ubuntu gutsy main
```
and now you can install it through Synaptic.

I am currently in this thread: [http://ubuntuforums.org/showthread.php?p=3974127](http://ubuntuforums.org/showthread.php?p=3974127)
My latest focus point is the temperature of the laptop. It seems to boot flawless when cold, and erronous when reboot when hot (after some work etc.)

---

### Post by igknighted on 2007-12-18
I compiled kernel 2.6.23.11 from kernel.org (following the instructions in the master kernel thread) and it seems to have done the trick.  I enabled most of the acpi related stuff when I ran 'make menuconfig' and seems to be working.  All boots (4) have been successful, and the one boot back to the old kernel failed.  Time will tell for sure, but this seems to be a success.

Now to get all my proprietary drivers back the old fashioned way... :P

---

### Post by foppeh on 2007-12-18
hi igknighted,

Thanks for your follow up in the other thread as well. 
I compiled the new kernel and unfortunately I still have the boot problem. 

I am still a believer of my temperature theory. I'll try a fresh install next with an kernel update next.

---

### Post by foppeh on 2007-12-19
I installed Sidux, only to see the same problem.
Their forum has a similar topic with no answer either: [http://sidux.com/index.php?name=PNphpBB2&file=viewtopic&t=4091&highlight=](http://sidux.com/index.php?name=PNphpBB2&file=viewtopic&t=4091&highlight=)

---

### Post by igknighted on 2007-12-19
foppeh:

I would be curious if your system worked with opensuse 10.3.  This was the only distro that worked for me right out of the box.  If it doesn't work for you we could be looking at completely different issues, if it does perhaps I compiled in support for something that you didn't and thats why mine is working?

---

### Post by foppeh on 2007-12-21
Yes,

OpenSuse worked flawless, but I didn't test it thouroughly. ' Our'  problem is reported more often and most of the times from an Acer Aspire. I think the non standard ACPI is the cause of it. Perhaps Linux interpretes the temerature setting different from what it is supposed to be.

---

### Post by igknighted on 2007-12-26
Why Suse 10.3 though?  It should be runnging the same software, and since Suse 10.3 is 100 F/OSS software, whatever they are using should be available on Ubuntu as well, even if we have to compile it.  I just really don't know what it is that we are missing, as even that custom compiled kernel I had started acting up a bit.

EDIT: Trying Hardy Alpha 2 to see if anything has changed on the new kernel

---

