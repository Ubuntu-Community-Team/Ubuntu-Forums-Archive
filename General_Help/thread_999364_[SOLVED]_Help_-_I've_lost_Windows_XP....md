---
title: "[SOLVED] Help - I've lost Windows XP..."
date: 2008-12-01
forum: General Help
---

### Post by AndrewS on 2008-12-01
Hi

I have a problem, in that I cannot boot my PC into XP - not something I do often nowadays, but something I do still need occasionally.  This is a bit long-winded, but the history to this is as follows...

[INDENT]Yesterday, before I started tinkering, I could boot into XP, 8.04 or 8.10 at will.

I used Gparted to shrink and move the two Linux partitions, to free up some disk space.

I installed Fedora 10 (just out of curiosity); I could then only boot F10 or Other, and Other was XP.  No sign of the two Ubuntu instals in grub.

I deleted the F10 partitions in Gparted and got as far as grub> on re-booting.

I used a SuperGrubDisk to fix grub, and got to a state where I could boot to XP or 8.04, but not 8.10.

I deleted the 8.10 partition and re-installed 8.10.  I can now boot into either of the Ubuntu  OSs but not XP.  I could not access the NTFS partition from Ubuntu.

In Gparted there is a warning next to the NTFS partition.  I tried to fix this with testdisk, and I can now access the files on the partition from Ubuntu but not boot into XP.

There is still a warning next to the NTFS partiton in Gparted, and the Information option tells me to run "chkdsk /f" and reboot TWICE.

Isn't chkdsk a Windows program?  If so, how do I run it as I can't boot into XP???  Can testdisk do this?[/INDENT]

Sorry that was a bit long, but any suggestions?

TIA

Andrew

---

### Post by TeXtonyx on 2008-12-01
You said you used Testdisk. Did you mean the rebuild boot sector
option that compares the backup boot sector to the current one?
You can try the first Repair option on the XP install cd, which
lets you do fixmbr, fixboot, and bootcfg /rebuild in that order.

If that works you will have to reinstall grub because XP writes
to the MBR, if you already have grub installed to the MBR. You
had better make a backup if you have to try the second Repair
option from the XP install cd as you might lose some data.
Probably you will also have to reinstall grub in this scenario.

---

### Post by mdurham on 2008-12-01
AndrewS, I would recommend that you learn how Grub works. It would me so much easier than re-installing things and plonking about without knowing what you are doing. It would also be very satisfying and fun for you too.
Grub isn't rocket science, it's really quite simple. Just type into Google search "how does Grub work" and I bet you'll get thousands of hits.
Cheers, Mike

---

### Post by JC Cheloven on 2008-12-01
> **AndrewS said:**
> Hi

I have a problem, in that I cannot boot my PC into XP - not something I do often nowadays, but something I do still need occasionally.  This is a bit long-winded, but the history to this is as follows...

Yesterday, before I started tinkering, I could boot into XP, 8.04 or 8.10 at will.

I used Gparted to shrink and move the two Linux partitions, to free up some disk space.
Moving partitions this way involves always a risk ... 

> I installed Fedora 10 (just out of curiosity); I could then only boot F10 or Other, and Other was XP.  No sign of the two Ubuntu instals in grub. 

--> Normal. Fedora's install isn't as smart as Ubuntu's. Usually it sets only for windoze.

> I deleted the F10 partitions in Gparted and got as far as grub> on re-booting.
--> Again normal. 

> I used a SuperGrubDisk to fix grub, and got to a state where I could boot to XP or 8.04, but not 8.10.
--> Most likely you installed 8.10 after 8.04, and SuperGrub (or you using it) picked the grub files from 8.04, from a time when 8.10 didn't exist on your computer. So no surprise in that no entry for 8.10 does appear.

> I deleted the 8.10 partition and re-installed 8.10.  I can now boot into either of the Ubuntu  OSs but not XP.  I could not access the NTFS partition from Ubuntu.
At this point, Ubuntu's 8.10 installer should have identified your xp OS and set an entry for it. If it didn't, I'm afraid something weird happened with the xp partition. Perhaps you didn't properly unmount the partition before, when done accesing it from ubuntu, or perhaps it is something related to supergrub and the removal of a partition at a later time.

