---
title: "Update manager error"
date: 2008-12-17
forum: Installation &amp; Upgrades
---

### Post by whistlerspa on 2008-12-17
Can anyone explain what the following error meassage means that i get when I try to run update manager? This just started happening a few days ago.

[COLOR="Blue"]W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://archive.canonical.com](http://archive.canonical.com) hardy Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release: The following signatures were invalid: BADSIG 2EBC26B60C5A2783 Medibuntu Packaging Team <admin@lists.medibuntu.org>
W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/hardy/Release](http://archive.canonical.com/ubuntu/dists/hardy/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead.[/COLOR]

---

### Post by nandob on 2008-12-17
Hi there.

I just saw your post and wanted to add my own question. I don't know if our issues are related but I have a laptop that I dual booted a few months ago with XP on one partitions and Ubuntu 8.04 on the other. A month ago I upgraded Ubuntu to 8.10 and for the most part all has been good. Today I ran the update mangager and it told me I had all my updates. Now I have an icon in the toolbar telling me there is an issue with update manager. If I try to launch it or the package manager the dialog boxes pop up, I may see a progress bar or not really quickly and then they disappear completely. No idea what happened.  I get no error messages apart from the icon in the toolbar.

Anyone have any thoughts?

Thanks in advance.

---

### Post by neu2buntu on 2008-12-17
this has something to do with /etc/apt/sources.list  ,or have a look at the gui in -->system-->administration-->software sources

---

### Post by whistlerspa on 2008-12-17
Yes i know  - but what?

---

### Post by jenkinbr on 2008-12-17
> **whistlerspa said:**
> Can anyone explain what the following error meassage means that i get when I try to run update manager? This just started happening a few days ago.

[COLOR="Blue"]W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://archive.canonical.com](http://archive.canonical.com) hardy Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release: The following signatures were invalid: BADSIG 2EBC26B60C5A2783 Medibuntu Packaging Team <admin@lists.medibuntu.org>
W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/hardy/Release](http://archive.canonical.com/ubuntu/dists/hardy/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead.[/COLOR]
The errors with the medibuntu repositories can be fixed by installing this package: [http://packages.medibuntu.org/pool/free/m/medibuntu-keyring/medibuntu-keyring_2008.04.20_all.deb](http://packages.medibuntu.org/pool/free/m/medibuntu-keyring/medibuntu-keyring_2008.04.20_all.deb)
Note that this is for [COLOR="Red"]**Hardy **[/COLOR]machines on [COLOR="Red"]**All Architectures**[/COLOR] (amd64, ix86, ppc, etc.)

---

### Post by whistlerspa on 2008-12-17
> **jenkinbr said:**
> The errors with the medibuntu repositories can be fixed by installing this package: [http://packages.medibuntu.org/pool/free/m/medibuntu-keyring/medibuntu-keyring_2008.04.20_all.deb](http://packages.medibuntu.org/pool/free/m/medibuntu-keyring/medibuntu-keyring_2008.04.20_all.deb)
Note that this is for [COLOR="Red"]**Hardy **[/COLOR]machines on [COLOR="Red"]**All Architectures**[/COLOR] (amd64, ix86, ppc, etc.)


Thanks for the post - I tried this  - it reinstalled the package but has not fixed the error. I was able to download and install new updates however.

---

