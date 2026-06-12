---
title: "Jaunty Messing Up when trying to get some files"
date: 2009-10-02
forum: Installation &amp; Upgrades
---

### Post by kierpaul on 2009-10-02
Can anyone help here??? I get this message when trying to get a file from source site. I added a couple of lines in /etc/apt/sources.list. Any help would be greatly appreciated.

**sudo apt-get check**

Dynamic MMap ran out of room. Please increase the size of APT::Cache-Limit. Current value: 25165824. (man 5 apt.conf)
E: Error occurred while processing python-visual (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/ftp.us.debian.org_debian_dists_etch_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

---

### Post by Partyboi2 on 2009-10-02
Hi, I would suggest removing the debian repo (ftp.us.debian.org_debian) from your sources.list as that is what is more then likely causing the problem.

---

### Post by kierpaul on 2009-10-03
OK, thanks this did it for me and I appreciate it very much!

---

