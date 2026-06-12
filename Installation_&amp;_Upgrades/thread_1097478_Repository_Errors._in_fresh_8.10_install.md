---
title: "Repository Errors. in fresh 8.10 install"
date: 2009-03-16
forum: Installation &amp; Upgrades
---

### Post by lemonshark10 on 2009-03-16
Alright, so i accidentaly made my machine unbootable over the weekend and had to reinstall tonight. I backed up my data and reinstalled but now when i'm trying to install any software i tells me the software doesn't support my hardware (i386) when really i have i686. Also whenever it tries to refresh the package list i get errors here is one that i got while in the process of trying to get the restricted extras package: 
```
W: GPG error: http://archive.canonical.com intrepid Release: The following signatures were invalid: NODATA 2
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: http://us.archive.ubuntu.com intrepid Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: http://us.archive.ubuntu.com intrepid-updates Release: The following signatures were invalid: NODATA 2

W: GPG error: http://us.archive.ubuntu.com intrepid-security Release: The following signatures were invalid: NODATA 2
W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/intrepid/restricted/i18n/Translation-en_US.bz2  Error reading from server - read (104 Connection reset by peer) [IP: 91.189.88.46 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/i18n/Translation-en_US.bz2  Error reading from server - read (104 Connection reset by peer) [IP: 91.189.88.46 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/i18n/Translation-en_US.bz2  Error reading from server - read (104 Connection reset by peer) [IP: 91.189.88.46 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/i18n/Translation-en_US.bz2  Error reading from server - read (104 Connection reset by peer) [IP: 91.189.88.46 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/intrepid-security/restricted/i18n/Translation-en_US.bz2  Error reading from server - read (104 Connection reset by peer) [IP: 91.189.88.46 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/intrepid-security/multiverse/i18n/Translation-en_US.bz2  Error reading from server - read (104 Connection reset by peer) [IP: 91.189.88.46 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/intrepid/Release  

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/Release  

W: Some index files failed to download, they have been ignored, or old ones used instead.

```

i have tried changing my source to main, and even to MIT's server i have been scaning the forums and google but found no one in the same situation.

I faintly remember something like this on my last install but forget how i fixed it (T_T).

Thank you in advance for your help.

---

### Post by cariboo on 2009-03-16
I would suggest going to System-->Administration-->Software Sources,and select other from the download from dropdown, then  click Select Best Sever, once it has finished click Choose Server. You will be prompted to update you Sources list, once down you should be able to do your updates.

Jim

---

### Post by lemonshark10 on 2009-03-16
i just tried that. i selected the database it chose and clicked close. it then told me it had to reload the package list or something to that effect abd then i got this error

