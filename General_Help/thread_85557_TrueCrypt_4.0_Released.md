---
title: "TrueCrypt 4.0 Released"
date: 2005-11-02
forum: General Help
---

### Post by jonzep on 2005-11-02
has anybody tried running truecrypt in ubuntu yet?

[http://www.truecrypt.org/downloads.php](http://www.truecrypt.org/downloads.php)

if so please share your experience...

---

### Post by QCompson on 2005-11-06
I downloaded the .deb for truecrypt 4.0, but unfortunately it is for the i386 kernel, and the install crapped out (running breezy, 2.6.12-9-686).

---

### Post by HotShot on 2005-11-07
used the sources and installed with bash-files. works for me (breezy, custom 2.6.14)
bad, the forum is closed at this time!

tested with new container from windows, created with TC 4.0.

---

### Post by TestUser on 2005-11-13
Hi

I have breezy 64 and installed truecrypt, you must have the generic kernel.
I have no problems installing and running it, no gui as in windows but it is possible to mount in both os and that is good enough.
Please verify that you DL the version for breezy.

I have one problem though, I encrypted a full external HDD, how to get write access to the encrypted disc after it is mounted?
I do like this:
sudo truecrypt /dev/sdX /media/xyz
and I tried to do chown and also tried to mount the HDD by fstab but since the HDD is encrypted it is not a valid filesystem. is there a way to use a script so I just need to give the password for the encrypted disc and then get write access?

EDIT:
I feel stupid, I tried a similar aproach earlier but add this and it works:'
--mount-options 'umask=000,uid=1000,gid=100' 
[http://ubuntuforums.org/showthread.php?t=94652](http://ubuntuforums.org/showthread.php?t=94652)
Thank you in advance

TU

---

### Post by Doc.Caliban on 2005-11-16
No GUI for the linux version?

-Doc

---

### Post by TestUser on 2005-11-23
Hi

No there is no gui (yet).

No problem to mount from terminal, the only problem I have is with encoding and write to the disk without using 'open as root'.

The Truecrypt forum i closed due to maintenance, as soon as it opens it will be possible to ask and get heped there.

TU

---

### Post by Darrena on 2005-11-27
I was unable to build it myself, but this package seemed to work for me:

[http://mirrors.geekbone.org/debian-desktop.org/debian/truecrypt/dists/sarge/main/binary-i386/](http://mirrors.geekbone.org/debian-desktop.org/debian/truecrypt/dists/sarge/main/binary-i386/)

---

### Post by jackwhite on 2005-12-19
I've installed it but don't know how to use it!

I'm a complete newbie to Linux. I've recently installed Ubuntu as a dual boot with XP on my pc. I'm gradually moving over to Ubuntu but for now I want to be able to use both, and to access the same info.

So I created a Truecrypt container in Windows but now I don't know how to access it. I've looked at the man page and I'm sure all the necessary info is there but I just dont understand it.

In Linux the file I created for the container is  /media/mount/drive/folder/file name.wmv  (I actually have a space between file and name, ist that a bad idea?)

I know it might be asking a lot but could someone walk me through how to map and mount the volume?

Thanks in advance,

jackwhite

---

