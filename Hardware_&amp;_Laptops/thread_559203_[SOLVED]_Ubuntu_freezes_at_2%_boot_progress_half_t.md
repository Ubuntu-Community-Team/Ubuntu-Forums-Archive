---
title: "[SOLVED] Ubuntu freezes at 2% boot progress half the time computer is [re]booted"
date: 2007-09-24
forum: Hardware &amp; Laptops
---

### Post by r0dzilla on 2007-09-24
I have been using Ubuntu for a few months, ever since I built a new system based on the Abit IP35 Pro motherboard.  The motherboard is well supported in Ubuntu, couldn't even get Fedora 7 to partition the drives.

One thing I have just grown to live with is that there is about a 50% chance or more that when I boot up or reboot Ubuntu (both 7.04 and 7.10) it will freeze at 2%.  Sometimes it will come up with errors from the initrd boot image.

I hoped switching to Gutsy would fix it but it hasn't and I want to start using power saving features but can't due to not knowing if it will recover.

Normally what I'll do is give the computer the three finger salute (ctrl-alt-del) when I see it stuck at 2%.

After 2  or so (sometimes 5 or 6 but that's rare) reboots the system will come up and works flawlessly.

When I was still using Fedora on my desktop (still do on my other machines, but I'm slowly ubuntuing them) I had a problem with an ATA problem slowing the boot up by about 10-15minutes, I believe one boot parameter that fixed this was "noirqdebug" but doesn't seem to have the same effect on ubuntu.  My problem on fedora was finally fixed by a kernel update.

My system is 100% serial ata, including the dvd burner and of course just about all new motherboards have the dreaded jmicron controller.

Without a log file to look at to troubleshoot this, has anybody had similar problems for found a solution?  I still think it may be problems similar to that I had on my old computer with Fedora but this is a new computer from the ground up.

Thanks for any information you can provide.

---

### Post by plasticM on 2007-09-26
Hi,

Apologies if seeing a post gives you false hope, but I think I may be having a similar problem (by virtue of the fact it's intermittent).

I was just wondering if, when left on 2%, your machine ever gives up and shows you a message of any kind.  I've posted my experience here:

[http://ubuntuforums.org/showthread.php?t=558001](http://ubuntuforums.org/showthread.php?t=558001)

For all the good it's done me.

Cheers,

Tim

---

### Post by r0dzilla on 2007-09-29
Well after three months or so of having boot problems the last couple patch sets pushed this past week for gutsy gibbon seems to have fixed my problem.

I have booted at least 3 or 4 times now with no problems.  Maybe I should have posted sooner... LOL

It's also funny that it started working right once I learned how to switch from the graphical boot screen to the text screen that shows the status of the boot process.

I will post here again if the boot problem rears it's ugly head again...

---

### Post by plasticM on 2007-11-01
Good news all round then.  My problem was solved by using the fix on the Dell Linux Wiki:
[http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Issues/USB-SATA_race_condition_causes_hang](http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Issues/USB-SATA_race_condition_causes_hang)

So I assume that's what the problem was.  Unfortunately the Gutsy upgrade didn't do it for me!

---

