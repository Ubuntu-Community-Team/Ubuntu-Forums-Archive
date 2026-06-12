---
title: "ipod with Amarok"
date: 2007-01-30
forum: Hardware &amp; Laptops
---

### Post by datakid on 2007-01-30
Right. so My ipod doesn't work with Amarok. I seem to have trouble getting it to work with others as well, but amarok is the one I'm looking at.

I noticed a plethora of other threads also discussing this, although all were NQR in some way (about dapper, about AAC, about gtkpod, complete n00bs, etc.)

So, it's a mini that was initialized on an ibook 2 years ago. 

Now I've moved to ubuntu edgy 6.10, amarok 1.4.3 other versions can be provided on request.

I noticed at first that I got this issue:

Media Device: failed to create lockfile on iPod mounted at /media/ipod: Read-only file system

so I did the chmod +w /media/ipod. Now I get this issue:

Media Device: No mounted iPod found

So then I look at one of the Howto's and took a peek in dmesg and /etc/mtab

that's when I noticed:

> datakid@boxen:~$ dmesg |grep hfs
[17179684.920000] hfs: write access to a jounaled filesystem is not supported, use the force option at your own risk, mounting read-only.
 

and 

> datakid@boxen:~$ more /etc/mtab 
/dev/sda5 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
....
/dev/sdb3 /media/ipod hfsplus rw,nosuid,nodev,uid=1000,gid=1000 0 0
datakid@boxen:~$ 


So, I presume there is some issue with the apple file system on the ipod  - I think that is what the HFS is referring to?

Any help appreciated

cheers

---

### Post by Maxtorm on 2007-02-01
Take a look here: [http://pag.csail.mit.edu/~adonovan/hacks/ipod.html](http://pag.csail.mit.edu/~adonovan/hacks/ipod.html)

It would appear that if you're going to use the iPod in HFS format, there's a bit more work invovled.  Mine is formated as vfat and appears to be working fine with Amarok.

---

