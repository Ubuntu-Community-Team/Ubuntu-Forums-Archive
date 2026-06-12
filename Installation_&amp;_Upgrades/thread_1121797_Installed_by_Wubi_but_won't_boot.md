---
title: "Installed by Wubi but won't boot"
date: 2009-04-10
forum: Installation &amp; Upgrades
---

### Post by Greenbean209 on 2009-04-10
I'm not new to ubuntu so I know quite a bit. But recently my old computer committed suicide so I switched to another one. My previous computer ran Ubuntu 8.04 on a Pentium3. My new one is gateway laptop with a pentium3. It runs windows 98. I tried installing ubuntu 8.10 through wubi and the install was successful. I rebooted my computer and tried to load ubuntu. It displayed some lines of "loading so and so" then strangely gave me a command prompt. It said Ubuntu@Ubuntu$. It is at this point that I don't know what to do. If it helps... A few lines displayed before the command prompt said something like " failure loading bash dev/null access denied" That is not exactly what it said but I'll see what I can do about getting the exact phrase.
any help is appreciated

---

### Post by ytsejam1138 on 2009-04-10
Is there more than one hard drive in this computer?  More specifically, are you running any kind of RAID?

---

### Post by alanwall on 2009-04-10
Ok, I have a ?
I installed wubi 8.10 and ubuntu 8.10
to the same partition-ntfs/30 gig-and ran wubi
and all went smooth.I rebooted/picked Ubuntu
and the drive light stayed on for a long time
so not sure if it did work. looking the the install
dir I can see the iso so am guessing that it was installing from the iso ? I also run Mandriva as dual boot and have several linux distros running under VmPlayer so am not a complete no0b.
Thanks for any help/ideas/fixes

---

### Post by Greenbean209 on 2009-04-11
> **ytsejam1138 said:**
> Is there more than one hard drive in this computer?  More specifically, are you running any kind of RAID?
I only have one HD and I don't know what a RAID is. But I'm pretty sure I don't have one because this computer is really fresh and I haven't done much at all to it yet.

---

### Post by buster on 2009-04-11
I had something quite similar. My secondary drive used to be Linux, and I had removed partitions and reformatted it from within XP to ntfs. Reformatted again from within XP.

Could never put my wubi on that drive, though it worked well from XP. Tried twice with 8.04.1 and 8.09. It didn't handle the file system well, claiming to see bits of reiserfs and dropping me to a prompt.

Ended up using the other drive which had always been ntfs and it worked perfectly.

---

