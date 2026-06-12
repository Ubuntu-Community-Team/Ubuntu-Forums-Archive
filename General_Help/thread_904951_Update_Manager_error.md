---
title: "Update Manager error"
date: 2008-08-29
forum: General Help
---

### Post by 5thborocs on 2008-08-29
This is preventing me from downloading updates.

"GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783Failed to fetch cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/dists/hardy/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs 
Failed to fetch cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/dists/hardy/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs 
Some index files failed to download, they have been ignored, or old ones used instead."

Any help is appreciated.

---

### Post by Yannick Le Saint kyncani on 2008-08-29
Hi 5thborocs,

You can import the medibuntu gpg keys by installing medibuntu-keyring.

As for the cdrom errors, you can remove the cdroms from apt sources.list either directly in /etc/apt/sources.list (as root) or using the gui "software sources" (in a system menu).

Cheers.

---

### Post by Shazaam on 2008-08-29
Run this in terminal to fix the gpg key for medibuntu....
```
sudo apt-get install medibuntu-keyring && sudo apt-get update
```
To get it to update without medibuntu and the cdrom go to System>Administration>Software Sources. Go through the tabs and uncheck medibuntu and the cdrom. When done it will tell you you need to update your sources list, go ahead and do it.

---

### Post by 5thborocs on 2008-08-29
Thank you both for helping.

I tried removing the checks in Software Sources, also tried the sudo apt-get install medibubtu-keyring && sudo apt-get update.

This is the response

"W: Failed to fetch cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/dists/hardy/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/dists/hardy/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

E: Some index files failed to download, they have been ignored, or old ones used instead."

---

### Post by iaculallad on 2008-08-29
> **5thborocs said:**
> Thank you both for helping.

I tried removing the checks in Software Sources, also tried the sudo apt-get install medibubtu-keyring && sudo apt-get update.

This is the response

"W: Failed to fetch cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/dists/hardy/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/dists/hardy/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

E: Some index files failed to download, they have been ignored, or old ones used instead."

Remove the CDROM source as a repository:

System->Administration->Software Sources, under the "Ubuntu Software" tab, uncheck the "Installable from CD-ROM/DVD" option. Click on Close and select Reload on the next window.

And on your terminal again:

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by 5thborocs on 2008-08-29
That fixed it error.

Thanks to everyone.

How do I close this post?

---

### Post by Shazaam on 2008-08-29
At the top click Thread Tools. Mark it as Solved.

---

### Post by shrestsn on 2008-12-02
I had the same error. There was no box to uncheck the "Installable from CD-ROM/DVD" option. 
Please do let me know if I am not clear enough stating my problem.

---

### Post by heimo11656 on 2008-12-28
I have the same problem as shrestsn, and I'm on intrepid so I don't know why I should even get this message about hardy!

---

### Post by plucky on 2008-12-29
> I have the same problem as shrestsn, and I'm on intrepid so I don't know why I should even get this message about hardy! 



**System > Administration > Software Sources > Third Party Software** and make sure the Hardy Heron entry is un-ticked,or delete it.

If you upgraded from Hardy,then the entry will be there.

If that doesn't work, then post output of ```
cat etc/apt/sources.list
```

Good Luck

---

