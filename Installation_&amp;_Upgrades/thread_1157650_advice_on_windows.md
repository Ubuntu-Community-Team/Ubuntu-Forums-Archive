---
title: "advice on windows"
date: 2009-05-12
forum: Installation &amp; Upgrades
---

### Post by Nighthawk4900 on 2009-05-12
So i have a dilemma with a nonbootable xp and ubuntu. 

I need the xp installation in one piece if possible. I can access all the files, so saving my data isnt a problem. I was wondering if i could do a clean install of windows on a brand new hard drive and then copy the whole original XP partition over the newly installed one and expect everything to work just like before?

or is there someway to do that? basically i want to save all the settings from the programs and stuff in XP instead of having to reinstall them all. 

thanks

---

### Post by lykwydchykyn on 2009-05-12
I guess it depends on why it's not bootable.  If XP is trashed, then it's not going to work because you'd be copying the trashed OS files.  If it's just a bootloader issue, then it might just work.

I've used the G4L CD a lot, though there might be friendlier options.  It has an option called "NTFSClone" which just copies the contents of an NTFS partition from one to another.  It could be used for what you describe.  You might be able to do NTFSclone from an Ubuntu liveCD as well, not sure.

It can be problematic at times, because of the way NTFS locates the boot partition.  I've had it fail on me maybe about 10% of the time.  But it seems like you've nothing to lose so go for it.

---

### Post by Dngrsone on 2009-05-12
You won't be able to import all your installed programs to a new Win installation and expect them to work.

What is the error you are getting?  Is it related to installing Ubuntu?

---

### Post by lindsay7 on 2009-05-13
We need to know a little more on why windows will not boot and what is going on with you system.  If the disk can be read, it might be possible to clone your windows installation with a program like Acronis Home Image. This would put your existing windows installation on a new drive and everything would work and be intact.

---

### Post by Nighthawk4900 on 2009-05-13
well, the XP installation is by no means trashed. [http://tinyempire.com/notes/ntldrismissing.htm](http://tinyempire.com/notes/ntldrismissing.htm) .. using the bootdisk from that site, i was able to successfully boot into my windows. everything was fine. i think when i installed ubuntu, the primary windows partition became a logical partition, and that is the reason it wont boot now. also for some reason, ubuntu/gparted/grub? all refer to that partition as /dev/sda5 which becomes (hd0,4)... and using that in menu.lst just causes the "starting up..." message with no actual starting up. i tried setting the boot flag to that partition in gparted... but still no luck. if it helps, gparted cant access the contents of that partition, though i am able to mount the partition and access all the files. how weird. 

what i was thinking was that if i do a fresh install of XP on that new drive, it will correctly write the MBR onto that disk... and then if i just copy the contents from the original ntfs partition to the new one through ubuntu (so as to not lock up the files...) the mbr should be pointing to the right place and everythign should be good as new rite?

---

### Post by lykwydchykyn on 2009-05-13
> **Nighthawk4900 said:**
> 
what i was thinking was that if i do a fresh install of XP on that new drive, it will correctly write the MBR onto that disk... and then if i just copy the contents from the original ntfs partition to the new one through ubuntu (so as to not lock up the files...) the mbr should be pointing to the right place and everythign should be good as new rite?

You never know 'til you try ;-)

Check out NTFSClone.  It's in the ntfsprogs package.  That should be a little more robust than just mounting and copying.

---

### Post by Nighthawk4900 on 2009-05-13
I guess ill try my way, and then use the NTFSclone tool..

also, what would be the ideal filesystem to use for the data partiton that is going to be shared between windows and linux? i heard writing to NTFS was "dangerous" with linux?

---

### Post by Dngrsone on 2009-05-13
> **Nighthawk4900 said:**
> 
also, what would be the ideal filesystem to use for the data partiton that is going to be shared between windows and linux? i heard writing to NTFS was "dangerous" with linux?

It used to be, but the NTFS-3G driver seems to be pretty stable (I haven't had any issues not caused by Windows itself).

---

### Post by Nighthawk4900 on 2009-05-14
just throwing an update on here....

i installed XP on my second disk. I then manually (no ntfsclone) copy/pasted the windows and progamfiles directories into the new installation via ubuntu... and lo and behold, it booted, and asked for my original password... and i tried a few programs, VLC player and adobe photoshop both loaded without a problem. im gonna put the original documents and settings directory back in also and we'll see how that works out

---

### Post by Nighthawk4900 on 2009-05-14
An update of an update says that everything works fine! i had to reapply some themes and stuff... but all the programs and my start menu... everything is back to the way it was.

so now... do i just change the grub menu.lst file with the HD mapping thing, that ive seen plenty of times before?

currently to boot either OS, i have to put that as my "first" disk via BIOS. whichever disk is first, that boots... editing to boot from grub shouldnt be very difficult, should it?

---

### Post by upchucky on 2009-05-14
Get Supergrub to set up/repair Grub here:

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

after you have downloaded and created the supergrub disk boot from it then use it to fix grub.

you must read the instructions carefully and understand them, google what you do not understand. You will not hurt anything with this but can get very confused if you do not understand what it does.

---

### Post by Nighthawk4900 on 2009-05-14
thank you my good sir! i have made a bootable CD... to be used if necessary...

for now, i just did the ole


```

title              Windows XP
root               (hd1,0)
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1
```

addition to my menu.lst and it worked! 


thanks EVERYONE for all your help!! =D

---

