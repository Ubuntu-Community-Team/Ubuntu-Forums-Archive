---
title: "Disk Check freezing"
date: 2009-05-02
forum: Hardware
---

### Post by Geoffbaker on 2009-05-02
Hi
on booting up I get a message saying routine disk check thencomputer freezes when at 48%. Nothing seems to get it past there but there is no error message. As a recent recruit from MS I would appreciate some help
Cheers
Geoff

---

### Post by Macchi on 2009-05-02
Hello Geoff,
Sad to read that you have that kind of trouble with your system.
A lot of hardware and software errors could cause the same symptoms, thus it would be good to exclude certain possibilities. 

Has the problem appeared from the beginning after your Ubuntu installation? Be sure to verify the checksum for the CD-image after download and before burning and installing the system. Burn at lower speeds and if possible verify the disk. Then you will know that the installation has been done from a reliable copy. This type of soft error may happen more often that we wish.

Which version and variant of Ubuntu are you using? There are some risks for bugs if you have Jaunty and decided to use the ext4 file system. It is not recommended for production machines yet.

I would also recommend you to run a memory check (at the grub menu upon start) and later also try to run a live-CD (or live-USB) on the system and check that it runs ok. You can also run a disk check from a live system.

Then there are other potential hardware problems, (hope it is not your case):  
A) Disk errors. If yu have a really bad disk error on the same disk that you are running the system then your entire system might have errors and any disk check is not reliable. Hard disk drives can be replaced.  

B) Memory errors. May happen quite often if you have the wrong settings on BIOS, or simply bad luck of having bad memory. Memory cards can often be replaced.

C) Bus or other hardware errors. In the simplest form there might be wrong settings in the BIOS that may cause the trouble. In the worst case there might be more permanent hardware problems. Obviously it can be more difficult to solve.

Hope this will give you some hints to solve the problem. 

Also remember to give more information about your system upon questions in the forum.

Keep in touch

---

