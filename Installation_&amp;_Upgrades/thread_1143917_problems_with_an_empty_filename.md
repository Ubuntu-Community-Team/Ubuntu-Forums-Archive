---
title: "problems with an empty filename"
date: 2009-04-30
forum: Installation &amp; Upgrades
---

### Post by FerfNocket on 2009-04-30
first things first, I'm new to ubuntu and am really enjoying it except for a couple things, this is probably the most aggravating problem I'm having.  any help would be much appreciated. 

here is my error ```
E: /var/cache/apt/archives/acpid_1.0.6-9ubuntu4.8.10.2_i386.deb: files list file for package `libedataserver1.2-11' contains empty filename
```i get a variation of this same error with pretty much everything i try to install now.  ex.

```
E: /var/cache/apt/archives/python-problem-report_0.119.2_all.deb: files list file for package `libedataserver1.2-11' contains empty filename
```suggestions? help? encouragement? a cup of coffee?  anything is good.

thanks
ferf

---

### Post by taurus on 2009-04-30
Try to clean out the cache and then update your system again.

```
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by Bucky Ball on 2009-04-30
Try:

```
sudo apt-get update
```... in a terminal (Applications->Accessories->Terminal)

* Like Taurus said. :)

---

### Post by FerfNocket on 2009-04-30
```
(Reading database ... dpkg: error processing /var/cache/apt/archives/acpid_1.0.6-9ubuntu4.8.10.2_i386.deb (--unpack):
 files list file for package `libedataserver1.2-11' contains empty filename
Errors were encountered while processing:
 /var/cache/apt/archives/acpid_1.0.6-9ubuntu4.8.10.2_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
```this is just the error code, you want to see everything it showed me?

---

### Post by Bucky Ball on 2009-04-30
You might get some clues here:

[http://ubuntuforums.org/showthread.php?p=2938785](http://ubuntuforums.org/showthread.php?p=2938785)

[http://ubuntuforums.org/showthread.php?t=21672](http://ubuntuforums.org/showthread.php?t=21672)

I´m guessing you still have some 8.10 repos listed in your sources list and they are not co-operating so could you post that:
```

sudo nano /etc/apt/sources.list
```

You can comment out the offending line like this:

```
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) hardy universe
```

(It will be a different entry to this containing 8.10 details)

---

