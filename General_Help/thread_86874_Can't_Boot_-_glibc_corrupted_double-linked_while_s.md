---
title: "Can't Boot - glibc corrupted double-linked while starting EVM"
date: 2005-11-06
forum: General Help
---

### Post by tboersma on 2005-11-06
My Breezy system has been up and running for a few weeks, but since yesterday I can't boot. I can't think of anything that might have changed before this started happening.

When booting, Just after "Starting Enterprise Volume Management System" I get:

*** glibc detected *** corrupted double-linked list: 0x08065a30

and thats it - no choice after that but to power down. Recovery mode - same problem. Earlier kernel versions, same problem.

I'm not sure if it is a factor and this may be a red herring -- but I've got software RAID5 running on my root ( / ) partition. My /boot partition is on a different drive not using RAID. The partitions are real partions, I 'm not running LVM.

During boot it reported "mounted /dev/md0 with two drives" but did sucessfully mount as far as I can tell. Curiously, it didn't mention the third drive of my RAID5 setup. I booted the CD-ROM and went into the partition area and just looked at my RAID array (didn't change any settings nor did I run any mdadm assemble commands) Then on the next boot it said "mounted /dev/mdo with two drives (out of three)" then mounted /dev/md0 as before and hung with the same glibc error.

It's possible that this RAID issue preexisted the glibc problem - I'm not sure.

I've tried everything I can think of to recover, and searched every forum I can think of - and I haven't found a solution.

Does anyone know what's going on?

Many thanks in advance.

---

### Post by tzembi on 2005-11-08
Hi There,

I just got the same problem. However I got my system to boot by "apt-get remove evms". However this solution is not perfect for me because the packet "ubuntu-standard" will also be removed. :( And without it my system will not switch off at shutdown time for any reason :(

It started when i began fiddling with evms on a system with 2 LVM Volumes on Raid 5. However i never klicked the "save"-Button in evmsgui. ;) 

However, i noticed removing the package, booting and readding the evms stuff and then firing up a "evmsn" in a console locks up the console with the exactly same error. The boot stuff, too,  wont work after a reinstallation.

Anybody that could shed some light on this behavior ?

PS: I just opened this question on the evms forums on Sourceforge, too. Maybe they´ll know anything too...

---

### Post by tboersma on 2005-11-08
I finally determined that I had a hardware problem.  

When I booted the Live CD it also hung on EVM.  This kinda blew my mind.  I then ran memtest86 and discovered some bad areas in RAM.    I think EVM was just looking suspicious because loading it was big enough to hit my bad RAM areas.  

Swapping out RAM and running more memtest86 tests showed that in my case it was a bad motherboard/cache, not bad ram.  So using BadRAM was not an option for me.  I swapped out the motherboard and the system booted and went past EVM.  From there I was able to add back in my missing drive to my software RAID 5 system - so everything is back to normal.

---

### Post by tboersma on 2005-11-09
Wrong  !   

After swapping out the mobo, it worked for a day, then when I booted this AM - same problem exactly and same reference:  0x08065a30.    So, I've got a new motherboard and RAM (borrowed from another computer, so not out of pocket thankfully...  ;)   ) and the same 1 Boot drive and 3 hard drives set up as software RAID5 Root on /dev/md0 - now saying two drives out of three.  When I replaced my motherboard at first, it booted successfully with two drives, then I rebuilt the array.  

So I keep losing a drive and getting this double-linked corruption error on glibc right after it tries to load Enterprise Volume Manager.  Still not sure if the events are related,  I did hit "Ctrl-Alt F1" and a couple of times I could see it say "Failed to Eject CD" right after the EVMS error, then same hang.  Keyboard etc works, I can change terminals, but I can't do anything else.  Have to power down.  BTW - I swapped out the cables too.  

I wanted to boot the live CD and rebuild my /dev/md0 ofline, but the Live CD seems to mount my /dev/md0 automatically then suffers the same hang.  Maybe there's a better way? 

Does anyone have a clue?  I'm at a loss.  Even a troubleshooting direction would be most welcome.

---

### Post by tzembi on 2005-11-10
Hi again,

thats a pity. I was happily running extensive Memtests Yesterday evening in anticipation of a solution (even though it meant exchanging some brandnew Hardware (2 weeks^^)) - no flaws whatsoever in the memory (Yay ! :cool: ).

But the error remains...

I just removed the evms (Boot in recovery mode; CTRL+C your way to the sh; and "apt-get remove evms".... done.) package, hoping some programming guy will investigate. That should be anytime soon seeing Ubuntu has been certified "Ready for IBM DB2" by IBM and evms is an IBM app...^^

Removing tough seems to be OK with me because the "not shutting down when ubuntu-standard is removed" had been another thing. (seemed strange to me, too... ;) ) But im curious: Anyone who can explain the dependency ?

Regards,
TZembi

---

### Post by The Belgain on 2005-11-13
Yeah, this seems a little worrying...

I've just hit the same problem in EVMS (this is just on a test system I'm running before migrating my main RAID array over).  EVMS was working fine for me, until I tried to create an array outside EVMS (using cfdisk and then mdadm).  When I opened the array in EVMS afterwards, I get the "double-linked" error when closing down EVMS.  I dunno if it'll have made the system unbootable or not...

I'm guessing it's not a particularly good idea to try and mix-and-match using mdadm and EVMS on the same system?  Incidentally, the reason I was using mdadm is that EVMS doesn't let you deliberately create degraded RAID5 arrays (in this case a RAID5 array with only 2 drives - i.e. missing the parity drive).

On a side note, I have to say I'm very impressed with EVMS apart from this.  It would be nice to get to the bottom of this problem though...

---

### Post by The Belgain on 2005-11-13
Just to confirm... the system now won't boot for me either.  It gets stuck when starting up EVMS in the boot sequence.

Is there a better way to get it to boot than uninstalling EVMS?  Basically I'd just like a way to blow away the dodgy array that's causing the bootup problem.

[edit]Seeing as I didn't have any data on the array, I managed to get away with just Ctrl-C'ing into the shell at bootup (in recovery mode, before it hangs on EVMS activation), and just wiping the drive with the dodgy array on it (by just doing a cfdisk).  Machine boots fine now.

---

### Post by jneves on 2005-12-22
Just adding a me too.

In my specific case, the RAID 5 array is fine.

I've booted by adding init=/bin/sh in the kernel line in the boot menu and have done a:

chmod a-x /etc/init.d/evms.

Is there any bug for this issue so far?

---

### Post by jneves on 2005-12-22
[QUOTE=jneves]Is there any bug for this issue so far?[/QUOTE]

Answering myself: yes - [https://bugzilla.ubuntu.com/show_bug.cgi?id=19828](https://bugzilla.ubuntu.com/show_bug.cgi?id=19828)

According to what I've read, EVMS can destroy a degraded RAID-5 array, so uninstalling seems to be the best option.

---

### Post by Ueland on 2005-12-25
> According to what I've read, EVMS can destroy a degraded RAID-5 array, so uninstalling seems to be the best option.
Appears to be correct, i installed Ubuntu on my server yesterday, today one disk in my 4-disk RAID5 system just got "destroyed". 

Though i can boot the server by skipping the "Starting Enterprise Volume Management System" under the boot, but i dont want to keep pressing ctrl C each time i boot the server.

---

### Post by Drock on 2006-06-24
Has anyone found a solution to this other than removing EVMS?

---

### Post by tboersma on 2006-06-26
[QUOTE=Drock]Has anyone found a solution to this other than removing EVMS?[/QUOTE]

In my case it turned out to be bad hardware - I had to replace a motherboard.

---

