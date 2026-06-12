---
title: "Kernelcheck 404 error"
date: 2009-09-21
forum: Installation &amp; Upgrades
---

### Post by HandyBob on 2009-09-21
Hi,

I just installed KernelCheck, but got following error when I click the "Get Kernel information" button
"Kernel.org server couldn't fulfill request. Error code: 404"

In the main.py file I noticed following url which appears to be dead:
"[http://master.kernel.org/kdist/fragments/stable.html](http://master.kernel.org/kdist/fragments/stable.html)"
it should be:
"[http://master.kernel.org/kdist/fragments.disabled/stable.html]("http://master.kernel.org/kdist/fragments/stable.html")"

there are 2 more links like this in the file.

Maybe there's a reason why they added .disabled to the url, but from what I could understand from the code it's used to check the latest stable version number and download it.
I found these url's by going backwards. If you go to [http://master.kernel.org/kdist/](http://master.kernel.org/kdist/) , you can figure out the rest.

Just thought this could help someone somewhere.

---

### Post by master_kernel on 2009-10-19
Fixed, see [https://bugs.launchpad.net/kernelcheck/+bug/432732](https://bugs.launchpad.net/kernelcheck/+bug/432732)

---

### Post by marksken on 2009-11-03
Any luck we can get a fixed version ? or just the patched files so we only have to replace them?

Need to compile my kernel for ubuntu 9.10 to get my dvd-drive working, used kernel check for my 9.04 kernel also really liked it

---

### Post by quazar on 2010-01-12
[http://launchpadlibrarian.net/35212126/kernelcheck_1.2.5-3_all.deb](http://launchpadlibrarian.net/35212126/kernelcheck_1.2.5-3_all.deb)

This version does work! The version number is the same, but this version has a fixed script.

---

### Post by markackerman8@gmail.com on 2010-04-11
worked for me thanks!!!!

oops spoke too soon, now it just doesn't do anything when I click "Get Kernel Info", Anyone have it working?

---

### Post by Gi0tis on 2010-04-16
> **markackerman8@gmail.com said:**
> worked for me thanks!!!!

oops spoke too soon, now it just doesn't do anything when I click "Get Kernel Info", Anyone have it working?
No idea what happened.Its been a while since i have the same issue.

---

### Post by master_kernel on 2010-04-17
The kernel.org structure changed again, but it's been patched.

DEB package: [http://ubuntuforums.org/showpost.php?p=9133861&postcount=500](http://ubuntuforums.org/showpost.php?p=9133861&postcount=500)
Bug report: [https://bugs.launchpad.net/kernelcheck/+bug/555979](https://bugs.launchpad.net/kernelcheck/+bug/555979)

---

