---
title: "Can't Install to New Dell Laptop"
date: 2012-01-13
forum: Hardware
---

### Post by Tk007LwZFJW5ej on 2012-01-13
I have a brand new Dell XPS-17 laptop. I want to delete Windows 7 and install Xubuntu x64. I burned an install disk to DVD, but the install always hangs. I also burned an Ubuntu install disk and it hung at the same place. I haven't scrolled all the way up on the screen it hangs on, but some messages that stood out to me near the bottom: 

Please append a correct "root=" boot option.
Kernel panic - not syncing VFS: Unable to mount root fs on unknown block (8,1)

Pid 1, comm swapper not tainted 

Call trace
panic
mount_block_root
mount_root
etc.

I read on the ubuntu site about some problems with dell computers, and so I added hw-detect/start_pcmcia=false to the boot options, but it didn't seem to do much, but I did notice this in the output, which wasn't there before:

cannot open root device "(null)" or unknown block(8,1)

I have a 1 TB hard drive that came partitioned in half: OS C: and Local Disk D: Could that be what is causing the install to choke? I also read somewhere that the problem may disappear if I install x86, but I really want an x64 OS.

---

### Post by wolfen69 on 2012-01-13
Is there an option in the bios to disable the nvidia graphics?

---

### Post by 2F4U on 2012-01-14
Is that the default liveCD you are trying to install? If yes, why did you burn it on a dvd, it should fit on a cd?
Did you verify the checksum of the downloaded iso file? It looks to me as if the install medium is damaged. This may be due to a bad download or a badly burned image.

---

### Post by Tk007LwZFJW5ej on 2012-01-14
Thanks for the responses. I burned the alternate Xubuntu CD; it hung the first time, then I was able to install from it the second time. Strange.

---

