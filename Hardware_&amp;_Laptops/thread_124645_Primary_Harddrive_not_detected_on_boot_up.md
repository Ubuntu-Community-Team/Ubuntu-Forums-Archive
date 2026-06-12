---
title: "Primary Harddrive not detected on boot up"
date: 2006-02-01
forum: Hardware &amp; Laptops
---

### Post by moothegoldencalf on 2006-02-01
Hi,
I'm having two problems that I suspect might be related.
1. On boot up my primary hard drive is not detected and then when I get to the boot setup screen I can hit f1 and it will detect the drive and boot up.
I checked the bios and the jumper settings and everything is set correctly at this point am a bit baffled.


2, My second drive which is fat32 is not detected at all in linux- when I use fdisk -l it doesn't come up, but before I installed Ubuntu, windows detected it fine..
Thanks for the hlep!
-Andrew

---

### Post by moothegoldencalf on 2006-02-02
I guess that I should add that before I reformatted I had a dual boot system with ubuntu and windows. Which worked fine and before that Redhat with windows and way back just windows which worked and was the same setup. 
I think this is a linux problem and not a harddrive problem.
Any ideas?

Thanks,
-Andrew

---

### Post by jason.b.c on 2006-02-02
:) Hey somebody told me ( I forget the gentlemens screen name now )that your supposed to set your ubuntu drive as master and windows drive as slave ..  I hope that helps you!   I don't claim to be a computer genius (ha ha);)

---

### Post by moothegoldencalf on 2006-02-02
Thanks for your help.

I installed Ubuntu over windows. I just did the basic setup.Basically I had hd0 with Ubuntu and hd1 as fat 32 but just a backup.

I also just pulled my second drive just to see what would happen- nothing changed. I also tossed in an old HD with windows and it booted up fine- so its not the cable/adaptors, ect. 

The drive is fine. The cpu doesn't recognize the drive on bootup and then at the bootup selection screen(f12) it will let me continue(f1) with the harddrive and it boots up fine.  It just adds like 2 min. to my boot up.

My instinct is that this is a partition/mbr problem but since I just did the default install with ubuntu I'm not sure where the problem is. 
Thanks for any help.

-Andrew

---

### Post by jason.b.c on 2006-02-02
Thanks for your help.

I installed Ubuntu over windows. I just did the basic setup.Basically I had hd0 with Ubuntu and hd1 as fat 32 but just a backup.

I also just pulled my second drive just to see what would happen- nothing changed. I also tossed in an old HD with windows and it booted up fine- so its not the cable/adaptors, ect.

The drive is fine.  The cpu doesn't recognize the drive on bootup and then at the bootup selection screen(f12) it will let me continue(f1) with the harddrive and it boots up fine. It just adds like 2 min. to my boot up.

My instinct is that this is a partition/mbr problem but since I just did the default install with ubuntu I'm not sure where the problem is.
Thanks for any help.

-Andrew




allright so i've got a couple of questions for you,

so your saying that you installed ubuntu to your master drive ( over windows )
have you messed around much in you systems b.i.o.s in the attemped to AUTO detect your second ( slave ) drive ?

not real sure what you mean by( the cpu dosen't recognize the drive on boot up) but like i said before you should be able to auto detect it..

what i was told to do was to pull my windows drive , set it to slave and stick it back in.  next install a new hdd in the first slot( were your old master used to be) take that new one and set it to master ( and i'm preatty sure there's a way to assign a drive letter too) then install ubuntu on the new master drive, so now you've got ubuntu on (master) and windows on (slave) then from ubuntu you are supposed to use something called GRUB BOOTLOADER to set ubuntu as default o's    at least i think i'm right about that one !!   it's ok for someone to correct me if need be      


well i hope this helps a-bit!!:p

---

### Post by moothegoldencalf on 2006-02-02
Wow, it worked to do the master/slave thing. I was so convinced it was a MBR problem I didn't even think to double check that.
Thanks for your help!!!!!

You're right about grub by the way

Thanks again!

-Andrew

---

