---
title: "update-manager -d fails"
date: 2008-08-30
forum: General Help
---

### Post by Xamiga on 2008-08-30
Any idea what to do about this repeating error?

root@al-tob:/# update-manager -d
extracting 'intrepid.tar.gz'
authenticate 'intrepid.tar.gz' against 'intrepid.tar.gz.gpg' 
exception from gpg: GnuPG exited non-zero, with code 131072
Debug information: 

gpg: WARNING: unsafe permissions on homedir `/tmp/tmpNeQUzv'

gpg: verify signatures failed: eof

I am at:

Kernel:        2.6.24-21-generic
Gnome:         2.22.3
GCC:           4.2.3 (i486-linux-gnu)
X-org version: unknown (13 June 2008  01:08:21AM)

---

### Post by tamoneya on 2008-08-30
looks identical to this thread: [http://ubuntuforums.org/showthread.php?t=801851](http://ubuntuforums.org/showthread.php?t=801851)

---

### Post by cariboo on 2008-08-30
IF you want to give intrepid a try I would suggest doing a clean install from the Alpha4 iso as there are a lot of changes being made to the nvidia drivers and kernels. Be aware that this is an alpha release, because there are a lot of things that don't work the way you would expect them to. Also be prepared to roll up your sleeves and fix things as they break with updates. You can get the iso here:

 [http://cdimage.ubuntu.com/releases/intrepid/alpha-4/](http://cdimage.ubuntu.com/releases/intrepid/alpha-4/)

Jim

---

### Post by tamoneya on 2008-08-30
> **cariboo907 said:**
> IF you want to give intrepid a try I would suggest doing a clean install from the Alpha4 iso as there are a lot of changes being made to the nvidia drivers and kernels. Be aware that this is an alpha release, because there are a lot of things that don't work the way you would expect them to. Also be prepared to roll up your sleeves and fix things as they break with updates. You can get the iso here:

 [http://cdimage.ubuntu.com/releases/intrepid/alpha-4/](http://cdimage.ubuntu.com/releases/intrepid/alpha-4/)

Jim

It is important though to debug the upgrade process as well.  There will be many people who use the upgrade instead of reinstall so we need to fix the bugs in it.  If all the testers just did fresh reinstalls we would never solve the bugs.  Personally I like to do fresh installs but for the purpose of testing I try the upgrades about half the time.

---

