---
title: "SSDs, FDE (dm-crypt/LUKS) and ecryptfs"
date: 2011-04-14
forum: Hardware
---

### Post by visual1ce on 2011-04-14
I've been reading and chatting on IRC and the general gist seems to be that encryption and SSDs mix about as well as water and oil. 

I was just wondering if any others are using an SSD with FDE or ecryptfs and how long you have been running your system with this configuration.

For those who are technically inclined: is it advisable to encrypt an SSD using FDE or ecryptfs? I understand that TRIM is not supported under FDE and not sure about ecryptfs although I've also read that some are using SSDs without TRIM... Apparently there was a commit for the most current kernel to enable TRIM and FDE but it seems this would introduce security issues.

Is software encryption a feasible option with SSDs? Does it depend on how the encryption works?

---

### Post by Paradoxfox93 on 2011-07-19
WOrks fine for me.  I used Gparted on live and Partitoned the /boot with 1mb preceding at the beginning of the drive.  THen finished encryption with the alternate CD on the second partition logical. LVM set up like a peach and SSD reported peak model preformance (Well and above benchmarks for the underpreforming 40GB model I have in the 320series, rather, achieving par with the larbger drives @280MB/s peak 260MB/s avg).

I did not install swap, disabled journalling etc. no problems at all.

TRIM support works fine.  Just add 'discard' to the relevant fstab mounts.

Only problem I had was due to my own configuration error and I'm reinstalling now without the need for LVM so we'll see how that goes.

---

