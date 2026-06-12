---
title: "Acer E3-112-C0MQ - HELP"
date: 2016-05-28
forum: Hardware
---

### Post by weardgar on 2016-05-28
SUMMARY: ANY *buntu except 12.04 LTS 32 bit will randomly freeze, as in complete and total system halt, no keys respond and laptop must be powered off with a long press. This happens in games, in browsers and while watching videos.

Hello all,

I am not entirely new to Ubuntu or anything like it, however I have come across an issue I have no idea how to fix. I purchased my notebook while in Korea, and removed the Windows 8.1 that was pre-installed. This all started about a year ago. 

As I stated above, the only *buntu I can get to work is Ubuntu 12.04 LTS 32 bit (64bit works, but is hit and miss). Before I realized I needed to install in UEFI mode, the laptop would lock up on a shut down or on a boot up sometimes, however, this is solved in UEFI mode with *buntu 16.04. The problem is that I am still getting random freezes that are 100% lock up leading me to a long press to power off the system. I think this has something to do with the GPU as it tends to happen mostly while watching videos online, during multiple browser window usage with downloads running, and especially during games in Wine or running natively from the software center.

I originally though maybe this was due to my CPU or RAM, but it has frozen while both are well within safe limits. I have even had the system lock up while idle on Lubuntu, using 3% CPU and 360mb of 2GB RAM.


Please let me know what commands to run to generate logs necessary for diagnosis. I am not terminal shy, so go nuts. This is my only problem with Ubuntu now and I really want to fix it...I don't want to go back to Windows :(

---

### Post by oldfred on 2016-05-28
It looks like that is a Bay Trail Processor.

       Bay Trail freeze need boot parameter: intel_idle.max_cstate=1 or patches, see comments
[https://bugzilla.kernel.org/show_bug.cgi?id=109051](https://bugzilla.kernel.org/show_bug.cgi?id=109051)
Many Intel Bay Trail Devices Have Been Borked On Linux For The Past Year - Mar 2016
[http://www.phoronix.com/scan.php?page=news_item&px=Intel-Linux-Bay-Trail-Fail](http://www.phoronix.com/scan.php?page=news_item&px=Intel-Linux-Bay-Trail-Fail)

---

### Post by weardgar on 2016-05-28
> **oldfred said:**
> It looks like that is a Bay Trail Processor.

       Bay Trail freeze need boot parameter: intel_idle.max_cstate=1 or patches, see comments
[https://bugzilla.kernel.org/show_bug.cgi?id=109051](https://bugzilla.kernel.org/show_bug.cgi?id=109051)
Many Intel Bay Trail Devices Have Been Borked On Linux For The Past Year - Mar 2016
[http://www.phoronix.com/scan.php?page=news_item&px=Intel-Linux-Bay-Trail-Fail](http://www.phoronix.com/scan.php?page=news_item&px=Intel-Linux-Bay-Trail-Fail)

Thank you for the quick reply, I will give this some vigorous but quick testing tonight.

---

### Post by weardgar on 2016-05-30
> **oldfred said:**
> It looks like that is a Bay Trail Processor.

       Bay Trail freeze need boot parameter: intel_idle.max_cstate=1 or patches, see comments
[https://bugzilla.kernel.org/show_bug.cgi?id=109051](https://bugzilla.kernel.org/show_bug.cgi?id=109051)
Many Intel Bay Trail Devices Have Been Borked On Linux For The Past Year - Mar 2016
[http://www.phoronix.com/scan.php?page=news_item&px=Intel-Linux-Bay-Trail-Fail](http://www.phoronix.com/scan.php?page=news_item&px=Intel-Linux-Bay-Trail-Fail)


I just wanted to say thank you so much. This solution has at least for now been perfect. I extended my testing and really pushed the limits of what the computer can do and had no trouble. Thanks again!

---

### Post by oldfred on 2016-05-30
Glad that worked.
Hopefully Intel gets updates into distributions soon.

---

