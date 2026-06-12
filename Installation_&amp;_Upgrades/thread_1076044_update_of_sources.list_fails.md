---
title: "update of sources.list fails"
date: 2009-02-20
forum: Installation &amp; Upgrades
---

### Post by tanveer on 2009-02-20
Dear all,

I am having a problem in running the sudo apt-get update with the default sources.list file. I have tried both 8.04 and 8.10 but the error occurs is of same type as below:
[PHP]
Get:43 http://bd.archive.ubuntu.com hardy-backports/universe Sources [24.6kB]                                                               
Get:44 http://bd.archive.ubuntu.com hardy-backports/multiverse Sources [3817B]                                                              
Get:45 http://bd.archive.ubuntu.com hardy/main Sources [443kB]                                                                              
96% [45 Sources gzip 0]                                                                                                          73.7kB/s 4s
gzip: stdin: not in gzip format
Err http://bd.archive.ubuntu.com hardy/main Sources                                                                                         
  Sub-process gzip returned an error code (1)
Fetched 8751kB in 15min1s (9703B/s)                                                                                                         
W: Failed to fetch http://bd.archive.ubuntu.com/ubuntu/dists/hardy/main/source/Sources.gz  Sub-process gzip returned an error code (1)

E: Some index files failed to download, they have been ignored, or old ones used instead.

[/PHP]

Can anybody help me why is this happening. I even checked the location and there is a file on that name. 

Thanks in advance.

---

### Post by konqueror7 on 2009-02-20
can you perhaps post your */etc/apt/sources.lst*?

---

### Post by tanveer on 2009-02-20
Thanks for reply. Please see attached my sources.list.

---

### Post by Partyboi2 on 2009-02-20
Try removing any files you have in /var/lib/apt/lists/partial.
```
sudo rm /var/lib/apt/lists/partial/*

```
then
```
sudo apt-get update
```

---

### Post by konqueror7 on 2009-02-20
try to comment out your backports sources, and refresh again...

oh btw, next time just post your sources.lst or any text file via 'code' tags...:D

---

### Post by tanveer on 2009-02-21
Sorry that doesn't work gives this error.

```

Hit http://bd.archive.ubuntu.com hardy-updates/multiverse Sources                                                                           
Get:2 http://bd.archive.ubuntu.com hardy/main Sources [443kB]                                                                               
56% [Working]                                                                                                                   25.0kB/s 13s
gzip: stdin: not in gzip format
Err http://bd.archive.ubuntu.com hardy/main Sources                                                                                         
  Sub-process gzip returned an error code (1)
Fetched 181kB in 6min19s (478B/s)                                                                                                           
W: Failed to fetch http://bd.archive.ubuntu.com/ubuntu/dists/hardy/main/source/Sources.gz  Sub-process gzip returned an error code (1)

E: Some index files failed to download, they have been ignored, or old ones used instead.


```
Here is the sources.list file now
```

tanveer@tanveer-desktop:~$ cat /etc/apt/sources.list
#deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://bd.archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://bd.archive.ubuntu.com/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://bd.archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://bd.archive.ubuntu.com/ubuntu/ hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://bd.archive.ubuntu.com/ubuntu/ hardy universe
deb-src http://bd.archive.ubuntu.com/ubuntu/ hardy universe
deb http://bd.archive.ubuntu.com/ubuntu/ hardy-updates universe
deb-src http://bd.archive.ubuntu.com/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://bd.archive.ubuntu.com/ubuntu/ hardy multiverse
deb-src http://bd.archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://bd.archive.ubuntu.com/ubuntu/ hardy-updates multiverse
deb-src http://bd.archive.ubuntu.com/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
#deb http://bd.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
#deb-src http://bd.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu hardy partner
deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://security.ubuntu.com/ubuntu hardy-security main restricted
deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted
deb http://security.ubuntu.com/ubuntu hardy-security universe
deb-src http://security.ubuntu.com/ubuntu hardy-security universe
deb http://security.ubuntu.com/ubuntu hardy-security multiverse
deb-src http://security.ubuntu.com/ubuntu hardy-security multiverse

```

---

### Post by konqueror7 on 2009-02-21
comment also this line...
```
deb http://archive.canonical.com/ubuntu hardy partner
deb-src http://archive.canonical.com/ubuntu hardy partner

```

after that, do this...
```
sudo apt-get -f clean
```

```
sudo apt-get update
```

try the following code for several times, see if that works...

---

### Post by tanveer on 2009-02-22
Nop, gives that same zip error.

Also tried changing http to ftp.

---

### Post by jocko on 2009-02-22
Can you open [http://bd.archive.ubuntu.com/ubuntu/dists/](http://bd.archive.ubuntu.com/ubuntu/dists/) in a browser?

Edit: I didn't notice you had an error complaining about gzip.
Your sources.list is ok, and the server (bd.archive.ubuntu.com) is online (I can browse it in firefox).
Maybe something is wrong with the files apt downloads from the server.
The errors only appear to happen with the "Sources" and not the "Packages".
Try commenting out all lines starting with "deb-src".

---

### Post by konqueror7 on 2009-02-22
maybe the server is down? try changing to a new server...

---

