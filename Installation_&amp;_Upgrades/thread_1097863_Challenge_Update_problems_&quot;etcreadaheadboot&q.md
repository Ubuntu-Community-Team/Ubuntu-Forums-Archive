---
title: "Challenge: Update problems &quot;\etc\readahead\boot&quot;"
date: 2009-03-16
forum: Installation &amp; Upgrades
---

### Post by triheart on 2009-03-16
Update problems "\etc\readahead\boot"

Okay, I'm a bit of a beginner with this...

I had an issue when I was trying to update; since we haven't used this computer for about...a year! It asked me if I was okay with changing/replacing "\etc\readahead\boot" and then something else; I pushed no (figuring that my boot was really important and could mess up a lot of things if I change it.

Now, when I check for updates it tells me:

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783

W: Failed to fetch [http://packages.medibuntu.org/dists/hardy/Release](http://packages.medibuntu.org/dists/hardy/Release)

W: Some index files failed to download, they have been ignored, or old ones used instead.

Then it tells me that it has no available updates, even though it was "last updated 279 days ago".

I have Ubuntu 8.04.2 \n \l

---

### Post by taurus on 2009-03-16
Looks to me like there is a type in your packages.medibuntu.org's repo.  The error message says **hary** but it should be **hardy**.

Have a look at your /etc/apt/sources.list.

```
cat /etc/apt/sources.list
```

---

### Post by triheart on 2009-03-16
oops... see I told you I was a beginner. I kept trying to get it to copy from what I highlighted from the errors, and paste them on here; but it didn't. I typed it all myself. Everything else *should* be correct.

---

### Post by taurus on 2009-03-16
If you need GPG key for Medibuntu, just run this line in a terminal.

```

sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

```

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by triheart on 2009-03-16
Thank you. This seems to have fixed the problem. I ran the line, and for a second it said most of the same errors again, but it continued and after awhile and a whole bunch of lines, it was done. I tried to do some updates, and I only had 6; some to help with music and video and some other stuff and skype. I'm not sure if it was all of the updates needed after 297 days, but it didn't say any errors when I was using the Update Manager. WOO-HOO!

---

