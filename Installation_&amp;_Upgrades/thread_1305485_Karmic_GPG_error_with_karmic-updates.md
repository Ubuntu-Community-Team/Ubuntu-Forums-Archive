---
title: "Karmic GPG error with karmic-updates"
date: 2009-10-29
forum: Installation &amp; Upgrades
---

### Post by mr19 on 2009-10-29
Installed RC the other day and I'm now having issues with updates.   Error I receive is 

```

W: GPG error: http://us.archive.ubuntu.com karmic-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

```Output from apt-key list
```

/etc/apt/trusted.gpg
--------------------
pub   1024D/437D05B5 2004-09-12
uid                  Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
sub   2048g/79164387 2004-09-12

pub   1024D/FBB75451 2004-12-30
uid                  Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>

```TIA
Marc

---

### Post by mr19 on 2009-10-30
Still failing, but here is what I've done so far (thanks to help from sciri in the irc release party).

Results of 'sudo apt-get update'
```

Fetched 190B in 3min 10s (1B/s)                           
Reading package lists... Done
W: GPG error: http://us.archive.ubuntu.com karmic-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

```

Next tried 'sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 40976EAF437D05B5'
```

Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv-keys 40976EAF437D05B5
gpg: requesting key 437D05B5 from hkp server keyserver.ubuntu.com
gpg: key 437D05B5: "Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1

```

Still no luck, same results as above.

---

### Post by ben2talk on 2009-12-01
Yes, I'm getting tons of errors with updates. I get updates, but the manager always tells me that the last time I refreshed the list was about 7 days ago! I have 11 GPG errors, and several just failed - some with '404 not found' and sometimes I just get other errors - the process is rather unreliable.

---

