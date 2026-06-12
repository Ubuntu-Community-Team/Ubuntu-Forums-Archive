---
title: "mount syntax vs fstab syntax"
date: 2022-03-11
forum: Hardware
---

### Post by mmdmurphy on 2022-03-11
I am trying to establish nfs mount.  By trial and error, I found that this works from the command line, but probably won't survive a reboot:
mount -t nfs -o nolock 10.15.217.253:/data/anda /data/anda
(and gives me the desired results).

I then ran this command "mount | grep anda":
10.15.217.253:/data/anda on /data/anda type nfs4 (rw,relatime,vers=4.1,rsize=1048576,wsize=1048576,namlen=255,hard,proto=tcp,timeo=600,retrans=2,sec=sys,clientaddr=10.15.217.254,local_lock=none,addr=10.15.217.253)

My question is about the syntax.  Can I copy and paste the output of the mount command into the /etc/fstab file, or is the syntax different?

Searching the web hasn't been fruitful, as the nuances are lost.

---

### Post by TheFu on 2022-03-11
The same options can be used, just the order in the line inside an fstab is different.
Taking this:
```
sudo mount -t nfs -o nolock 10.15.217.253:/data/anda /data/anda
```
The fstab line becomes
```
10.15.217.253:/data/anda /data/anda nfs nolock
```

However, you probably want:
```
#  <SOURCE>                  <MNT Point>   <FS Type>   <Options>                          <5>  <6>
10.15.217.253:/data/anda     /data/anda      nfs      nconnect=4,proto=tcp,async,nolock    0    0
```
to help performance.

The number of spaces between each segment don't matter in either method. The "options" part CANNOT have spaces.  The last 2 fields, while optional in the fstab, are expected. The 0 0 is perfect for all non-local storage. The fstab manpage explains the different fields.

The only secrets in Linux are that all the answers are already installed on your system as manpages. Every option, file types, and arguments to commands are specified there, unless you disable the automatic installation of the manpages in APT.

---