The rest of your post sums up in that you can't boot from xp. As far as I can remember (not sure), Fedora installer makes a boot partition by default, which is perhaps over there. To be honest, I don't know exactly what is happening, but I'd try the following in the lack of better ideas:

1º.- Boot from xp install disk, launch a recovery console and type "fixmbr". Exit and reboot. This is supposed to repair the windows bootloader (which doesn't matter really), and hopefully put your master boot record in a recognizable state. You should boot into xp. If you don't you can continue trying the following anyway.

2º.- Boot from ubuntu live cd. In a terminal type "sudo grub", then "find /boot/grub/stage1".  The answer will be one or more partitions in the format hd?,? . You will choose the one of your 8.04 partition, which probably has an entry for xp (you can confirm that having a look on the /boot/grub/menu.lst file on that partition). I guess in your case is likely to be (hd0,1). Then type "root (hd0,1)", or whatever the 8.04 partition is. Then type "setup (hd0)". This would place you at a point where you can boot from xp and 8.04 using grub.

3º.- Copy the entry for ubuntu 8.10 in the /boot/grub/menu.lst file of the 8.10 partition, to the end of the file of the same name on the 8.04 partition. I guess you'll find out where to do it, as the file has a lot of annotations.

If everything is alright, you should be able to boot from xp, 8.04 and 8.10 again. The boot files are now in the 8.04 partition.

An advice for the future: Partition your disk once, before installing anything. If you plan to try distros often, set one or more small partitions for that (about 6 Gb will do). Is better to have 6Gb of unused HD space than moving partitions around.

Greetings
______________

---

### Post by AndrewS on 2008-12-02
OK, all fixed, although it took longer than it should.

Many thanks to JC for the suggestions about how to sort out the menu.lst file - in the end I simply added the entry for XP to the file in the 8.10 partition, which gave me the full range of options, but not a bootable XP partition.

I followed the suggestions from TeXtonyx - boot from XP installation disc, run fixmbr, fixboot and bootcfg /rebuild to get a bootable XP.  Then got grub back and working.

So, a big thank you to JC and TexTonyx.

Mike - I take your point, and I've actually read the Grub manual and a couple of tutorials I came across from your suggested Google search.  I feel I now have a much better understanding of bootloaders and grub, and as you say, it's not rocket science.  However, if I hadn't "plonked about" in a state of relative ignorance, I'd never have broken the system and wouldn't have learnt all I have...  And a few pointers in addition to your suggestions to find out what I'm doing would have been appreciated...

Andrew

---

### Post by mdurham on 2008-12-02
> **AndrewS said:**
> 
Mike - I take your point, and I've actually read the Grub manual and a couple of tutorials I came across from your suggested Google search.  I feel I now have a much better understanding of bootloaders and grub, and as you say, it's not rocket science.  However, if I hadn't "plonked about" in a state of relative ignorance, I'd never have broken the system and wouldn't have learnt all I have...  And a few pointers in addition to your suggestions to find out what I'm doing would have been appreciated...

Andrew
That's great that you got it fixed AndrewS. I would say that a lot of us have done similar things in the past, I know I have, and I always regreted afterwards that I didn't take the time to study the problem first. The reason I didn't supply any pointers was because there has been a ton of stuff already written on the subject, most of which would be better than any effort that I might attempt.
Cheers, Mike

PS
FWIW, I have a separate partition with my Home and the /boot/grub directory, so that if I install a test distro that overwrites the MBR I can always reinstall my 'normal' Grub menu that's on the separate partition. Hope that makes sense!

---

### Post by JC Cheloven on 2008-12-02
> **AndrewS said:**
> 
So, a big thank you to JC and TexTonyx.

Andrew

You're welcome.
Everyone here made a mess of her/his system sometimes, and learned things each time :-)

---

