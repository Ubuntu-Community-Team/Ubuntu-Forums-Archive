---
title: "Vista/Ubuntu - Partition strategy advice req'd"
date: 2008-12-25
forum: Installation &amp; Upgrades
---

### Post by OinkOink2 on 2008-12-25
Greets to the Ubuntu community,

I've Google'd phrases like "partition strategy Vista Ubuntu" but there seems to be a large lack of decent documentation on the best strategy to employ for this issue. But essentially I want to install Ubuntu (8.10) but keep my Vista installation.

Also, I recently fixed a dumb installation I'd done which has taken the best part of a full day [today] because I was too eager to install Linux, so I really don't want to make a repeat performance!

I have a 150GB HD in my laptop -
[COLOR="Indigo"][LIST]
[*]'C:\' which occupies 99.3GB with just 55.3GB occupied by Vista (25GB of that is my Documents (Music, Pictures, etc)) leaving around 40GB space on C:\. 
[*]The rest of the space on the disk 49.69GB of 'unallocated space.' 
[/LIST][/COLOR]Due to having spent today reinstalling Vista and restoring some backed up documents this is a fresh recovery and is very stripped of all the programs I used to have. But I'm quite liking the minimalistic installation really so I think I'll keep it that way.

My question is this. I'm looking for a _good partition strategy_. Ideally I would like to have my HD split like follows
[COLOR="Green"][LIST]
[*]30-35GB for Vista (which after the next point the math there will work out)
[*]A new volume for my Documents which are currently occupying 25GB of space on C:\
[*]A SWAP file for Vista
[/LIST][/COLOR]So this is how I'd like things to look for Vista. **For Ubuntu I'm unsure** and hopefully this is where you guys' input will come in handy! I'm a Linux newbie but keen to learn: as far as I understand it I'll need to create 4 partitions out of the remaining unallocated space for '[COLOR="SlateGray"]/boot[/COLOR]' '[COLOR="SlateGray"]/[/COLOR]' '[COLOR="SlateGray"]/usr[/COLOR]' and '[COLOR="SlateGray"]/swap[/COLOR]'...?

Bearing in mind that I would like my Documents partition to be Linux readable so I can cross-use the files in either OS, would that need to be formatted as [COLOR="SlateGray"]FAT32[/COLOR], [COLOR="SlateGray"]NTFS[/COLOR] or [COLOR="SlateGray"]Ext3[/COLOR]? I'm unsure!

Is it realistic to have this many volumes on one HD without it being a problem?

---

### Post by oilchangeguy on 2008-12-25
this may be of some help:
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

also i might suggest that when you do a google search, keep it simple. in your case something like dual boot vista and ubuntu partition size. many people would not include the word strategy in their search. just type key words. it does not have to be a sentence that even makes sense.
and you don't need a swap file for vista. windows already has this taken care of. it's called page file (in xp anyway) i hope you understand that all swap/page file is, is virtual ram. most modern computers will never use it. they have enough physical ram.

---

### Post by Vakman on 2008-12-25
[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)
Also may be of use to you.

---

### Post by oilchangeguy on 2008-12-25
and that 25gb of documents, and music and pics make sure you back it up BEFORE you attempt to install ubuntu.

---

### Post by OinkOink2 on 2008-12-25
Cheers guys.

---

