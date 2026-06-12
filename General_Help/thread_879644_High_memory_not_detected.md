---
title: "High memory not detected"
date: 2008-08-04
forum: General Help
---

### Post by editrix on 2008-08-04
I've just installed Dapper on an old Toshiba laptop, and it's running slow as molasses in January.

When I boot up, I get a message from Grub about memory, but it goes by too fast to read. However, dmesg tells me **0MB HIGHMEM available** and Kinfocenter says I have only 128MB ram, when I know I have 256.

I've googled around and found the **0MB HIGHMEM available** message in a lot of posts, but I haven't found anything that tells me how to make that other 128MB available.

Thanks in advance for any help.

---

### Post by coffeecat on 2008-08-04
Have you checked in your BIOS settings? Perhaps something needs changing in there. And you will also be able to see how much RAM the BIOS is detecting. If it is only detecting 128 of your 256MB, then the operating system won't see it either.

---

### Post by editrix on 2008-08-04
> **coffeecat said:**
> Have you checked in your BIOS settings?

Nope, because it never ocurred to me. Thanks for this.

Now, let's hope I can figure the bios out :-(

---

