---
title: "upgrade 8.10 -&gt; 9.04 finshed w/ errors"
date: 2009-05-05
forum: Installation &amp; Upgrades
---

### Post by ForMar on 2009-05-05
So I upgraded from 8.10 -> 9.04 today but it finished with errors, unfortunately I didn't actually look at the errors so after combing through the log files I *think* I found what the errors are.

The fail path: /var/log/dist-upgrade/main.log

I used "grep 'error' 'warning' main.log" to find the errors and they were:
```
main.log:2009-05-05 00:14:28,150 ERROR got an error from dpkg for pkg: 'ca-certificates': 'subprocess post-installation script returned error exit status 1
main.log:2009-05-05 00:14:28,150 DEBUG running apport_pkgfailure() ca-certificates: subprocess post-installation script returned error exit status 1
main.log:2009-05-05 00:14:28,188 ERROR got an error from dpkg for pkg: 'ca-certificates': 'subprocess post-installation script returned error exit status 1
main.log:2009-05-05 00:18:37,405 ERROR got an error from dpkg for pkg: 'libcurl3-gnutls': 'dependency problems - leaving unconfigured
main.log:2009-05-05 00:18:37,405 ERROR got an error from dpkg for pkg: 'libcurl3-gnutls': 'dependency problems - leaving unconfigured
main.log:2009-05-05 00:18:38,197 ERROR got an error from dpkg for pkg: 'openoffice.org-core': 'dependency problems - leaving unconfigured
main.log:2009-05-05 00:18:38,198 ERROR got an error from dpkg for pkg: 'openoffice.org-core': 'dependency problems - leaving unconfigured
main.log:2009-05-05 00:18:38,434 ERROR got an error from dpkg for pkg: 'python-uno': 'dependency problems - leaving unconfigured
main.log:2009-05-05 00:18:38,434 ERROR got an error from dpkg for pkg: 'python-uno': 'dependency problems - leaving unconfigured
main.log:2009-05-05 00:20:21,017 ERROR got an error from dpkg for pkg: 'libraptor1': 'dependency problems - leaving unconfigured
main.log:2009-05-05 00:20:21,018 ERROR got an error from dpkg for pkg: 'libraptor1': 'dependency problems - leaving unconfigured
main.log:2009-05-05 00:20:21,025 ERROR got an error from dpkg for pkg: 'tracker': 'dependency problems - leaving unconfigured
main.log:2009-05-05 00:20:21,025 ERROR got an error from dpkg for pkg: 'tracker': 'dependency problems - leaving unconfigured
main.log:2009-05-05 00:20:21,033 ERROR got an error from dpkg for pkg: 'libdeskbar-tracker': 'dependency problems - leaving unconfigured
main.log:2009-05-05 00:20:21,033 ERROR got an error from dpkg for pkg: 'libdeskbar-tracker': 'dependency problems - leaving unconfigured
main.log:2009-05-05 00:20:22,649 ERROR got an error from dpkg for pkg: 'audacious-plugins-extra': 'dependency problems - leaving unconfigured
main.log:2009-05-05 00:20:22,650 ERROR got an error from dpkg for pkg: 'audacious-plugins-extra': 'dependency problems - leaving unconfigured
main.log:2009-05-05 00:20:35,781 ERROR got an error from dpkg for pkg: 'openoffice.org-base-core': 'dependency problems - leaving unconfigured

``` 

There is actually about four times that but you get the idea. Any help would be very appreciated 

THANKS for your time
terterm.log:jaunty: Fatal IO error 9 (Bad file descriptor) on X server :0.0.m.log:jaunty: Fatal IO error 9 (Bad file descriptor) on X server :0.0.
EDIT: 
after combing through some more files I found a few more errors @ /var/log/dist-upgrade/term.log

errors are as follows: 
term.log:invoke-rc.d: release upgrade in progress, error is not fatal
term.log:invoke-rc.d: release upgrade in progress, error is not fatal
term.log:jaunty: Fatal IO error 9 (Bad file descriptor) on X server :0.0.

again thanks for your time

---

### Post by dstew on 2009-05-05
Did you try```
sudo apt-get update
sudo apt-get upgrade
```Sometimes that will fix an incomplete upgrade.

---

### Post by ForMar on 2009-05-05
> **dstew said:**
> Did you try```
sudo apt-get update
sudo apt-get upgrade
```Sometimes that will fix an incomplete upgrade.

No that didn't seem to do anything :(

---

### Post by dstew on 2009-05-05
Does the newly installed system work at all? Do you get a desktop?

---

### Post by ForMar on 2009-05-05
> **dstew said:**
> Does the newly installed system work at all? Do you get a desktop?

yea everything seems to work fine.

---

### Post by dstew on 2009-05-06
Does the word processor (Open Office) work?

---

### Post by ForMar on 2009-05-06
It does 


Also thank you for taking time to replay and think on my behalf :)

---

### Post by dstew on 2009-05-06
When you did```
sudo apt-get update
sudo apt-get upgrade
```did you get any error messages?

Since you got an error that says ```
'openoffice.org-core': 'dependency problems - leaving unconfigured
```yet open office works, I think it might have corrected itself during an update or some other time. I wouldn't worry about the error messages unless you have some loss in functionality.

---

### Post by ForMar on 2009-05-06
I hadn't gotten any error messages when I use apt-get. 
Well i hope it corrected it self then :) I really appreciate your time!

---

