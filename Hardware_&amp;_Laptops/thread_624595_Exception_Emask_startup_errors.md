---
title: "Exception Emask startup errors"
date: 2007-11-27
forum: Hardware &amp; Laptops
---

### Post by willemmulder on 2007-11-27
Hi all!

I had 7.04 installed and everything worked flawlessly. However, after updating to 7.10, I suddenly get a few errors when I start up. 

Those errors look like this:
ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
ata1.00: (BMDMA stat 0x65)
ata1.00: cmd c8.......................... tag 0 cbd 0x0 data 4096 in

( a screenshot is here: [http://willem-mulder.nl/ubuntu/IMG_6819_kl.jpg](http://willem-mulder.nl/ubuntu/IMG_6819_kl.jpg) )

After a few of these errors, it boots but X doesn't work and I can't do anything but restart. 

If I boot into Win XP, I can access the ext3 filesystem just fine (by installing the ext2fs extension in windows) and read all the files I want. 
In other words: the HD, the partitions and files etc are still there and are in good condition!

could anybody please help??

---

### Post by rossjp on 2008-02-18
I just performed the recommended automatic web update from Ubuntu 7.04 to 7.10, and to my amazement and sheer joy, it worked.  Initially.  After loading the OS on several different occasions and checking things out and watching some videos from a CD, I had to load up XP to do some work (dual-boot machine, both OS's on the same disk).  After a forced restart because XP sucks, I tried to load up Gutsy again.  And it fails on the splash screen, roughly 25% of the way through the progress bar.  

The system loads all the files needed to boot OK, prepares restricted drivers OK, clock OK, networking OK, and so on, until it starts to check the root file system.  "/dev/sda6 contains a file system with errors, check forced."  Proceeds to check the file system, and I receive a number of errors similar to those listed by the previous poster.  And then finally: 

"Buffer I/O error on device sda6, logical block 2457779  Error reading block 2457779 (attempt to read block from filesystem resulted in short read) while getting next inode from scan.

/dev/sda6: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
fsck died with exit status 4"

i unmount /dev/sda6, and run 'fsck /dev/sda6', then get a rundown of all the same "exception Emask" errors, then a "Buffer I/O error on device sda6, logical block 2457779".  I'm asked if I want to ignore, I say 'no' and the fsck aborts with "Can't read next inode."

I've done some searching on these forums and google, and haven't really found much useful information.  I'm 99% sure this is not a hard drive failure, which is what most responders to these types of posts tend to offer as the reason.  What is particularly perplexing about this to me is that I ran 7.10 successfully on at least 5 separate occasions before this problem surfaced.  So does anyone have any other suggestions?  

More info available if you want or need it.

---

### Post by rossjp on 2008-02-19
I was able to "fix" this problem by allowing fsck to ignore all the errors it came across and force rewrites on all the bad blocks it found.  You can do this manually (I did for a while but after hitting 'Y' 50 times I got tired of it) or you can do it automatically by running fsck with the '-y' option on your device.  I still get a couple Exception Emask errors upon startup of Ubuntu, but the OS loads right after that instead of aborting.

---

