---
title: "Yet another broken raid array"
date: 2009-06-02
forum: Installation &amp; Upgrades
---

### Post by dradams on 2009-06-02
Hello all,

I know that this is a tired subject, but I upgraded from Uv8 to Uv9.04 and my raid array got trashed. Most everything was backed up, but a few important things didn't make the back-up and I'd appreciate any help available.

The array was raid0 (yes, I know) mounted on /dev/md0. It comprised two 500 Gb SATA drives /dev/sdb and /dev/sdc. It was furthermore encrypted with truecrypt.

-mdadm.conf is essentially empty with no definitions
-mdadm --detail --scan says "md device /dev/md/d0 does not appear to be active"
-mdadm --assemble /dev/md0 /dev/sdb /dev/sdc  says "mdadm: cannot open device /dev/sdc: Device or resource busy"

In addition to not using raid0 and being more careful with my backups, can anyone offer any advice?

Thanks. -David

---

### Post by dradams on 2009-06-03
Please?

---

### Post by ronparent on 2009-06-03
My impression (yet unchallenged) is that 9.04 is broken for use with raid drives. I don't boot to raid, so I wasn't impacted too bad, but, I had concluded that unless you were an advance linux maven (which I am not) it was unlikely that you would be able to boot to a raid0 array. My observation was that in the upgrade to 9.04 the boot process would no longer activate your raid drives (apparently true with both software raid and fakeraid as I use). That behavior would render a raid0 unbootable with a raid drive. I've both searched for a work around and posted a bug report to launchpad, so far to no avail. From some of the launchpad chatter it appears that there will be no offical fix until release of the next distro.

My own current solution was just today to reinstall 8.10 to replace 9.04. So far although I am booting with the new 2.6.27-14-generic kernal, everything looks stable right now with raid0 behavior as I expected from 8.10. You will have to draw your own conclusions but I would reccomend regressing to 8.10. If you haven't already done so you might creat a separate /home partition to preserve your data in a reinstall! I wish you the best of luck whatever you decide to do.

---

