---
title: "apt-get update generates erros on new install"
date: 2009-09-11
forum: Installation &amp; Upgrades
---

### Post by BarnesK on 2009-09-11
I have a fresh install of 8.04 server, 64-bit. No changes have been made to the installation and apt-get is the very first command executed on the server. When I try to do an apt-get update, I get the following errors:
 
sudo apt-get update
 
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg 
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release.gpg 
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_US 
98% [3 Translation-en_US bzip2 0] [Waiting for headers] [Connecting to securitybzip2: (stdin) is not a bzip2 file.
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_US 
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Translation-en_US 
72% [4 Translation-en_US bzip2 0] [Connecting to us.archive.ubuntu.com (91.189.bzip2: (stdin) is not a bzip2 file.
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Translation-en_US 
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_US 
58% [5 Translation-en_US bzip2 0] [Waiting for headers] [Connecting to securitybzip2: (stdin) is not a bzip2 file.
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_US 
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Translation-en_US 
47% [6 Translation-en_US bzip2 0] [Connecting to us.archive.ubuntu.com (91.189.bzip2: (stdin) is not a bzip2 file.
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Translation-en_US 
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_US 
40% [7 Translation-en_US bzip2 0] [Waiting for headers] [Connecting to securitybzip2: (stdin) is not a bzip2 file.
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_US 
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Translation-en_US 
35% [8 Translation-en_US bzip2 0] [Connecting to us.archive.ubuntu.com (91.189.bzip2: (stdin) is not a bzip2 file.
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Translation-en_US 
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_US 
31% [9 Translation-en_US bzip2 0] [Waiting for headers] [Connecting to securitybzip2: (stdin) is not a bzip2 file.
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_US 
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Translation-en_US 
28% [10 Translation-en_US bzip2 0] [Connecting to us.archive.ubuntu.com (91.189bzip2: (stdin) is not a bzip2 file.
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Translation-en_US 
Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release.gpg 
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release 
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release 
 
Get:13 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Translation-en_US 
36% [13 Translation-en_US bzip2 0] [Connecting to us.archive.ubuntu.com (91.189bzip2: (stdin) is not a bzip2 file.
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Translation-en_US 
Get:14 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Translation-en_US 
33% [14 Translation-en_US bzip2 0] [Connecting to us.archive.ubuntu.com (91.189bzip2: (stdin) is not a bzip2 file.
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Translation-en_US 
Get:15 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Translation-en_US 
31% [15 Translation-en_US bzip2 0] [Connecting to us.archive.ubuntu.com (91.189bzip2: (stdin) is not a bzip2 file.
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Translation-en_US 
Get:16 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Translation-en_US 
29% [16 Translation-en_US bzip2 0] [Connecting to us.archive.ubuntu.com (91.189bzip2: (stdin) is not a bzip2 file.
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Translation-en_US 
Get:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release 
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release 
 
Get:18 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release 
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release
 
Fetched 5150B in 1min14s (69B/s)
Reading package lists... Done
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release: The following signatures were invalid: NODATA 1 NODATA 2
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release: The following signatures were invalid: NODATA 1 NODATA 2
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release: The following signatures were invalid: NODATA 1 NODATA 2
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/Release](http://security.ubuntu.com/ubuntu/dists/hardy-security/Release) 
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy/Release](http://us.archive.ubuntu.com/ubuntu/dists/hardy/Release) 
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release](http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release) 
W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems
 
 
I have tried apt-get clear and also pointing to different repositories. Neither has resulted in a change. An installation of Red Hat on this same machine & IP was able to operate normally, so it doesn't appear to be a firewall issue. There is no proxy. Multiple installs produce the same results. I am uncertain where to proceed from here.
 
I have not found anything in the forums to date that seem to deal with this specific issue. A pointer to another thread would be great if there's already a solution out there.

---

### Post by Skilly on 2009-11-07
Are you running apt-cacher by any chance?

---

