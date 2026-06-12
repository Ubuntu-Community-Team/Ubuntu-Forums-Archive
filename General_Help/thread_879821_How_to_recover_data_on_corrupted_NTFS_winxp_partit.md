---
title: "How to recover data on corrupted NTFS winxp partition"
date: 2008-08-04
forum: General Help
---

### Post by l @ l o on 2008-08-04
Hello to everybody

anyone did succes to recovery data from ntfs winxp partition?

unfortunately i`ve done a big mistake with my hd laptop.

i use this laptop on office, and here unfortunately we are forced to use windows, anyway i`ve forget that previously i`ve installed kubuntu many and many windows format ago.

the problem is that from the disk manage option on winxp, i`ve tried to allocate space for a logical volume (that i suppose it was the spap partition of my kubuntu)

The problem is that now, once the mistake is done, i got the blue screen win error on all system where i connect the hd with my usb box.

I`ve tried many lice vd versions (knoppix,systemrescuecd,PDL etcetc) because on those live`s cd there is a nice tool called TESTDISK

with this tool, i can see the partition ntfs that i may recover all the data, the problem is that i can`t copy it.

-first i tried knoppix 5.1 live cd, but testdisk version 6.5 is too old and not have the copy option

-than i tried pdl and systemrescuecd, that have installed testdisk version 6.9 but when i list the files of my ntfs partition, i select the copy option but as destination copy directory it only allow me to save it on the path where i launched it (is a live cd, so i cant write on a live cd, volume is only in read mode)

-so, i tried the lastest knoppix version 5.3 on DVD, but this knoppix version have testdisk 6.8 version, that seems have a damned bug, when i try to list the files of the partition, the program exit the shell!!!!

-at this point, i`ve installed ubuntu on a friend pc, but when i go to install the application (by launching sudo apt-get install testdisk, unfortunately it install it the version 6.8!!!! that have this bug that exit the testdisk application when i try to list the files of my ntfs partition!!! :(


so, i need one linux distro that may run testdisk 6.9 or 6.10, where i can recover my data using testdisk, copying my files from ntfs partition to another partition of another hard disk that i have just buyed for recover my data.

somebody can help me please? :confused:

---

### Post by bijeeshvs on 2008-08-04
you can use test disk to rewrite the old partition table to the disk if it finds every file u owned previously, trying this could be better than trying to copy paste files....................

---

### Post by l @ l o on 2008-08-04
> **bijeeshvs said:**
> you can use test disk to rewrite the old partition table to the disk if it finds every file u owned previously, trying this could be better than trying to copy paste files....................

thanks for the tip, but i`m afraid to do another mistake, so before rewrite the partition table i want to copy all data before

---

### Post by caljohnsmith on 2008-08-04
I would give ["SystemRescueCD"]("http://www.sysresccd.org/") a try. Also, I think it has ["PhotoRec"]("http://www.cgsecurity.org"), which is supposed to be a great program for recovering files; although I've seen many recommendations for it, I haven't actually tried it myself.

---

### Post by l @ l o on 2008-08-04
> **caljohnsmith said:**
> I would give ["SystemRescueCD"]("http://www.sysresccd.org/") a try. Also, I think it has ["PhotoRec"]("http://www.cgsecurity.org"), which is supposed to be a great program for recovering files; although I've seen many recommendations for it, I haven't actually tried it myself.

as i wrote, systemrescuecd have testdisk version 6.9 that is ok but as livecd, i cant wrote thata to another hd even mount it.

PhotoRece is usually used for recover data from pendrives, photocamera's sd memory cards etc.

anyway, thanks for the reply

---

### Post by l @ l o on 2008-08-04
i got an idea.

i'm downloading lastest mandriva version.

i can see from testdisk download page

[http://www.cgsecurity.org/wiki/TestDisk_Download](http://www.cgsecurity.org/wiki/TestDisk_Download)

that there's also the .rpm package version.

i will try it with mandriva and i will let all of you know.

---

### Post by l @ l o on 2008-08-04
> **l @ l o said:**
> i got an idea.

I'm downloading lastest mandriva version.

I can see from testdisk download page

[http://www.cgsecurity.org/wiki/testdisk_download](http://www.cgsecurity.org/wiki/testdisk_download)

that there's also the .rpm package version.

I will try it with mandriva and i will let all of you know.

i was right!

Problem solved with last version of mandriva!

I restore all my data!!!!!! :d

---

