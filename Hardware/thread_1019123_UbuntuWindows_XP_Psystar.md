---
title: "Ubuntu/Windows XP Psystar"
date: 2008-12-22
forum: Hardware
---

### Post by Zahne on 2008-12-22
Hi,

This is my first post here. I'm very new to Linux just recently acquainted with Terminal. It reminds me of my old Atari XE, of course this software/hardware is vastly superior. 

Anyway, I was hoping to get an OpenLite with Ubuntu Linux unit by Psystar. I have a copy of Windows XP, would it be possible to partition the HDD and have both OSs running. My only real attraction to this computer by Psystar is that it's $299.99. 

I just want a very cheap and very basic computer that I can do this partition deal. I have a Mac for all my film work, but Linux and Windows offer certain film and other tools that are simply not available on Macs. They don't take up a lot of space (literally megabites), they don't require a lot of memory (1 gig will do) and they don't require a lot of horse power (1.8 ghz will do for sure). 

I heard good things about Asus hardware, but I've visited the site and can't seem to find any direct way to find pricing or ordering, but I've heard that have notbooks as low as $199.99? Is this true?

Any input would be much appreciated.

---

### Post by 2hot6ft2 on 2008-12-22
Sure, since you already have the linux on the pc you would use a livecd or the supergrubcd I'm sure someone will jump in with links or try google. anyway partition the drive from a livecd then install windows then you'll need to install a bootloader.

If using a linux livecd you would boot your Live CD, open a terminal (Applications > Accessories > Terminal) and do:

```
sudo grub
grub> root (hd0,0)
grub> setup (hd0)
grub> quit
```

And that's all it should take.

---

### Post by 2hot6ft2 on 2008-12-22
Of course I don't know which linux or bootlader the pc will have that you're talking about I assumed grub.

Most people doing a double boot install windows first then linux making a lot easier as opposed to the other way around like in your case.

As for the prices sorry I already threw the paper along with the sales ads out. But a $200 pc wouldn't surprise me these days.

---

