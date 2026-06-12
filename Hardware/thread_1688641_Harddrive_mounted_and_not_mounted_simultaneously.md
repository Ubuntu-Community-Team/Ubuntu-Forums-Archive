---
title: "Harddrive mounted and not mounted simultaneously"
date: 2011-02-15
forum: Hardware
---

### Post by quarrelinastraw on 2011-02-15
One of my hard drives on my desktop system appears to be in a quantum state.  

It fails to mount most of the time when I boot up or when I wake up from hibernation.  When it fails to mount, if I ls the directory where it should be mounted, I correctly see that nothing is there.  But if I fsck or try to mount it, I get an error saying that the drive is already mounted.  

mtab does not indicate the drive is mounted, and dmesg only gives 

 EXT4-fs (sda1): re-mounted. Opts: commit=0

several times (but I get a bunch of the same messages for my other drives that mount correctly.

Any ideas what could cause this?  Is it possibly a sign of hard drive failure?

---

