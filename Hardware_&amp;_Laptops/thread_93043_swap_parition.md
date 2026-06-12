---
title: "swap parition?"
date: 2005-11-21
forum: Hardware &amp; Laptops
---

### Post by megashake on 2005-11-21
Just wondering if anyone can offer advice on swap paritions? I have an AMD 64 notebook with 1GB(2x512MB DIMM) RAM running 32-bit breezy. If what I've read is true then I should have 2x1024MB swap partition although a former work colleague who introduced me to unbuntu and who is knows his linux stuff said that with that much RAM a swap wouldn't be needed at all and that for 512MB RAM a 512MB swap partition would be fine.

My current config inlcudes a 512 MB swap partition just to be safe, from what I've read a swap partition is needed but what size should it be? :rolleyes:

---

### Post by msr7x57 on 2005-11-21
[QUOTE=megashake]Just wondering if anyone can offer advice on swap paritions? I have an AMD 64 notebook with 1GB(2x512MB DIMM) RAM running 32-bit breezy. If what I've read is true then I should have 2x1024MB swap partition although a former work colleague who introduced me to unbuntu and who is knows his linux stuff said that with that much RAM a swap wouldn't be needed at all and that for 512MB RAM a 512MB swap partition would be fine.

My current config inlcudes a 512 MB swap partition just to be safe, from what I've read a swap partition is needed but what size should it be? :rolleyes:[/QUOTE]

it isn't absolutely necessary as far as I know, but it will be useful if you ever decide to "suspend to disk" From what I've read, they contents of memory get spewed out to disk (in the swap partition), and then reread at startup

I'm including part of my /boot/grub/menu.conf, which shows
[INDENT]root (hd0,2)
    kernel /boot/vmlinuz root=/dev/hda3 vga=0x317 selinux=0 resume=/dev/hda2 spl
ash=silent  showopts
    initrd /boot/initrd[/INDENT]

the "resume=/dev/hda2", which is my swap partition. To make this work, you would need something at least as large as your used memory, and likely as large as all your memory + some amount for overhead.

Hope this Helps

---

### Post by suRoot on 2005-11-21
I'm running Breezy on a thinkpad T40p & most of the stuff I read before installing said to set swap to 1.25 x RAM (1.25GB in my case).  This seems fine for me.  Suspend works just fine.  If you don't care about suspending, you can probably get away with 512MB.

---

### Post by megashake on 2005-11-22
Can you explain what ""suspend to disk" means? ;)

---

### Post by az on 2005-11-22
[QUOTE=megashake]Can you explain what ""suspend to disk" means? ;)[/QUOTE]
You can put your computer to sleep.  Some hardware supports suspending to ram which is just turning everything off but keeping a small current flowing to the ram so that everytying in ram is intact.  You boot up in ten seconds and you are put back to the spot you were when you suspended to ram.

Suspend to disk (hibernation) is a feature where the contents of your ram is stored on the disk so that you boot up normally, but the boot process looks to see if you have a former session stored.  If so, it loads it back into ram and you are up and running.

In this case, the place where it will write the contents of your ram is your swap space.  That is why it has to be slightly bigger than your physical memory.

Otherwise, discussions on how big to make your swap are the stuff of religious wars.  Swapping is slow anyway.  If your copmuter slows down because you need more ram, a bigger swap will not help.  Get more ram.  Otherwise, forget  about it.

---

