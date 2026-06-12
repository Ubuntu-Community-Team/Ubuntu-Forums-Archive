---
title: "Nas"
date: 2005-05-29
forum: Hardware &amp; Laptops
---

### Post by EddieBenton on 2005-05-29
Hi guys, next year I was planning on running a network in my house with the topology shown [here](http://www.eddiebenton.co.uk/Network.png) and was wondering how I could accomplish the 1TB NAS part.
I was thinking of building a decent processor powered machine with 4 300 GB HDDS connected to an adaptec RAID controller to be effectively displayed as one drive, then having it use NFS or something?

Im a little shady on the particulars, however I would need to be able to do the following with the system and was wondering if ubuntu could accomplish it on the machine

*User based access, some read only some rw
*Data encryption, all the data on the disk encrypted and only decrypted on the fly when accessed by a valid user
*Storage space mountable as drives by linux and windows (perhaps as mapped network drive)

Thanks Guys
Ed

---

### Post by nocturn on 2005-05-30
[QUOTE=EddieBenton]
*User based access, some read only some rw
*Data encryption, all the data on the disk encrypted and only decrypted on the fly when accessed by a valid user
*Storage space mountable as drives by linux and windows (perhaps as mapped network drive)
[/QUOTE]

You will need two things (without the data encryption).
1) A user directory/Authentication strucutre
2) A File Sharing protocol.

For 1 to be done securely and in a portable way, you might want to check out LDAP and Kerberos.
2 is a bit of a problem.  On Linux you can use NFS (not secure).  
AFS or NFSv4 (development) would be more secure and they support kerberos.
Windows does not do NFS well, so you will need either Samba or an AFS client (whichever you choose).  I'm not sure if an AFS client exists for Windows.

The encryption is much more difficult, you will need some crypto loopback filesystem.  This will significantly slow down the machine (just so you know) and I do not know how reliable the encrypted partitions are.

Another alternative is to store sensitive files encrypted, you can use PGP (GnuPG) for this.

---

