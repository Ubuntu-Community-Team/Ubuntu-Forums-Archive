---
title: "Sub-process bzip2 returned an error code (2)"
date: 2009-05-28
forum: Installation &amp; Upgrades
---

### Post by Goregasm on 2009-05-28
Hello, newbie here.

I just installed 9.04 for the second time due to an error, but still it persists. After fresh-install I want to install a few applications but I have some error with the repositories. With the default installation I have universe and multiverse repositories on Portuguese mirrors, but after the first errors, I changed it to use only the canonical on main server, but still it does not work.


```
flux@flux:~$ sudo apt-get update
[sudo] password for flux: 
Hit http://archive.ubuntu.com jaunty Release.gpg
Ign http://archive.ubuntu.com jaunty/main Translation-en_US
Hit http://archive.ubuntu.com jaunty-updates Release.gpg
Ign http://archive.ubuntu.com jaunty-updates/main Translation-en_US
Hit http://archive.ubuntu.com jaunty-security Release.gpg
Ign http://archive.ubuntu.com jaunty-security/main Translation-en_US
Hit http://archive.ubuntu.com jaunty Release
Hit http://archive.ubuntu.com jaunty-updates Release
Hit http://archive.ubuntu.com jaunty-security Release
Get:1 http://archive.ubuntu.com jaunty/main Packages [1253kB]
Hit http://archive.ubuntu.com jaunty-updates/main Packages
Hit http://archive.ubuntu.com jaunty-security/main Packages
99% [1 Packages bzip2 2977792]                
bzip2: Data integrity error when decompressing.
	Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Err http://archive.ubuntu.com jaunty/main Packages
  Sub-process bzip2 returned an error code (2)
Fetched 1253kB in 4s (295kB/s)
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty/main/binary-i386/Packages.bz2  Sub-process bzip2 returned an error code (2)

E: Some index files failed to download, they have been ignored, or old ones used instead.

```

Already tried to re-install/remove+add the bzip2 package but did not work. In fact when I removed it, it asked to remove 3 other packages and now i can't add them due to errors.

I searched and found no suitable solution. Most of them were network problems due to proxies but I'm writing this post on the troubled machine behind nat on a soho router.

---

### Post by Goregasm on 2009-05-29
Can anyone help me? At least, do you think this might be an hardware error? I already tested the ram with no errors. Changing the motherboard to get the same results would be too much pain.

---

### Post by Partyboi2 on 2009-05-29
Hi, open a terminal and try
```
sudo apt-get clean
sudo apt-get update
```

---

### Post by dregin on 2009-10-04
I have the same issue with 9.04 :(

apt-get clean didn't make a difference.

Any help would be much appreciated.

---

