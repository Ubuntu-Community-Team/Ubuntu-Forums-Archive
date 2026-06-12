---
title: "[SOLVED] Error boots me out of update manager"
date: 2008-11-10
forum: General Help
---

### Post by aaror on 2008-11-10
Well, sort of, when I check for new updates, it gives me an error message, and then does not populate the update manager with what it downloaded (I think because of the error).  Error message follows:

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://kw.archive.ubuntu.com](http://kw.archive.ubuntu.com) intrepid Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch [http://kw.archive.ubuntu.com/ubuntu/dists/intrepid/Release](http://kw.archive.ubuntu.com/ubuntu/dists/intrepid/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead.

Any ideas on how to get update manager working again?

---

### Post by kernelhaxor on 2008-11-10
You might find this helpful: 
[https://answers.launchpad.net/ubuntu/+question/37313](https://answers.launchpad.net/ubuntu/+question/37313)

Not sure if yours is the same problem as the one mentioned there .. There's a work around in one of the comments on that page ..

---

### Post by aaror on 2008-11-11
Yep, that was the problem, here I was in Kuwait thinking the Kuwait server would be the best one, instead of logically using the one in Japan (grin).  Thank you so much for your help.

---

