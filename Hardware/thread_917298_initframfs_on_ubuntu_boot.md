---
title: "initframfs on ubuntu boot"
date: 2008-09-11
forum: Hardware
---

### Post by andtsoreyu on 2008-09-11
I have been a ubuntu user for a couple of years now and have never come across this issue before.  I am using the amd64 version of ubuntu on my Dell M1210 laptop.  I installed Ubuntu inside my windows partition (looks like an application in my Add/Remove Apps list).

ubuntu worked fine for a while and all of a sudden is giving me a lot of issues.  Ubuntu Installed some updates, and then did not shut down cleanly (because my laptop ran out of battery).  Now everytime I go to boot my ubuntu OS I just get dumped into a shell (BusyBox / InitramFS command line).

I have tried going into windows, and running 
```
chkdsk c: /f
```

and doing a clean shutdown of windows, which seemed to work for most people.  I have also tried to use the commands

```
modprobe ide-core
```

from the initramfs command line, which again seemed to work for most people but not me.  Actually before I can the mod-probe command I was getting a root.dsk not found shown above (previous) to the BusyBox / Initramfs.  After I ran modprobe ide-core I do not get this error anymore but I still get dumped into the command line.


Kind of stuck here and do not know what to do.  I have herd that some people I tried booting into an old kernel but my issue is I do not know which ones are installed on my machine because they are not in the grub list.

HELP!

---

