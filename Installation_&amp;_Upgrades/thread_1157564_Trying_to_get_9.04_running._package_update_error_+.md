---
title: "Trying to get 9.04 running. package update error + no Nvidia driver"
date: 2009-05-12
forum: Installation &amp; Upgrades
---

### Post by The MAX on 2009-05-12
So I just finished installing XP, 9.04 64bit, and Win 7 RC 64bit.
After installing everything, making sure things were booting okay went to bed.

Now I'm trying to get everything set up, drivers preferences, etc...
boot into 9.04 first, there is no restricted driver listed for my 8800GT nvidia card and upon trying to install nvidia-settings it couldn't find it.
Tried to check for updates - error
sudo aot-get update -error
package manager - error 

they're all giving this sort of error.
```
Reading package lists... Error!
E: Problem parsing Provides line
E: Error occurred while processing libhk-classes-paradox (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_jaunty_universe_binary-amd64_Packages
E: The package lists or status file could not be parsed or opened.

```

if anyone has any ideas fill me in!
I'm going to try a reinstall see how that works.

---

### Post by The MAX on 2009-05-14
Reinstall worked. :)

---

### Post by 5mil3 on 2009-06-18
[https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/370294](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/370294)

sudo cd /var/lib/apt/lists
sudo rm -f *.ubuntu.*

sorted it for me, my router had dumped a load of garbage into the lists...

---

