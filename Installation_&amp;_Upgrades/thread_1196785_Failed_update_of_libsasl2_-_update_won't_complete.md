---
title: "Failed update of libsasl2 - update won't complete"
date: 2009-06-25
forum: Installation &amp; Upgrades
---

### Post by Laysan_A on 2009-06-25
Hi,

I was updating the libsasl2 security update when I had a sudden freeze to black and had to hit the power button (first one in five days - actually had two in a row - but that's another story). They still showed in the K packager manager (don't remember what it's called), but when I tried to re-do the update it just errored out.

How can I fix this?

Here's the error message:

/var/cache/apt/archives/libsasl2-dev_2.1.22.dfsg1-23ubuntu3.1_amd64.deb E: Invalid archive signature E: Prior errors apply to /var/cache/apt/archives/libsasl2-dev_2.1.22.dfsg1-23ubuntu3.1_amd64.deb E: Invalid archive signature E: Prior errors apply to /var/cache/apt/archives/libsasl2-2_2.1.22.dfsg1-23ubuntu3.1_amd64.deb E: Invalid archive signature E: Prior errors apply to /var/cache/apt/archives/libsasl2-modules_2.1.22.dfsg1-23ubuntu3.1_amd64.deb debconf: apt-extracttemplates failed: Illegal seek E: Invalid archive signature E: Prior errors apply to /var/cache/apt/archives/libsasl2-dev_2.1.22.dfsg1-23ubuntu3.1_amd64.deb E: Invalid archive signature E: Prior errors apply to /var/cache/apt/archives/libsasl2-2_2.1.22.dfsg1-23ubuntu3.1_amd64.deb E: Invalid archive signature E: Prior errors apply to /var/cache/apt/archives/libsasl2-modules_2.1.22.dfsg1-23ubuntu3.1_amd64.deb debconf: apt-extracttemplates failed: Illegal seek E: Invalid archive signature E: Prior errors apply to /var/cache/apt/archives/libsasl2-dev_2.1.22.dfsg1-23ubuntu3.1_amd64.deb E: Invalid archive signature E: Prior errors apply to /var/cache/apt/archives[/code]/libsasl2-2_2.1.22.dfsg1-23ubuntu3.1_amd64.deb E: Invalid archive signature E: Prior errors apply to /var/cache/apt/archives/libsasl2-modules_2.1.22.dfsg1-23ubuntu3.1_amd64.deb debconf: apt-extracttemplates failed: Illegal seek

---

### Post by Laysan_A on 2009-06-26
Okay, since no one was willing or able to help, I decided to try something myself and hope I didn't break my system doing it. I opened aptitude and cleared the cache. The aptitude terminal gui opened but after about an hour of trying to figure out how to make it apply the updates it showed me, I gave up and closed the terminal. 

I opened update notifier, applied all the updates, and they appeared to all have downloaded and installed properly. :D Hurray!

---

### Post by john.oneill on 2009-12-08
Hi Layson_A,

Thank you so much for this post.  I encountered almost the exact same issue:

I had a broken package and tried 'sudo apt-get -f install' -- outcome here:

E: Invalid archive signature
E: Prior errors apply to /var/cache/apt/archives/python2.6-minimal_2.6.4-0ubuntu3_amd64.deb
debconf: apt-extracttemplates failed: Bad file descriptor
dpkg-deb: `/var/cache/apt/archives/python2.6-minimal_2.6.4-0ubuntu3_amd64.deb' is not a debian format archive
dpkg: error processing /var/cache/apt/archives/python2.6-minimal_2.6.4-0ubuntu3_amd64.deb (--unpack):
 subprocess dpkg-deb --control returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/python2.6-minimal_2.6.4-0ubuntu3_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

I looked for about 30 minutes before I found your post - fixed me right up.  Just needed to clear the cache (used aptitude as you did) and all good.  No one may have answered your post but thank you for posting - helped me greatly.

---

