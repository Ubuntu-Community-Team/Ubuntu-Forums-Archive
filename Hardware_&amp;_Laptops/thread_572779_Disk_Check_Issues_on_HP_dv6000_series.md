---
title: "Disk Check Issues on HP dv6000 series"
date: 2007-10-10
forum: Hardware &amp; Laptops
---

### Post by hun7er on 2007-10-10
I've been running Ubuntu on my recently-purchased AMD-powered HP notebook. The filesystem has reached its 26th mount, but the system refuses to complete the check. Other than this, I have had no significant problems with the operating system. 

If anyone can help, I would really appreciate it. Any more information is valuable. I am not new to Linux, but I am not an expert, either.

Specs:

AMD Turion 64 x2 Processor
2 GB ram
Nvidia graphics card
Ubuntu 7.04 32-bit

I will be happy to provide any other information that I may have omitted. Just ask. Thanks again

---

### Post by cubeist on 2007-10-11
I have the same problem... as do most hp users... very frustrating indeed.

The solution is to boot in via the live cd and run fsck manually.  FSCK is a file system consistency check and is important to maintain long-term disk health.

to run fsck from the live cd, open the terminal and run e2fsck.  I can't remember the options required, you'll have to check the man page for that.

post back if you need further instructions

also, this link helps change the frequency required for fsck... I have mine set at 50 because I turn my laptop off more than once a day

[http://ubuntuforums.org/showthread.php?t=300477](http://ubuntuforums.org/showthread.php?t=300477)

---

### Post by hun7er on 2007-10-11
I feel stupid, but I can't figure out how to even get it to find my drive when I boot under the live cd. Does the Live CD version have to be the same as the version installed (ex. 32- vs. 64-bit?) If not, could you tell me what options I need to get it to work?

---

### Post by cubeist on 2007-10-11
well you have to know which file system you want to run fdisk on in your system, for example mine is /dev/sda3 (you can find this in the terminal by typing fdisk -l)

so here are the instructions ... I am going from memory at the moment

boot using a live cd (shouldn't matter if it is 32 or 64bit)
once booted open the terminal
find the filesystem (fdisk -l)
type "man e2fsck" and that will give you descriptions of the commands to run. For me,  I think the options I use are -v (for verbose...tells you what it is doing as it runs) and -f (I have to force it to run). So, the final command will be something like:
"sudo e2fsck -f -v /dev/xxxx" where you replace the x's with your filesystem (mine is sda3, yours may be hda1 or something like that)

BUT, to ensure you are using the correct commands for your system first run man e2fsck

Remember, never ever run e2fsck from a mounted file system or you can ruin your system!  Hence the need to boot via a live cd!

I hope this helps...

---

