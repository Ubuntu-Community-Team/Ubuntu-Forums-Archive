---
title: "Speed of shredding a hard drive"
date: 2009-06-16
forum: Hardware
---

### Post by youoneah on 2009-06-16
Hi all,

I've been given a modern laptop by a friend and have just had the motherboard replaced by a licensed repairman (defective graphic chip). My friend asked me to securely delete his data for the case that the laptop would ever be passed on. I'd never actually done this, but some googling turned up various methods, including Darik's Boot and Nuke and killdisk.com. In the end, I decided to use a GNU tool, since I didn't feel like burning Yet Another CD, as described in the following articles:
[http://linuxhelp.blogspot.com/2006/06/how-to-securely-erase-hard-disk-before.html](http://linuxhelp.blogspot.com/2006/06/how-to-securely-erase-hard-disk-before.html)
[http://www.oreillynet.com/sysadmin/blog/2005/03/please_for_the_love_of_all_tha.html](http://www.oreillynet.com/sysadmin/blog/2005/03/please_for_the_love_of_all_tha.html)
I also noted that this procedure is correctly called *reinitializing* and not [low-level formatting.]("http://en.wikipedia.org/wiki/Disk_formatting#Low-level_formatting_.28LLF.29_of_hard_disks")

I booted the machine with a live CD of Jaunty Jackalope and brought up the CLI. The command I used is ```
$ sudo shred -vfz -n 100 /dev/sda
```
This set about its task, but I noticed with mild disquiet that it is much slower than my expectation. The hard-drive is "250 GB" (shred reports "233 GiB"), and after a couple of hours it had only polished of a few percent of the first pass. I let it run overnight and in the morning it had gotten up to eighty-three percent; still only of the first pass. Since this is a modern machine, I expected that a random overwrite of 233 GB would be finished in less than an hour. Assuming one of the above methods is 

My current plan is to interrupt the process later today after it's finished the first pass, so that I'm relatively sure that at least the whole drive has been randomly overwritten once. Then I'll possibly try re-invoking the command just to overwrite with zeros. If that goes equally slow, I might look for other options.

Has anyone else here experience with the shred command? Is this really a typical speed, or could something be wrong?

Since someone is likely to ask, the machine is a Dell M1330, so the hard-drive is S-ATA. I left the BIOS setting for the drive on AHCI.

Thanks for any feedback,
Mike

---

### Post by stinger30au on 2009-06-16
boot and nuke is the go, you woul have had it done by now and with out all the stuffing round as well

[http://www.dban.org/](http://www.dban.org/)

---

### Post by youoneah on 2009-06-16
Yes, as I mentioned I did it that way because I didn't feel like mucking about with burning a new CD. I don't mind stuffing around a bit, after all I was sleeping and working while it ground things out. In any case, something happened while I was at work today, because at lunchtime it was on its fourth pass. That means during four hours it made well over two passes, although it took the whole night plus some to do 83% of the first pass. I noticed last night that the hard-drive LED wasn't lighting up much, and today it was constantly lighting, so something was holding things up. In the end it's done 7 complete passes in about 24 hours, so I interrupted it and am now filling zeros (more or less "for fun") with "sudo dd if=/dev/zero of=/dev/sda". The old data should be nigh-unrecoverable now.

Things are fixing to get crankin', after Vista come Debian, Ubuntu, and Linux Mint.
:popcorn:

---

### Post by jward3010 on 2009-11-18
The reason it took so long is because you performed 100 passes, this is so excessive it's worse than Simon Cowell's annual income of $75 million.

Do a lower amount like about 2 or 3, also keep in mind that the shred command does take it's time. There are ways to speed it up but I'm researching this at the mo.

---

### Post by youoneah on 2009-12-18
Actually, that's not the reason:
[QUOTE="youoneah"]The hard-drive is "250 GB" (shred reports "233 GiB"), and after a couple of hours it had only polished of a few percent of the first pass. I let it run overnight and in the morning it had gotten up to eighty-three percent; still only of the first pass.[/QUOTE]

"The shred command does take it's time" is certainly the right assessment. All ended well though.

---

### Post by Cheesemill on 2009-12-18
No need for multiple random passes, just doing:
```
sudo dd if=/dev/zero of=/dev/sda
```
will blank the drive.

---

### Post by jward3010 on 2009-12-20
Oh, I agree, a 250GB drive will take it's time and I would hate to think what a 1TB would take, but 100 passes @ a day a "pass" was going to be the real time enhancer here if OP let it keep going.

As far as I know there are arguments you can pass to "dd" that can increase the speed but you need to know the technicalities of the drives sectors, blocks etc. blah etc. blah and I'm not completely sure of that stuff. I certainly know that you can speed up a zero write of a USB key when you provide certain block details to dd.

---

### Post by youoneah on 2009-12-21
Thanks Cheesemill, but as stated in the original post my goal was not to blank the drive, which zeroing it does not do.

Anyway, I found the shred command convenient (much more so than dd) and powerful, but was surprised by the amount of time needed. Thanks for all replies!

---

