---
title: "[SOLVED] How can I get rid of these update errors??"
date: 2008-11-27
forum: General Help
---

### Post by volaer on 2008-11-27
I always get this errors:

[B]GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-security/restricted/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy-security/restricted/binary-i386/Packages.bz2)  Hash Sum mismatch
Some index files failed to download, they have been ignored, or old ones used instead.[/B]

Can someone assist me in getting rid of these errors or at least solve this update problem??? I am a newbie here.

Thanks...

---

### Post by kpkeerthi on 2008-11-27
Its quite possible that the GPG keys are not updated yet in the repository. Just wait for a few hours and then do
```
sudo apt-get clean && sudo apt-get update && sudo apt-get upgrade
```

---

### Post by volaer on 2008-11-27
> **kpkeerthi said:**
> Its quite possible that the GPG keys are not updated yet in the repository. Just wait for a few hours and then do
```
sudo apt-get clean && sudo apt-get update && sudo apt-get upgrade
```

I have already done all these things but the errors are stil there. This causes me to have failures in all my updates.:(

Can anybody help?

By the way, one time when I tried installing intrepid, It was a failure. And now I think I have some intrepid files mixed up with my hardy. Any suggestions on how can I remove the unnecessary files from intrepid? That would really be a great help.

---

### Post by volaer on 2008-11-27
> **volaer said:**
> I have already done all these things but the errors are stil there. This causes me to have failures in all my updates.:(

Can anybody help?

By the way, one time when I tried installing intrepid, It was a failure. And now I think I have some intrepid files mixed up with my hardy. Any suggestions on how can I remove the unnecessary files from intrepid? That would really be a great help.

Is this really the best solution here??? Well, it doesn't take away the errors.

---

### Post by mc4man on 2008-11-28
you could try going into System -> Admin.. -> software sources and in the 'download from' box pick some 'other' mirror.

If that doesn't work wait some more or maybe try this in the terminal

```
sudo apt-get update -o Acquire::http::No-Cache=True
```

---

### Post by volaer on 2008-11-28
> **kpkeerthi said:**
> Its quite possible that the GPG keys are not updated yet in the repository. Just wait for a few hours and then do
```
sudo apt-get clean && sudo apt-get update && sudo apt-get upgrade
```

Thanks!!! This seemed to work well.:)

---

