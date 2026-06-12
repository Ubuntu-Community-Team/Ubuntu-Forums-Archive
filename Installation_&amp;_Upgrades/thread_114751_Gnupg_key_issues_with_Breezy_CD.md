---
title: "Gnupg key issues with Breezy CD"
date: 2006-01-09
forum: Installation &amp; Upgrades
---

### Post by miahfost on 2006-01-09
Hello there,

It appears that there are some issues with the Breezy CD and Gnu Privacy Guard. Specifically, Synaptic and apt-cdrom will return an error if they cannot find the public key for the CD. Here is the error message;

sudo apt-cdrom add
Using CD-ROM mount point /cdrom/
Unmounting CD-ROM
Waiting for disc...
Please insert a Disc in the drive and press enter
Mounting CD-ROM...
Identifying.. [7800775d2ce00e630ff4fbae2bcd6551-2]
Scanning disc for index files..
Found 2 package indexes, 0 source indexes and 1 signatures
Found label 'Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)'
This disc is called:
'Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)'
Copying package lists...gpgv: Signature made Wed 12 Oct 2005 06:25:36 PM CEST using DSA key ID FBB75451
gpgv: Can't check signature: public key not found
E: Sub-process gpgv returned an error code (2)
W: Signature verification failed for: /cdrom/dists/breezy/Release.gpg


It would be great if there was some mention on these boards about the key signing issue, many users who are new to linux do not use a private key and are unfamiliar with key signing and this prevents the CD from being usable.

Where is the public key stored, since I presume that is the issue, so that one can download the key and authenticate the CD.

Thanks,

Jeremiah

---

### Post by routerbad on 2006-08-05
I used the dapper CD and had the same problem.

I found the public.key at the root of the cd and used 
sudo apt-key add /media/cdrom0/public.key

it came back with "ok" and let me add the cdrom as a repo.

---

