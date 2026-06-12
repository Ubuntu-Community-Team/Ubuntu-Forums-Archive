---
title: "dmraid Promise FastTrak capabilities..."
date: 2014-01-14
forum: Hardware
---

### Post by robsoles on 2014-01-14
Hi folks

I have to replace a drive in a RAID1 mirror shortly, it is 1Tb on a modern(ish) build using an older Promise FastTrak controller;```
rob@file-server:~$ lspci | grep RAID
01:07.0 RAID bus controller: Promise Technology, Inc. PDC20371 (FastTrak S150 TX2plus) (rev 02)
```dmraid reports all is OK but SMART status of the drive in question indicates it needs to be replaced and SOON.

This is the second time a drive in this array has needed replacing. The last time was over a year ago, by memory I was rushed to replace it and ended up waiting for the BIOS utility to duplicate the surviving drive to the new member because I couldn't find enough reassurance that dmraid can do it on the fly for Promise controller in the time I was given back then AND it seemed that on adding a raw drive to the array using the BIOS tool it just locked up the PC till it completed the duplication.

Googling and reading everything that seemed relevant has only reinforced that I need to find Robinson Crusoe and ask him what happened when he tried this, or at least, what he thinks will happen when I try it ;)

**Question:**
If I add a raw drive and skip the option to enter the FastTrak configuration tool on booting, find the raw drive and then issue ```
sudo dmraid -R <array> /dev/<raw_drive>
``` then does anybody know as a sure thing that dmraid can add the drive to the array 'properly' and *should* it rebuild the mirror successfully?


I expect that if the BIOS tool allows me to add the drive without locking up the PC while it duplicates the survivor then that dmraid -R command will rebuild the mirror on the fly so if I am wrong about that I'd appreciate knowing.

---

### Post by robsoles on 2014-01-15
dmraid probably would have done it with a less stupid (fake)raid controller. I should probably have taken the opportunity to switch to a completely soft-raid setup using mdadm but for a variety of reasons, my laziness being among top on the list, I did not. Of course, the people who own the data can't afford to lose it and don't thrill over downtime either.

I wasn't able to absolutely determine that I could even just remove the drive hot let alone hot-swap it in the implementation it is in so I shut their server down 'properly' after apt-get updating it and swapped the failing drive for a healthy one cold, rebooted and prepared to have a bash at it ;)

While booting the array status was reported as critical and I was offered the '[CTRL-F] for FastTrak config utility' for a couple of seconds longer than it offers when the array is 'normal', I let it proceed to booting from the hard drive and shortly found that the (fake)raid controller had not passed the degraded array to the operating system - I could have accessed it as /dev/sdb but it was missing from /dev/mapper and I did not even bother trying the dmraid command, I just rebooted and entered the FastTrak config utility.

No option offered to just add the new drive without locking up to duplicate it and by waiting for 1% to complete I calculate the process will complete in just under 11 hours, a bit of shrugging and apologising at the owners of the data afterwards I think it will be easier to convince them to either shell out for a real raid controller or allow me to remove that promise card and re-set their server up using software raid next time.

I wish I had a spare system with that (fake)raid controller in it so I could check my belief that between dmraid to remove the pdc metadata from the surviving member of the array and mdadm to initialise a new [S]isw[/S] [COLOR=#0000cd]soft-[/COLOR]array with that drive as source and a new drive as target for rebuild in well under an hour but I don't and if I had the cash to spare I can think of twenty things I'd blow it on first :lol:

---

