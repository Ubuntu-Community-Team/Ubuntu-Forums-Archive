---
title: "error while updating"
date: 2009-02-03
forum: Installation &amp; Upgrades
---

### Post by bojcistv on 2009-02-03
Hi everyone!

I have problem while I updating my ubuntu 8.10 through update manager. Here is a message I got when update manager finish:

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://ba.archive.ubuntu.com](http://ba.archive.ubuntu.com) intrepid-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch [http://ba.archive.ubuntu.com/ubuntu/dists/intrepid-updates/Release](http://ba.archive.ubuntu.com/ubuntu/dists/intrepid-updates/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead.

If someone have a same or similar problem go ahead.

Is there a chance to download update manually and update a system by myself?


Thanks in advance

---

### Post by e-a-c on 2009-02-03
I am getting the same message.

---

### Post by taurus on 2009-02-03
So into System -> Administration -> Synaptic Package Manager -> Settings -> Repositories and pick another server.  Try the Main Server if you don't know which one to use.  Don't forget to click the Reload button.

---

