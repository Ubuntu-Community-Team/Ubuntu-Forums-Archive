---
title: "synaptic / apt error"
date: 2009-10-01
forum: Installation &amp; Upgrades
---

### Post by dreamingdarkness on 2009-10-01
After the kernel changes and associated releases made a couple nights ago, and the installation of Firestarter and fslint (only changes made to  system), I'm no longer able to get apt or synaptic to sync without disabling the mediabuntu repository. Looks like a file's locked, doesn't clear up on reboot/etc. Firestarter's been uninstalled. I also noticed some network issues with the Ubuntu box communicating badly to its gateway and modem on the local net addresses, but I may address that later.
This is on Ubuntu 9.04, 64bit.

Here's the message:
```
Failed to fetch http://packages.medibuntu.org/dists/jaunty/free/binary-amd64/Packages.bz2  rename failed, Operation not permitted (/var/lib/apt/lists/partial/packages.medibuntu.org_dists_jaunty_free_binary-amd64_Packages.decomp -> /var/lib/apt/lists/packages.medibuntu.org_dists_jaunty_free_binary-amd64_Packages).
Some index files failed to download, they have been ignored, or old ones used instead.
```

When I check in the specified directory:
```
-rw-r-----     1 root root     0 2009-04-20 08:01 lock
?-wsrw-rwt 44928 5236 50340 3.7G 1969-10-18 05:18 packages.medibuntu.org_dists_jaunty_free_binary-amd64_Packages
-rw-r--r--     1 root root   11K 2009-09-27 03:19 packages.medibuntu.org_dists_jaunty_free_source_Sources
-rw-r--r--     1 root root   30K 2009-09-27 03:19 packages.medibuntu.org_dists_jaunty_non-free_binary-amd64_Packages
-rw-r--r--     1 root root   21K 2009-09-27 03:19 packages.medibuntu.org_dists_jaunty_non-free_source_Sources
-rw-r--r--     1 root root   12K 2009-09-27 03:19 packages.medibuntu.org_dists_jaunty_Release
-rw-r--r--     1 root root   197 2009-09-27 03:19 packages.medibuntu.org_dists_jaunty_Release.gpg

```

It looks to me like the packages.medibuntu.org_dists_jaunty_free_binary-amd64_Packages is either corrupted or has bad permissions.
Unfortunately, I'm not certain what the best option at this stage is.
All I can think of is:
1. Chmod that bugger to match the permissions of all the others?
2. Delete the bugger and see if re-running synaptic or apt-get update will fix?
3. Other thoughts or suggestions?

---

### Post by oldos2er on 2009-10-01
"2. Delete the bugger and see if re-running synaptic or apt-get update will fix?"

 Slightly less drastic would be to rename the file (you'll need sudo privileges to do so) first. You can always rename it again if this fails.

---

### Post by dreamingdarkness on 2009-10-01
Thanks oldos2er, I'll give a rename a try before I smite it from upon high. Never a bad idea to be safe, 's true.

---

