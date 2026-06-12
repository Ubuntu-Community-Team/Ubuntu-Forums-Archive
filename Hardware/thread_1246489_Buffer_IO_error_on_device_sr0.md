---
title: "Buffer I/O error on device sr0"
date: 2009-08-21
forum: Hardware
---

### Post by mattgyver83 on 2009-08-21
Let me see if i can best explain my dellima.  Long story short, it all started when i typed "sudo rm -rf /lib" in the wrong ssh session.

After this mishap I went to reinstall ubuntu from the live cd, *the same cd i did last install on this machine with*

The live cd opens up, lets me select 'Install Ubuntu' Then... i get this madness.

> 
[4.370442] IO APIC resources could not be allocated
[5.xxxxx]  end request: I/O error, dev sr0 sector 40
[5.57771] buffer I/O error on device sr0, logical block 5
[5.xxxxx]buffer I/O error on device sr0, logical block 6
[5.xxxxx]buffer I/O error on device sr0, logical block 7
[5.xxxxx]buffer I/O error on device sr0, logical block 8
[5.xxxxx]buffer I/O error on device sr0, logical block 9
[5.xxxxx]buffer I/O error on device sr0, logical block 10
[5.xxxxx]buffer I/O error on device sr0, logical block 11
[5.xxxxx]buffer I/O error on device sr0, logical block 12
[5.xxxxx]buffer I/O error on device sr0, logical block 13
create_floppy_devices[548] specified group "floppy" not found

[4.370442]end_request: I/O error, dev sr0 sector 40
starting system log daemon: syslogd, klogd


After this message the installer loads and I follow through prompts and I have gotten several errors "Kernel Panic, Must restart", "Unable to mount CD-Rom", "CD does not contain a valid 'release' file".

Ive been reading forums all day long and have tried a ton of things, the following.. all have failed.  

1.  Downloaded fresh copy, verified md5sums, burned cd, verified md5 - fail
2.  pressed f6, tryied with noacpi - fail
3.  pressed f6, tryied with all_generic_ide=1 - fail
4.  pressed f6, tryied with noacpi=off - fail
5.  Switched drives - fail
6.  Switched IDE cable - fail
7.  Took HDD out and formated drive, retried - fail

Anybody know what else I can try?? Oy vey!

---

### Post by hansdown on 2009-08-21
Hi mattgyver83.

Your CD may be scratched, etc.

Try burning a new one, and burn at the slowest possible speed.

---

### Post by mattgyver83 on 2009-08-22
Thanks for the reply.  I actually have done this and made 3 different copies, the slowest my burner can burn is at 16x, same problem with those as well :(

---

### Post by hansdown on 2009-08-22
Are you using rewritable disks?

---

### Post by PatrickVogeli on 2009-08-22
maybe your drive is starting to fail?? For two weeks I tried burning some dvd's, all failed and I didn't now why. After thinking about it, the disks looked and worked ok on other PC's, but wouldn't mount on mine. Changing the drive did the trick. Seems mine wasn't OK anymore.. I don't use it much and it has a year or so. I had bad luck I guess

---

### Post by mattgyver83 on 2009-08-22
Yes, i am using rewritable discs, and they are Sony discs there not just cheapo discs.  Just a side note i am not trying to re-write over any existing cds, these are all fresh burns.

As well this machine has 2 cd-rom drives and to test if it was a bad drive I switched the other drive to master and still had the same problem.

Whats puzzling is that I have other live cds that will work in the drives :\

---

### Post by hansdown on 2009-08-22
I've had some problems with CD+RW discs, but CD-RW usually work very well.

---

### Post by mattgyver83 on 2009-08-22
I have one copy on cd-rw, that was a reburn copy after i downloaded the image again.  The first cd I used (original) was just a cd-r, so are 2 other cds that I freshly burned.

Just to humour myself I went out and bought a brand new dvd/cdrom drive.  I will try these with this drive and see if they work, even try a dvd burn.

Ill keep posted, thanks for your comments.

---

### Post by mattgyver83 on 2009-08-22
Well, this can gladly be marked as solved.  The new drive works and the OS has been reinstalled.

I guess my drives were just beginning to fail, they are rather old.  If anyone is able to offer information as to why some CDs would work with these 2 drives until now that would be great, id like to answer that enigma.

Well, to all those who responded thanks a lot, and to every one else reading this.... moral of the story..   Check your SSH sessions at the door sudo rm -rf /lib = bad.

Until i break something else... fin.

---

### Post by hansdown on 2009-08-22
Glad you fixed it mattgyver83.

Your patience, and determination are admirable.

---

