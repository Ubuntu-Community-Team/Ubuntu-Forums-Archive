---
title: "Mount fakeraid in Ubuntu live cd"
date: 2008-11-27
forum: General Help
---

### Post by douirc on 2008-11-27
So I installed Ubuntu 8.1 on my ICH10R RAID 0 array using the alternate disk without any problem.  I had to run some memory testing software and had to temporarily disable raid to get it to run.  After re-enabling the array in BIOS, Ubuntu no longer loads.  I put the alternate cd back in and tried recovery mode, but I didn't get very far.

So, instead I put the 8.1 live cd in, installed dmraid and am now trying to figure out how to mount the raid array so I can copy what files I need and reinstall Ubuntu to start all over again.

Some information:

*ls /dev/mapper*
crw-rw---- 1 root root  10, 60 2008-11-27 05:19 control
brw-rw---- 1 root disk 254,  0 2008-11-27 05:19 isw_chahihcff_Volume0
brw-rw---- 1 root disk 254,  1 2008-11-27 05:19 isw_chahihcff_Volume01
brw-rw---- 1 root disk 254,  2 2008-11-27 05:19 isw_chahihcff_Volume05

isw_chahihcff_Volume0 is my RAID array and the one I want to mount

*sudo dmraid -r*
/dev/sdd: isw, "isw_chahihcff", GROUP, ok, 145226109 sectors, data@ 0
/dev/sdc: isw, "isw_chahihcff", GROUP, ok, 145226109 sectors, data@ 0
/dev/sdb: isw, "isw_chahihcff", GROUP, ok, 145226109 sectors, data@ 0
/dev/sda: isw, "isw_chahihcff", GROUP, ok, 145226109 sectors, data@ 0

not sure what this means...

*sudo dmraid -tay*
isw_chahihcff_Volume0: 0 580885504 striped 4 64 /dev/sda 0 /dev/sdb 0 /dev/sdc 0 /dev/sdd 0
isw_chahihcff_Volume01: 0 557278722 linear /dev/mapper/isw_chahihcff_Volume0 63
isw_chahihcff_Volume05: 0 23599422 linear /dev/mapper/isw_chahihcff_Volume0 557278848

again, not sure what all this means...


I'm not sure what to do next.  Again, I just want to access the files on the RAID so I can copy them off to my external hdd so I can reinstall Ubuntu and start over.

Thanks for the help!

---

### Post by douirc on 2008-11-27
btw...when I try to run the command *sudo mount /dev/mapper/isw_chahihcff_Volume0 /mount* I get the error:

mount: /dev/mapper/isw_chahihcff_Volume0 already mounted or /mount busy

I looked around for a solution to this problem but I haven't found a solution.  The directory was just created and I'm not in the directory when running the command, so the other option would be the array is already mounted, which I find hard to believe.

---

### Post by psusi on 2008-11-29
What exactly do you mean when you say "it won't boot"?  The raid array looks like it is working fine.  Your attempt to mount it failed because the directory you are trying to mount it in ( /mount ) does not exist.  Try /mnt instead, which should already exist.

---

