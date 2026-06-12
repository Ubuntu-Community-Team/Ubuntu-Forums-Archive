---
title: "Can not upgrade from 9.04 to 9.10"
date: 2009-10-29
forum: Installation &amp; Upgrades
---

### Post by hoboy on 2009-10-29
I am using update manager to try to upgrade from 9.04 to 9.10
I am getting the following errors:
**************************************************************************
W:Failed to fetch [http://dk.archive.ubuntu.com/ubuntu/dists/karmic/restricted/binary-amd64/Packages.bz2](http://dk.archive.ubuntu.com/ubuntu/dists/karmic/restricted/binary-amd64/Packages.bz2)  Hash Sum mismatch
, W:Failed to fetch [http://dk.archive.ubuntu.com/ubuntu/dists/karmic/main/binary-amd64/Packages.bz2](http://dk.archive.ubuntu.com/ubuntu/dists/karmic/main/binary-amd64/Packages.bz2)  Hash Sum mismatch
, W:Failed to fetch [http://dk.archive.ubuntu.com/ubuntu/dists/karmic/multiverse/binary-amd64/Packages.bz2](http://dk.archive.ubuntu.com/ubuntu/dists/karmic/multiverse/binary-amd64/Packages.bz2)  Hash Sum mismatch
, W:Failed to fetch [http://dk.archive.ubuntu.com/ubuntu/dists/karmic/restricted/source/Sources.bz2](http://dk.archive.ubuntu.com/ubuntu/dists/karmic/restricted/source/Sources.bz2)  Hash Sum mismatch
, W:Failed to fetch [http://dk.archive.ubuntu.com/ubuntu/dists/karmic/universe/binary-amd64/Packages.bz2](http://dk.archive.ubuntu.com/ubuntu/dists/karmic/universe/binary-amd64/Packages.bz2)  Hash Sum mismatch
, W:Failed to fetch [http://dk.archive.ubuntu.com/ubuntu/dists/karmic/universe/source/Sources.bz2](http://dk.archive.ubuntu.com/ubuntu/dists/karmic/universe/source/Sources.bz2)  Hash Sum mismatch
, W:Failed to fetch [http://dk.archive.ubuntu.com/ubuntu/dists/karmic/multiverse/source/Sources.bz2](http://dk.archive.ubuntu.com/ubuntu/dists/karmic/multiverse/source/Sources.bz2)  Hash Sum mismatch
, E:Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by NormanFLinux on 2009-10-29
Sounds like your Internet connection is bad or the Ubuntu servers are broken or not reachable.

---

### Post by hoboy on 2009-10-29
> **NormanFLinux said:**
> Sounds like your Internet connection is bad or the Ubuntu servers are broken or not reachable.

well my connection is very good I have 10 megabit.
but maybe Ubuntu server is broken or reachable.
That is unfortunate, if that is the case.

---

### Post by PhilipJohnLewis on 2009-10-29
It's been like that all day. I work for an internet company :) - trsut me, it's not the network that is at fault.

There is something rotten in the state of danmark

Sikken noget lort, mand!

---

### Post by hwttdz on 2009-10-29
You can open up synaptic and change the repository you're using.  It could just be a problem with that repository.  settings->repository->download from: other->select best.

---

### Post by hoboy on 2009-10-29
> **PhilipJohnLewis said:**
> It's been like that all day. I work for an internet company :) - trsut me, it's not the network that is at fault.

There is something rotten in the state of danmark

Sikken noget lort, mand!

Ha ha ha ha det er måske rigtig.. sorry guys
have you been able to upgrade ? if so witch server have point to ?

---

### Post by sports fan Matt on 2009-10-29
When I upgraded in the early alpha phase, I used a canadian server since the fastest US one has been broken for a while.

---

### Post by PhilipJohnLewis on 2009-10-29
Thanks, Main Server seems to have passed the critical point, so now we wait an hour or so.

---

### Post by PhilipJohnLewis on 2009-10-29
Well that took hours and hours, and somewhere near the end of the process it seemed to enter some sort of error generation loop, however the poup error messages were always empty. I left it humming away in the office, but I somehow suspect that the installation has been a catastrophic failure and my Ubuntu partition is now toast.

More news tomorrow.

---

