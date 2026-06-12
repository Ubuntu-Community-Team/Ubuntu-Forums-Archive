---
title: "Overclocking leads to Kernel Panic"
date: 2005-12-13
forum: Hardware &amp; Laptops
---

### Post by akshoslaa on 2005-12-13
This isn't so much a question, more just being posted for other people to find incase someone else spends two days tearing their hair out over this problem. (Though if someone else can shed some light on why it happens I'd be interested :P)

Anyway...

My P4 3ghz is (was) overclocked to 3.75, and seemed that everything was stable. No lockups, Temp below 50c under full load, superpi and prime95 both doing their thing flawlessly (under my windows (games) partition) it was all good.

However thing started getting a bit flakey of late and I decided to tidy things up by formatting/reinstalling both my windows and linux partitions. So I reinstall windows first, that went fine, followed by linux - installing grub to the mbr (they're both on the same disk) Windows still boots fine from grub - but linux is kernel panicing right after the line 'uncompressing kernel' try it in recovery mode and the full error I'm getting is (along the lines of)

Uncompressing Kernel Image ... OK. Booting the Kernel ...
CRC Error
VFS: Cannot open root device "hda2" or unknown-block(0,1)
Please append a correct "root=" boot option
Kernel panic: VFS: Unable to mount root fs on unknown-block(0,0)

(Probably not the exact error, but close enough from memory) The important bits being that hda2/(0,1) are correct inspite of not being able to find them.

CRC error caught my eye so I used cmp on another ubuntu box I'm running to compare the kernel files. Lo and behold - initrd.img-2.6.12-9-386 differed between the system that worked and the one that didn't... copied it across and everything booted just fine.

Ran the auto update, which updated to image 12-10 and 12-10 started giving the same CRC error, though 12-9 still worked.

I tried downclocking, with do difference reinstalling _many_ time... (I'm about to do my 10th reinstall in two days)... Just installing linux (no windows, not mounting my other drives) no difference... Burning (multiple) new discs (on different burners, from different ISO's onto different branded media...) Still no good... Then I tried 5.04 - and it worked. Interesting... Upgraded from 5.04 to 5.10... stops working again...

Then I tried the bleedingly obvious that had escaped me... (*duh*)... try nstalling the new kernel _while_ being downclocked... and hurrah - it worked, plus I could set my speeds back up after installing and still have it boot... but that's fiddly - so experimented with lowering my clock just a little...

On 3.75 it wouldn't work... but on 3.6 it did... I have no idea why everything was borking so badly... I don't know why 5.04 would work, but 5.10 wouldn't. I don't know why it was creating CRC errors in instalation... I've had a hellish last couple of days... but it seems to be going t work now.. (Just finished the windows install - about to add 5.10...

Just wanted to post this experience somewhere so fellow googlers might have slightly less troubles... (All google has to say on this topic is making sure I've got SATA suppor compiled into the kernel rather than as a module... which isn;t all that helpfull given it's not actually a SATA drive...)

Hope this is of use to someone...

O)-c

---

