---
title: "Lost 1 TB of data, in need of expert help :("
date: 2008-07-14
forum: General Help
---

### Post by shemhamforash on 2008-07-14
Hi all,

Last Friday the worst imaginable thing happend to me: I accidently formatted my 1 TB external harddisk. Now, that isn't a that big problem if the filesystem was fat and formatten to fat, en ntfs formatted to ntfs, etc etc. But the disk was NTFS, and I formatted it to ext3. Just with the command mkefs.ext3.. 

I tried some tools and recovery programs, but not one of them worked, bc of the fact that the file were stored as a NTFS filesystem, en the HD is now the ext3 filesystem.

I hope that anyone here has any experience on this matter or tips for me. The data is really important for me, because there were a lot of photo's of my father who passed away bc of cancer a few days ago, and lot's of other data important to me :(. I know that i should've made a backup, but the irony is that I bought a second HD to store the pictures and data the day before this happend :@..

Please help me.. If this doens't work my next step is to call an expert recovery center or something, hope they can recover something.

What I already did is setting the bootsector to NTFS, to see if that worked, but it didn't.

---

### Post by ibuclaw on 2008-07-14
There is a piece of software called testdisk that is in the Hardy repos.
It claims to have the ability to recovery lost partitions. Although, as of yet. I haven't had the need to try it out.
```
sudo apt-get install testdisk
```

then run
```
sudo testdisk
```
And select your Terrabyte Harddrive.

Proceed wisely, I recommend that you tell the program to restore all recovered data on another partition (if that option is available), else the data that the program is trying to recovery gets overwritten in the process.
I know this is true with photorec (similiar to teskdisk, but photorec recovers individual files). But whether or not the option comes with testdisk is not known to me.

Regards
Iain

---

### Post by bodhi.zazen on 2008-07-14
good place to start : [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery) 

To be honest, with 1 Tb data you will need a large hard drive for recovery -> take it to a professional ?

---

