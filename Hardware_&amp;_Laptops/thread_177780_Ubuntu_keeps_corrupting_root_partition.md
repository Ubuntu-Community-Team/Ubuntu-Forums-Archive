---
title: "Ubuntu keeps corrupting root partition?"
date: 2006-05-16
forum: Hardware &amp; Laptops
---

### Post by mattlach on 2006-05-16
Hi,

It's happened three times thus far.  First time was the same day I first installed ubuntu, next time was a few weeks later, and now again a few weeks after that.

Ubuntu seems to somehow be corrupting my root partition (ext3) beyond what fsck can correct, so when I try to boot, it will fail on boot with a forced fsck that fails with the error message: "Buffer IO error on drive hdb1".

The hard drive and controllers work fine under other linux distributions (notably Gentoo that I just got rid of) but Ubuntu seems to be causing trouble.  

The partition - once reformatted - works perfectly again (until ubuntu does something to it and corrupts it again, which seems to happen once every 3 days to 3 weeks or so)

Does anyone have any ideas what might be causing this?

This is on an Athlon 64 on a Nforce 3 mobo running the AMD 64 release of Breezy.

Appreciate any assistance!

--Matt

---

### Post by hw-tph on 2006-05-17
I suggest first installing smartmontools and checking the health of your drives. **sudo smartctl -t long /dev/hda** would run a long selftest (usually takes about an hour, but it varies) on the /dev/hda disk. You can read [this LJ article](http://www.linuxjournal.com/article/6983) for a full tutorial on smartmontools.


Håkan

---

### Post by mattlach on 2006-05-17
[QUOTE=hw-tph]I suggest first installing smartmontools and checking the health of your drives. **sudo smartctl -t long /dev/hda** would run a long selftest (usually takes about an hour, but it varies) on the /dev/hda disk. You can read [this LJ article](http://www.linuxjournal.com/article/6983) for a full tutorial on smartmontools.


Håkan[/QUOTE]

Not a bad idea to check - just in case - but I doubt the hardware is the problem, as it works perfectly fine with other operating systems and even linux distributions on the same partition location on the same drive...

I currently can't boot it though.  Do you know of any livecd that includes smartmontools?   Maybe knoppix? (knoppix.org doesnt seem to be detailed on what exactly the disk includes)

Thanks,
Matt

---

### Post by mattlach on 2006-05-19
Ok..  So I ran smartmontools on my HD with the -t long test, and then pulled the codes from the drive, and there were no logged errors.

Looks like the drive is in prime health (as I suspected)

Does anyone have any other suggestions?

Is there any other tool better at fixing ext3 partitions than fsck?  It would be nice to just fix the partition and not have to reinstall...

---

### Post by Sef on 2006-05-19
I am wondering if you had a bad install.  You could redownload and reinstall Breezy or wait a couple of weeks for Dapper to be stable, or download Dapper now.

If you would redownload, burn, and reinstall that will likely take care of your problems.

---

### Post by mattlach on 2006-05-19
[QUOTE=Sef]I am wondering if you had a bad install.  You could redownload and reinstall Breezy or wait a couple of weeks for Dapper to be stable, or download Dapper now.

If you would redownload, burn, and reinstall that will likely take care of your problems.[/QUOTE]


I don't think redownloading will do anything at all.   The MD5 hash checked out fine on the first download.  I could be wrong, but from my personal experience if a download is corrupt, it usually completely fails on either burning or install.   Never had a system failure months down the road depend on a faulty download...

I suspect the problem is that some kernel driver or package is of an older version in Breezy than what I used to use in Gentoo, and is not fully compatible with some aspect of my hardware.

It could be either something udev related, block device related, partition related, or maight even be related to power management and shutdown scripts.

It happened once when I first installed it.   I recinstalled it and it went away for months and now it just reocurred...

With a little luck the problem will disappear with Dapper, as it will have more recent packages.

When is the dapper release again?

It would be nice if the partition were fixable so I could use my current install of breezy until Dapper final gets released, but I guess if fsck can't fix it, nothing can?   Is that the general consensus?

It would be annoying to have to install again just for a couple of weeks...

If I were to install the non-stable release of Breezy, would it update to the stable release, or would I have to reinstall stable Dapper once it is released?

Thanks for your help :)

---

### Post by Sef on 2006-05-20
> When is the dapper release again?

1 June 2006.  Less than a fortnight away.

> If I were to install the non-stable release of Breezy, would it update to the stable release, or would I have to reinstall stable Dapper once it is released?

Since you are having problems with Breezy, I would do a clean install (reinstall) because updating may not get rid of the problem.

**Back up** your data before upgrading either way.

---

### Post by gamma on 2007-12-05
I'm on Ubuntu 7.10 and I'm having the similar issues as the thread poster. I didn't see any errors using smartctl so I'm stumped. I'm also on a laptop too and the machine is about 5 years old, so these errors are making me concerned about the safety of my data. Do you think it's just a bad install? I'm getting IO errors when trying to extract deb packages on my drive for a apt-get dist-upgrade. Removing the packages in question forced Ubuntu to redownload them and then they install fine.. Thoughts?

---

