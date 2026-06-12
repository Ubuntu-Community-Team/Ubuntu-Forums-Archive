---
title: "Second Hard Drive Ubuntu 9.10"
date: 2009-10-27
forum: Hardware
---

### Post by mikeyd612 on 2009-10-27
The way my computer is set up is I have my original 200 gig hard drive, from when I built my computer, with just about nothing but the operating system on it. Then I have a secondary 1.5 terabyte hard drive that I use for storing media and other files. It mounted fine a few months ago with 9.04, but it randomly decided to stop grating me access to the disk. Being that 9.10 was just around the corner I decided to upgrade a little early and see if that would solve my problem. The new situation is that the drive is recognized in the "Places" menu automatically after the fresh install, but it still wont grant me access. When I try it gives me the error:

 > Unable to mount 1500 GB Filesystem
 Error mounting: mount exited with exit code 32: mount: wrong            fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

and in Palimpsest it says:
> Count of remapped sectors. When the hard drive
finds a read/write/verification error, it marks the
sector as "reallocated" and transfers data to a
special reserved area (spare area)

I searched a little online and a lot of the info was Window$ based. Thanks for any help.

---

### Post by amishphysicist on 2009-11-30
I got this and simply reformatted the drive with gparted. sudo apt-get install gparted, sudo gparted, you're done!  Hopefully there's nothing on the drive you need, otherwise, try pulling everything off on a windows box first.

---

### Post by mikeyd612 on 2009-12-04
Thanks for the reply. I still don't know what's wrong with it, and I probably will end up formatting it. Luckily there is nothing on it that I can't live without, but it's gonna be a major bummer.

---

### Post by coffeecat on 2009-12-04
When you say "randomly stopped granting you access", do you mean that sometimes it would and sometimes it wouldn't, or that it simply suddenly became inaccessible? If the latter that does sound like a filesystem corruption.

But before you reformat it, what filesystem is it? If it's NTFS and you can access it with Windows, try a 'chkdsk /R' from Windows.

---

