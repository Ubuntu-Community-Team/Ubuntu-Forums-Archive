---
title: "Installed, Did Not Detect Vista"
date: 2009-10-03
forum: Installation &amp; Upgrades
---

### Post by Moptop650 on 2009-10-03
Hi,
I just installed Ubuntu on my desktop. The install was kind of... Shaky. When I booted to live, nautilus segfaulted, and I couldn't launch it. Oh well, I installed anyways. Once I booted off the HDD, everything worked fine.

Except, the windows install on my other HD wasn't detected, and wasn't added to Grub. I have ubuntu + swap space on sda, windows (7) on sdb, and data on sdc-e.

What can I do to get back into my windows?

Edit: I should mention this also - the drive I put ubuntu on, used to have Windows Server 2008, the previous primary OS, so I think the bootloader for Server 08 and 7 was on that drive.

Should I repair windows 7 then reinstall grub?

Edit 2: I tried to repair windows 7, and it said the disc I was using is incompatible with that version of windows, but its the same disk I used to install it. What?

---

### Post by bumanie on 2009-10-04
In general, it is accepted that windows prefers to be on the first partition of the first hard drive when in a dual boot situation with linux. Could you please provide the output of terminal command sudo fdisk -l (that is a lower case L), it's a good starting point to know exactly how your partitioning is set up. Also which version of ubuntu are you using?

---

### Post by Moptop650 on 2009-10-04
I got into the windows repair thing, which I completed, but now I've got Bootmgr is missing, on boot. So I tried reinstalling grub, and that didnt' change anything. 

I did fdisk -l from the Live cd:

(Switching computers, I'll edit in a sec)

Edit: Well that listed my liveCDs thing, my fault.

My partitions are like this, though:

HD0: 
Part1: swap
Part2: Ubuntu

HD1:
Part1: Windows 7

And the rest of the drives are data drives.

I'll try swapping some plugs and move Windows to HD0, and the linux drive to HD1.

Edit: Ubuntu 9.04 32bit, btw.

---

### Post by bumanie on 2009-10-04
That is not a bad idea, although if bootmgr is missing, vista still won't boot. You will have to find a copy of bootmgr to install onto the vista drive. [This]("http://cyberst0rm.blogspot.com/2007/04/how-to-fix-bootmgr-is-missing-in.html") may help.

---

### Post by Moptop650 on 2009-10-04
Hmm... When I'm doing bootrec /rebuildbcd, I get an Element Not Found error when I go to add my windows install to the boot list.

[http://www.beginnerspc.com/articles.cfm?articleid=2264&page=9](http://www.beginnerspc.com/articles.cfm?articleid=2264&page=9)

So I found that, tried it, and it didn't fix the error...

BTW, to simplify things in repairing windows, I unplugged every hard drive except the windows one.

Edit: HEY! I got it working. Something about unplugging all of the drives EXCEPT the windows one worked. 

Thanks so much for the help! :)

---