```
GPG error: http://archive.canonical.com intrepid Release: The following signatures were invalid: NODATA 2Failed to fetch http://mirror.fslutd.org/linux/distributions/ubuntu/packages/dists/intrepid/main/i18n/Translation-en_US.bz2  Error reading from server - read (104 Connection reset by peer)
Failed to fetch http://mirror.fslutd.org/linux/distributions/ubuntu/packages/dists/intrepid/universe/i18n/Translation-en_US.bz2  Error reading from server - read (104 Connection reset by peer)
Failed to fetch http://mirror.fslutd.org/linux/distributions/ubuntu/packages/dists/intrepid-updates/Release.gpg  Error reading from server - read (104 Connection reset by peer)
Failed to fetch http://mirror.fslutd.org/linux/distributions/ubuntu/packages/dists/intrepid-updates/restricted/i18n/Translation-en_US.bz2  Error reading from server - read (104 Connection reset by peer)
Failed to fetch http://mirror.fslutd.org/linux/distributions/ubuntu/packages/dists/intrepid-security/main/i18n/Translation-en_US.bz2  Error reading from server - read (104 Connection reset by peer)
Failed to fetch http://mirror.fslutd.org/linux/distributions/ubuntu/packages/dists/intrepid-security/universe/i18n/Translation-en_US.bz2  Error reading from server - read (104 Connection reset by peer)
Failed to fetch http://mirror.fslutd.org/linux/distributions/ubuntu/packages/dists/intrepid/main/binary-i386/Packages.gz  Error reading from server - read (104 Connection reset by peer)
Failed to fetch http://mirror.fslutd.org/linux/distributions/ubuntu/packages/dists/intrepid/restricted/binary-i386/Packages.gz  503 Service Unavailable
Failed to fetch http://mirror.fslutd.org/linux/distributions/ubuntu/packages/dists/intrepid/main/source/Sources.gz  Error reading from server - read (104 Connection reset by peer)
Failed to fetch http://mirror.fslutd.org/linux/distributions/ubuntu/packages/dists/intrepid/restricted/source/Sources.gz  503 Service Unavailable
Failed to fetch http://mirror.fslutd.org/linux/distributions/ubuntu/packages/dists/intrepid/universe/binary-i386/Packages.gz  503 Service Unavailable
Failed to fetch http://mirror.fslutd.org/linux/distributions/ubuntu/packages/dists/intrepid/universe/source/Sources.gz  Error reading from server - read (104 Connection reset by peer)
Failed to fetch http://mirror.fslutd.org/linux/distributions/ubuntu/packages/dists/intrepid/multiverse/binary-i386/Packages.gz  503 Service Unavailable
Failed to fetch http://mirror.fslutd.org/linux/distributions/ubuntu/packages/dists/intrepid/multiverse/source/Sources.gz  Error reading from server - read (104 Connection reset by peer)
Failed to fetch http://mirror.fslutd.org/linux/distributions/ubuntu/packages/dists/intrepid-updates/main/binary-i386/Packages.gz  503 Service Unavailable
Failed to fetch http://mirror.fslutd.org/linux/distributions/ubuntu/packages/dists/intrepid-updates/restricted/binary-i386/Packages.gz  Error reading from server - read (104 Connection reset by peer)
Failed to fetch http://mirror.fslutd.org/linux/distributions/ubuntu/packages/dists/intrepid-updates/main/source/Sources.gz  503 Service Unavailable
Failed to fetch http://mirror.fslutd.org/linux/distributions/ubuntu/packages/dists/intrepid-updates/restricted/source/Sources.gz  503 Service Unavailable
Failed to fetch http://mirror.fslutd.org/linux/distributions/ubuntu/packages/dists/intrepid-updates/universe/binary-i386/Packages.gz  Error reading from server - read (104 Connection reset by peer)
Failed to fetch http://mirror.fslutd.org/linux/distributions/ubuntu/packages/dists/intrepid-updates/universe/source/Sources.gz  503 Service Unavailable
Failed to fetch http://mirror.fslutd.org/linux/distributions/ubuntu/packages/dists/intrepid-updates/multiverse/binary-i386/Packages.gz  Error reading from server - read (104 Connection reset by peer)
Failed to fetch http://mirror.fslutd.org/linux/distributions/ubuntu/packages/dists/intrepid-updates/multiverse/source/Sources.gz  503 Service Unavailable
Failed to fetch http://mirror.fslutd.org/linux/distributions/ubuntu/packages/dists/intrepid-security/main/binary-i386/Packages.gz  Error reading from server - read (104 Connection reset by peer)
Failed to fetch http://mirror.fslutd.org/linux/distributions/ubuntu/packages/dists/intrepid-security/restricted/binary-i386/Packages.gz  503 Service Unavailable
Failed to fetch http://mirror.fslutd.org/linux/distributions/ubuntu/packages/dists/intrepid-security/main/source/Sources.gz  503 Service Unavailable
Failed to fetch http://mirror.fslutd.org/linux/distributions/ubuntu/packages/dists/intrepid-security/restricted/source/Sources.gz  503 Service Unavailable
Failed to fetch http://mirror.fslutd.org/linux/distributions/ubuntu/packages/dists/intrepid-security/universe/binary-i386/Packages.gz  503 Service Unavailable
Failed to fetch http://mirror.fslutd.org/linux/distributions/ubuntu/packages/dists/intrepid-security/universe/source/Sources.gz  Error reading from server - read (104 Connection reset by peer)
Failed to fetch http://mirror.fslutd.org/linux/distributions/ubuntu/packages/dists/intrepid-security/multiverse/binary-i386/Packages.gz  503 Service Unavailable
Failed to fetch http://mirror.fslutd.org/linux/distributions/ubuntu/packages/dists/intrepid-security/multiverse/source/Sources.gz  Error reading from server - read (104 Connection reset by peer)
Some index files failed to download, they have been ignored, or old ones used instead.
```

ARGHHH!!!!

---

