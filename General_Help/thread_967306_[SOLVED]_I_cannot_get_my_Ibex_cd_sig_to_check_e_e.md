---
title: "[SOLVED] I cannot get my Ibex cd sig to check e_e"
date: 2008-11-01
forum: General Help
---

### Post by Lord Xeb on 2008-11-01
```
nathan@nathan-laptop:~$ apt-cdrom add
Using CD-ROM mount point /cdrom/
Unmounting CD-ROM
Waiting for disc...
Please insert a Disc in the drive and press enter 
Mounting CD-ROM...
Identifying.. [ac20a1ac35626cb607897968f3dd2440-2]
Scanning disc for index files..
Found 2 package indexes, 0 source indexes, 0 translation indexes and 1 signatures
This disc is called: 
'Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)'
Copying package lists...gpgv: Signature made Wed 29 Oct 2008 07:24:11 PM EDT using DSA key ID FBB75451
gpgv: Can't check signature: public key not found
E: Sub-process gpgv returned an error code (2)
W: Signature verification failed for: /cdrom/dists/intrepid/Release.gpg

```

---

### Post by Partyboi2 on 2008-11-03
Have a look that you have the key listed in Authentication in Software Sources (System>Admin>Software Sources>Authentication) If you do not see [FONT=monospace]
[/FONT]> FBB75451 2004-12-30
Ubuntu CD image Automatic signing key <cdimage@ubuntu.comthen try pressing "restore defaults"
If it does not add the ubuntu cd key then try importing the key by copying and paste the key from [[COLOR=Blue]here[/COLOR]]("http://keyserver.ubuntu.com:11371/pks/lookup?search=Ubuntu+CD+Image+Automatic+Signing+Key&op=vindex") into a text editor (gedit) and then save and use the import key button in Software Sources to import the key.

---

### Post by Lord Xeb on 2008-11-03
Thanks. I fixed it by doing a reinstall >_>

---

