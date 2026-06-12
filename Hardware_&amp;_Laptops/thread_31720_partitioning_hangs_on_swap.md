---
title: "partitioning hangs on swap"
date: 2005-05-04
forum: Hardware &amp; Laptops
---

### Post by paxmark on 2005-05-04
Sorry about the cross post, no answers on install to date.

Hey,

I got KUbuntu up and loved it on the 20 gb hard drive on my AMD k2-350.  I decided to take plunge and get rid of Mandrake.  I love apt-get, I had thought about going Debian for over a year.  My process was

I wiped hdc (master) which is 20 gb on a AMD k2-350 and installed Kubuntu, and I really liked it.  I still had Mandrake on the 40 gb hdb (slave).

I wiped hdc (master) and copied over /home and /usr/local from 40 gb hdb (slave).  I called it /home2 and /usr/local2.  

Mandrake 9. 10.0 and 10.1 had seen the 40 gb hard disk drive as a 31.1 GB. FreeBSD of course would see it as a 40 GB drive (not using FreeBSD these days, I do like it though). I was impressed that Kubuntu on hdc saw hdb as 40 gb. Both hdrives are Maxtors. 

So I decided to abandon Mandrake. /home and /usr/local saved. 

I was going to install kubuntu on the slave hdb 40 gb hard drive. I was going to wipe entire drive off.

I did not like the setting in multiseat. /usr too big for me, I like a bigger tmp, and I like a bigger swap. So I did it by hand root / 512 mb, /usr 2.1 GB, /var 1.0 Gb /swap 1.0 Gb, tmp 1.0 GB and rest to home on a total reformat on hdb.

Six different ways I have gone at it, and each time the partitioning hangs on not identifying the swap file. I have tried stock multiseat, stock single user, and various partition editing by hand.  I tried setting up all as percentages (except root of 512 MB - doesn't accept 0.5% - percentages need to be at least an integer I am inferring).

Yes, swap is as a swap file, usually hdb7. / is primary. all the rest are logical.

Any ideas. Is the 40 gb too big to identify for my old Soyo motherboard bios?

Is it my having hdb as slave and hdc as master? 

Is my swap too big?

I would prefer not having the 20 gb be the workhorse, it is getting long in the tooth.

Should I be going LVM after setting up root (/)

TIA

peace, Mark

---

