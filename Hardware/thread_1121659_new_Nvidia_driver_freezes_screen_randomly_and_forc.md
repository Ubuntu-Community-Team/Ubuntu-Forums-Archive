---
title: "new Nvidia driver freezes screen randomly and forces scan on bootup"
date: 2009-04-10
forum: Hardware
---

### Post by Irishpolyglot on 2009-04-10
I have checked other threads and seen that I'm not alone, others have had problems with the new Nvidia driver, like here:
[http://ubuntuforums.org/showthread.php?t=1115079]("http://ubuntuforums.org/showthread.php?t=1115079")
The cause is the same, but my problem is different to any others I can find. 

Nvidia automatically updated to 180 earlier this week and my computer (Dell Inspiron 9400 with nVidia Geforce Go 7800) did not like it!! At first I couldn't get past a black screen after boot up, and after trying a lot of different things I gave up and formatted the computer and installed a new OS (previously on 8.10, now on 9.04 beta). Very frustratingly, the problem remains. The hard drive is forced to a scan regularly, and the boot-up screens are unclear and have lines across them.

I found a temporary (albeit timeconsuming) alternative of accessing Ubuntu, but sometimes putting the computer to sleep gives me the black screen again and the process has to be repeated. Ubuntu will always freeze randomly anyway if I use simple applications for 5-10 minutes. Ctrl+Alt+F1 or F7 or Backspace do nothing and I have to force the computer to reboot. When I do this I am back to the black screen after the Ubuntu boot-up.

So here is what I do to get back to a temporarily working system (until the next freeze). I've tried it several times; it's extremely frustrating but works. Maybe this process will tell you what is going wrong? Here is what I do:

**1. **Select the "recovery" version of Ubuntu from from grub. (Note that at this stage the Dell boot-up screen is not crisp; there are lines all over the place. If I leave it, I see those same lines on the Ubuntu boot-up screen.), Instead of giving me the usual selection screen (dpkg, fsck, grub etc.) it goes immediately into checking the root file system (I can't cancel this with Esc etc.) The message it gives is as follows:

> ...
* Checking root file system
fsck 1.41.1 (27-Jan-2009)
/dev/sda1 was not cleanly unmounted, check forced
/dev/sda1
Deleted inode 4554774 has zero dtime, FIXED
/dev/sda1: |==========
and it scans for a few minutes, with some other inodes with zero dtime that it fixes. Then I see:
> /dev/sda1: ***** REBOOT LINUX ******
/dev/sda1: 113901/16416768 files (0.6% non-contiguous),
fsck died with exit status 3
and it reboots.

**2.** After rebooting, either (a) the Dell boot-up screen looks clear as it should and then Ubuntu loads as normal and will work fine for 5-10 minutes until it crashes again, **or** (b) if the Dell boot up screen is still not clear with lines across it, it would boot into the black screen again so to avoid this I go back into recovery mode; this time there is no scan and I have the usual list to select. I go to root and simply type "reboot". If this doesn't work I try fsck, reboot and then the screen looks fine and Ubuntu works.

Back when in the OS even if I enable older versions of Nvidia like 173 or 96 that are in the list, I still have to go through the rebooting sequence. Nvidia version 180 is what initially caused the problem, and even after formatting and reinstalling it, I still have this issue. Even with Nvidia disabled, Ubuntu will still crash after a short time.

I have tried everything I can think of; and I really do not understand why doing what I do makes it work temporarily. I would really appreciate some more suggestions/advice!!! I just formatted a segment of the disk for Windows, installed it and it's working fine when selected. I'd rather not have to use that permanently :(

Thanks!!!

---

### Post by sowelie on 2009-04-10
Are you using the drivers from the repos?  Have you tried installing the official drivers from nVidia?  I always use the drivers from nVidia as they perform better than the ones in the repos.  The ones in the repos are always a bit behind.

---

### Post by Irishpolyglot on 2009-04-10
Thanks for the response. I downloaded the latest driver version (180.44) and tried to run it as suggested on the Nvidia site (sh file_name), but it can't be run when X is running. I tried to run it from root after booting up, but my hard-drive seems to be read-only then and the driver installation can't load.

I'm not even sure if that would work, but I might have to leave it - I've spent so much time on this problem... I might have to use Windows for the next 2 weeks and install 9.04 when it comes out and hope that good drivers are updated then...

---

### Post by rabaal on 2009-04-11
oh my god, so i'm not the only one with this problem =D
everything you're discribing is what is happening to me, albet, it all started differently for me but the end result and problems are all the same.

Does anyone have any idea on how to fix this issue, i was using ubuntu 8.10 but recently went to version 8.04 due to this problem and not being able to get past the boot screen.

---

### Post by PhileDealer on 2009-04-11
I've had some funny issues with 180 as well. It crashed the display and needed to hard reset. I was lucky and I always got X back after restart. I had to go back to 177 drivers and it seems to be better now. I have the 9200m card.

---

### Post by Irishpolyglot on 2009-04-11
Wow, this new driver really got its claws into my computer :( Even WINDOWS doesn't work unless I'm in safe mode (as soon as I had installed the Windows Nvidia drivers). I'm amazed at this; I've formatted the entire computer twice since the problem started and this is even a different partition. How is this possible?? I still see the Dell boot-up screen as garbled.

I would honestly think I dropped my computer without noticing and physically broke it if others didn't comfirm they have similar issues since this driver update

Any solution really appreciated!!! If I don't fix this in the next couple of days I'll have to buy a new laptop before I get back to work :( Can someone at least give me hope that reformatting and installing Ubuntu 9.04 on Friday (Release Candidate) or a week later (official release) might help or make any difference? Maybe by then the Ubuntu version of the Nvidia drivers will have been updated. Or is my computer somehow damaged for life?

---

### Post by MechWarrior001 on 2009-04-11
I don't know how to fix this, sorry.

But I think it is possible that the new driver might contain malicious code, based on what you have told us.

If you can, I would do a complete format, and go way back to maybe, 7.XX, and go with the stable 96-177 drivers off of the repository, and then wait a bit before going back to 8.XX. Even then, go with the stable release.

You might end up having to replace your systems HDD.

---

### Post by Irishpolyglot on 2009-04-12
I don't think reinstalling any version of the drivers will help; I've just formatted the computer once more and there are NO Nvidia drivers currently installed, but the Dell screen is still garbled. I always selected stable releases previously and that caused the problem. From previous experience I know that if I enable any drivers I'll be back where I started. At least with weak graphics and no drivers I know the computer won't crash randomly. But I can't work like this and I have to look into replacing my computer :(

Nobody has any other suggestions?? Replacing the hard drive seems like a lot of work/money for an unsure solution, in which case I might as well buy a new laptop. If formatting the hard drive doesn't work, why would replacing it? This problem seems to have gotten into the BIOS or something.

Anyone else?? Surely there's a solution to this - how could malicious code have gotten into the system for so many people?? I thought Ubuntu and its trusted repositories were built to prevent such things.

---

### Post by MechWarrior001 on 2009-04-12
> **Irishpolyglot said:**
> I don't think reinstalling any version of the drivers will help; I've just formatted the computer once more and there are NO Nvidia drivers currently installed, but the Dell screen is still garbled. I always selected stable releases previously and that caused the problem. From previous experience I know that if I enable any drivers I'll be back where I started. At least with weak graphics and no drivers I know the computer won't crash randomly. But I can't work like this and I have to look into replacing my computer :(

Nobody has any other suggestions?? Replacing the hard drive seems like a lot of work/money for an unsure solution, in which case I might as well buy a new laptop. If formatting the hard drive doesn't work, why would replacing it? This problem seems to have gotten into the BIOS or something.

Anyone else?? Surely there's a solution to this - how could malicious code have gotten into the system for so many people?? I thought Ubuntu and its trusted repositories were built to prevent such things.

They are, but remember that for the most part, most of Ubuntu software is Open source. Even though the drivers came from Nvidia, someone could have slipped a Viral program written for Linux into the Nvidia section of the repository. (Just a thought) However, I don't think its likely that happened and I dont know many viruses that are capable of effecting the BIOS. It might be that the drivers caused a section of the system to malfunction and damage the physical components (like overclocking, for example), which resulted in the BIOS/System corruption.

---

### Post by Irishpolyglot on 2009-04-13
Thanks for your explanation... it at least makes sense. 

So, sadly I have to look into getting a new computer. The one I want to replace this with also has Nvidia drivers, I'm quite scared to get it because of that! The hardware is completely different and the Nvidia version is different (8700M), but I'd hate to have to face this same issue in the future. Is there some way I can avoid it? Are all graphics card updates just as prone to this problem? Is there any real advantage to enabling these updates if the graphics card already works?

Is anyone else as horribly screwed as I am with their computer? Mine is 2 years old and used every day, maybe some wear contributed to the problem?

Until I buy it tomorrow, I'm still open to suggestions if there is some magic solution I haven't tried yet...

---

### Post by sowelie on 2009-04-15
I would try the latest drivers first...all you have to do is the following to is hit CTRL+ALT+F1 to get to the terminal and then:

```

sudo /etc/init.d/gdm stop
chmod +x (name of the installer).bin
sudo ./(name of the installer).bin

```

Follow the prompts and then:

```

sudo /etc/init.d/gdm start

```

You can then re-log in and everything should be fine.  I've never had problems with the latest NVIDIA drivers, they're almost always very well done.  You definitely get the best performance out of the newer drivers.

---

