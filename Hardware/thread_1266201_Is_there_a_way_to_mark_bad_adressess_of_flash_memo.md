---
title: "Is there a way to mark bad adressess of flash memory?"
date: 2009-09-14
forum: Hardware
---

### Post by richterlevania3 on 2009-09-14
Hi,

I have a 16Gb pen-drive. Every files I copy to it gets corrupted. I could buy another one, but I'd like to fix this one. I know there is a workaround to use bad RAM using Memtest86 to find the malfunctioning adressess and BadRAM to mark them at boot time, so the OS doesn't use them. I googled everywhere, but couldn't find something like that for flash memory.

Anyone knows a workaround for this?

Thanks in advance.

---

### Post by tgalati4 on 2009-09-14
badblocks

or

sudo fdisk -l

sudo fsck -c /dev/sde  (change sde to what your flash drive actually shows up as in previous command)

---

### Post by richterlevania3 on 2009-09-14
Great! I'm running badblocks right now. It will take a time, if it works I will mark this thread as "solved".

Also, that fsck command does the same as badblocks?

Thank you.

---

### Post by richterlevania3 on 2009-09-15
Well, actually the badblocks program runs for about one hour and says that my pendrive has more than 800000 bad blocks. But when I try to mount it on windows, it says it need to be formatted. After it's formatted, I can access it normally, but it keeps corrupting my files. I ran the test three times, with the same results. I believe it is finding the bad blocks, but is not marking them.

The command I'm using: badblocks -svfw

Any clues?

Thanks in advance.

---

### Post by Pianoman72 on 2009-09-15
Try splitting it into 2 partitions and see if both partitions cause problems.  If so, the bad blocks (cells) must be spread out all over, and I wouldn't bother trying to save it.

If they are isolated to one area of the stick you could always bookmark that area with an unformatted partition.

---

