---
title: "Installing Hardy onto a 16gb flash drive"
date: 2009-04-12
forum: Installation &amp; Upgrades
---

### Post by n.chau on 2009-04-12
My question is, can it be done? The only other Ubuntu install I've done is onto a 4gb sandisk drive, which worked flawlessly might I add. That is, until I tried updating to firefox 3.

Point is, I have tried installing with manual partitions (as i did with my sandisk). I have tried it with

-40mb PRIMARY  /boot  ext3
-7168mb PRIMARY  /  ext3
-1536 LOGICAL  /swap

I have tried it with varying sizes of root ranging from 3.5gb to 10gb. The install goes great but everytime I restart, I get "grub error 22: partition does not exist". I hit enter, and choose it again, this time i get "grub error 18: the selected cylinders exceed the maximum supported by the bios".  The same thing happens when I go to boot options and choose recovery or memtest.

Everything was setup the same way as my 4gb stick except I've tripled the swap size and doubled the size of root. Has anyone else run into this problem or know how to fix it?

Thanks,
n.chau

EDIT!!!
I'm currently trying the guided install I'll post an update tomorrow night after I've check it out. The reason I've always done manual is that I want the rest of my drive free for a fat32 partition which allows me to still use the drive as a thumb drive and also makes transferring files to and from windows a lot easier (I'm a student and as such, my studies sometimes require windows based apps).

Also, GRUB was always installed to /dev/sdb, which is the flash drive.

---

### Post by ispyamoose on 2009-04-12
Have you tried using Wubi to install it?

---

### Post by miegiel on 2009-04-12
When I did this on my 40GB mp3 player I removed the hard disk to make sure grub would be installed on the mp3 players disk and not somehow land on my hard disk.

You also need to be aware that flash disk bits (compared to real disks of the spinning type) can be written to limited amount of times. This "limit" goes into the tens of thousands, so for storage purposes it's not such a big deal. But is you use it as a root of your linux (or any other OS) certain sectors will be written to a lot. For example where the /tmp data is written, like cached web browser files. This significantly reduces the life of you flash drive if you use it this way daily for months. If it's just to test and get familiar with ubuntu for a short period you need not worry about it to much.

---

### Post by n.chau on 2009-04-13
1. Isn't Wubi for installing through windoz? I tried installing it direct from live cd.

2. I never actually took into account the life of the flash drive. The thing is, I do a lot of computer work all over (I'm the IT guy for my family and friends). It's kinda stoopid to carry my laptop, my external, my cd album, etc everywhere I go when they have at least two computers in the house. A flash drive is just simpler. Besides, I picked up this drive for $16, $1/GB? that's a steal. And it's not the really cheap ones either. But drive life is prolly something to think about.

But for now, how would I make this work? I tried the guided install using the whole drive but it still wouldn't work. Would it really make a difference if I took the hard drive out? I already set grub to install to /dev/sdb.

I also have a 20gb external drive. One of those passport cases that take a 2.5" SATA. Ideally, I would get ubuntu installed one that, but I tried it once and had the same errors as the flash drive. Also, being an external drive, it takes up 2 usb ports to provide adequate power for the drive. Although I do have a powered USB hub that I COULD carry around with me, and isn't a problem if I'm using it at home.

---

### Post by n.chau on 2009-04-14
okay so I got ubuntu installed. I actually took the my laptop's hardrive out, put the 20gb in, installed hardy and then put the drive back into the enclosure. I got it to boot though USB. Everything was working very well. I got openoffice, java, frostwire and firefox 3 installed. as soon as I restarted though, it hung right after I sign in. I just get the background and nothing else.

Help please?
n.chau

---

### Post by miegiel on 2009-04-21
> **n.chau said:**
> ... as soon as I restarted though, it hung right after I sign in. I just get the background and nothing else.

I suspect it's a kind of problem you could get doing a normal installation too. Since it happens right after logging in I think it's got something to do with (something in) your home directory. I've no idea what though, if you still haven't solved it you could try asking in a new thread.

---

