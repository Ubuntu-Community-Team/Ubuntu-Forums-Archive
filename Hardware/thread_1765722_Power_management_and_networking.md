---
title: "Power management and networking"
date: 2011-05-23
forum: Hardware
---

### Post by squarooticus on 2011-05-23
I have a desktop machine with a LUKS-encrypted disk that mounts home directories via NFS. I would like to be able to put this machine to (S1 or S3) sleep so I can save power while making it possible for me to wake the machine remotely (i.e., without having to enter a password at the console).

The problem is obvious: the power management subsystem takes down the network via NetworkManager and *then* calls sync, which obviously blocks forever in disk wait because the NFS server is unavailable.

In 10.10, I just had to dpkg-divert /usr/lib/pm-utils/sleep.d/55NetworkManager elsewhere to solve this problem: since I will always bring the machine back up with the same (static) IP owing to the fact that it weighs 20lbs and is connected to several large, stationary monitors, there is no good reason to take the network down. Unfortunately, this does not appear to work in 11.04. What is the new magick for un-stupiding power management? </snark>

FWIW, while this problem occurs 100% of the time for me owing to my use of NFS for home directories, there is no reason why this could not happen intermittently on *any* machine mounting a remote file system with NFS "hard"-style mounting semantics: if there happens to be a write pending after the network is taken down, sync will block forever in such a case.

---

