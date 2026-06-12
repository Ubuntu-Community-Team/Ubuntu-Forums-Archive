---
title: "Drive(s) not recognized (?)"
date: 2008-11-10
forum: General Help
---

### Post by Curieux on 2008-11-10
Hi!

I installed Wubi under Vista 32 bits, but at reboot, Ubuntu does not start.
It seems there is a problem with the disk C.
I attached a screen shot.

I tried several things:
1. Installing files on external USB HD.
2. Installing files on internal SATA HD (disk C).
3. Trying each choice for Wubi/Ubuntu boot.
4. Trying options on configuration boot file, adding to "boot": "vga=771" , "noapic", "nolapic", "irqpoll", and "all_generic_ide", separated *or* mixed.

Nothing work. Each time, in graphic mode it freezes, and in text mode it hangs after a "Kernel panic".

But booting Ubuntu CD normally *does* work (I mean a real CD). So it should not be a problem with Ubuntu itself.

I have a laptop, a HP 6622ef. Its bios does not have ACPI or any advanced options.

Any suggestions ?  :)
Thanks.

---

### Post by ago on 2008-11-10
Boot in verbose mode
Can you access the command line at all?
If so look into /casper.log

---

### Post by Curieux on 2008-11-12
> Boot in verbose mode
Can you access the command line at all?

No, all of the 5 boot options freeze in a kernel panic. So I have no command line available.

I presume the only way to access a log file (if any) should be to boot a real Ubuntu CD (that works, I tried) and mount the file "*/media/disk/ubuntu/disks/root.disk*" as a drive. I don't know enough Linux to do that.

EDIT:
I tried Explore2fs under Vista, but it says "*Error: could not find valid Superblock*". I guess the virtual partition is not formated yet.

And I saw no log files in "*c:\ubuntu\.....*".

---

