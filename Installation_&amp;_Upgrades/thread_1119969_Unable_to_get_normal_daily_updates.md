---
title: "Unable to get normal daily updates"
date: 2009-04-08
forum: Installation &amp; Upgrades
---

### Post by gfkbob on 2009-04-08
When I try to get the daily updates I get a message saying I can only run a partial upgrade but it will not even allow that.  It says something about a previous update being unsuccessful or a couple of other items.  Anyone have a clue where I go from here?

---

### Post by Mark Phelps on 2009-04-08
You need to write down and report the exact error messages you're getting.

We can't give specific directions without knowing what errors are being generated.

---

### Post by Psychopump on 2009-04-08
I have the same issue.

This is what I get when I check for possible updates:


```
W: GPG error: http://packages.medibuntu.org hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: GPG error: http://ppa.launchpad.net intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 9423A34CCA967634
W: GPG error: http://ppa.launchpad.net intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 13824E1582F8DE87
W: Failed to fetch http://edevelop.org/pkg-e/ubuntu/dists/edgy/Release.gpg  Could not resolve 'edevelop.org'

W: Failed to fetch http://edevelop.org/pkg-e/ubuntu/dists/edgy/e17/i18n/Translation-en_US.bz2  Could not resolve 'edevelop.org'

W: Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/edgy/multiverse/binary-i386/Packages.gz  404 Not Found [IP: 91.189.88.46 80]

W: Failed to fetch http://e17.dunnewind.net/ubuntu/dists/hardy/e17/binary-i386/Packages.gz  404 Not Found

W: Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/edgy/multiverse/source/Sources.gz  404 Not Found [IP: 91.189.88.46 80]

W: Failed to fetch http://e17.dunnewind.net/ubuntu/dists/hardy/e17/source/Sources.gz  404 Not Found

W: Failed to fetch http://repoubuntusoftware.info/dists/harty/all/binary-i386/Packages.gz  404 Not Found

W: Some index files failed to download, they have been ignored, or old ones used instead.
```

---

### Post by oldos2er on 2009-04-08
Why do you have Edgy and Hardy and Intrepid repositories? I'm sure that's one reason your package manager's confused.

---

### Post by Psychopump on 2009-04-08
I added those reps while trying to DL specific apps.
I will remove them now and see what happens..


EDIT:

Good news: the error message has become SHORTER:
```
GPG error: http://ppa.launchpad.net intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 9423A34CCA967634GPG error: http://ppa.launchpad.net intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 13824E1582F8DE87Failed to fetch http://repoubuntusoftware.info/dists/harty/all/binary-i386/Packages.gz  404 Not Found
Some index files failed to download, they have been ignored, or old ones used instead.
```

But it&#347; still an error.
How can I resolve this issue concerning signatures and public keys (whatever they are)?

---

### Post by oldos2er on 2009-04-08
Is that actually supposed to say "harty" instead of hardy? Just curious.

 You need to download and install the public key for repoubuntusoftware.

---

### Post by Therion on 2009-04-08
Switch to a different server.

System/Administration/Software Sources/Ubuntu Software tab.

Click on the "Download From" dropdown menu and either switch US Main/Main Server or click on "Other" and then on "Select Best Server" to find the fastest download server for your current connection.

---

