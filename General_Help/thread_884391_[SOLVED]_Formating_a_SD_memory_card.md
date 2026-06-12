---
title: "[SOLVED] Formating a SD memory card"
date: 2008-08-08
forum: General Help
---

### Post by tinny on 2008-08-08
Hello

I want to format a 4GB SD memory card that I have. What is the best way to do this?

1. What is the best file system to use? FAT16? or EXT2? (ive read somewhere that you should use FAT16 for SD memory)
2. What is the best formating utility?

Thanks lot! :)

EDIT: Im thinking about using GParted as the formating utility and the FAT16 file system. Is this correct?

---

### Post by dcstar on 2008-08-09
> **tinny said:**
> Hello

I want to format a 4GB SD memory card that I have. What is the best way to do this?

1. What is the best file system to use? FAT16? or EXT2? (ive read somewhere that you should use FAT16 for SD memory)
2. What is the best formating utility?

Thanks lot! :)

EDIT: Im thinking about using GParted as the formating utility and the FAT16 file system. Is this correct?

It totally depends on what you actually want to use the card for.

---

### Post by tinny on 2008-08-09
> **dcstar said:**
> It totally depends on what you actually want to use the card for.

Thanks for the reply.

(Im using this card on a Asus eee PC)

I want to use the card to run a couple of Java applications from.

E.g.

I want to install Eclipse and NetBeans IDE's on the card.

EDIT: Because im using the SD card for running applications would it be best to use a non journaling file system like ext2?

---

### Post by mb_webguy on 2008-08-09
Using FAT16 or FAT32 would give you greater flexibility in transferring the card to other computers and devices.  If you aren't planning on moving the card to other computers or devices, it doesn't much matter what file system you use, although using ext2, ext3, or ReiserFS would have some advantages in a Linux system, such as allowing you to use Linux file permissions.  Since this is a small storage device with limited space, you probably don't want to use a journaling file system, so I'd suggest ext2.

---

### Post by MobiusNZ on 2008-08-09
General thoughts to bear in mind:

If you want it to be compatible with all other OS's, chose FAT32.
If you are only using it with *nix, remember that flash drives have a limited write life... its pretty big, but using a journaled filesystem will decrease it's lifespan - hence, choose ext2 instead of ext3.

---

### Post by tinny on 2008-08-09
Thanks for those replies MobiusNZ and mb_webguy.

The flash write limitation is something that im aware of, so was very keen to ask the question here.

I only plan to use this card on my Asus eee PC running Ubuntu.

So the solution for me is to use GParted and the ext2 file system.

---

