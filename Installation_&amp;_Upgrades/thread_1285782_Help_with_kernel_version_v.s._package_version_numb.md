---
title: "Help with kernel version v.s. package version numbers"
date: 2009-10-08
forum: Installation &amp; Upgrades
---

### Post by lunarlatte on 2009-10-08
Recently I read [http://www.ubuntu.com/usn/USN-819-1](http://www.ubuntu.com/usn/USN-819-1) which explains about a kernel bug fix for CVE-2009-2692.  I'm running Ubuntu 8.10.  The article says to install one of the following to fix the problem:

  linux-image-2.6.27-14-generic   2.6.27-14.39
linux-image-2.6.27-14-server    2.6.27-14.39
linux-image-2.6.27-14-virtual   2.6.27-14.39

Okay.  From this I decide I need .39 or higher and I chose the generic one to be appropriate to my needs.  This is where the confusion begins.  I ran "apt-get update" followed by synaptic.  When choosing a high version linux-image from synaptic I'm told that I should actually be installing the meta package so the correct associated tools are installed too.  The problem is I can't tell from looking at the meta package what the exact kernel version is it installs.  After installing the meta package "uname -r" only tells me I have kernel version 2.6.27-14-generic installed.  I don't know if this is actually version:
2.6.27-14.37 or 2.6.27-14.39 or 2.6.27-14.40 or 2.6.27-14.41??

Please tell me how to identify the exact version of kernel I'm running and also how to know precisely which kernel the linux-image meta package points to (prefereably before installing it?)

---

