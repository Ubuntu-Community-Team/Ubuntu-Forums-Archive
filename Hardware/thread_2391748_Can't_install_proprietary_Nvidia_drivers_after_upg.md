---
title: "Can't install proprietary Nvidia drivers after upgrading 16.04 &gt; 18.04"
date: 2018-05-12
forum: Hardware
---

### Post by james_xxx on 2018-05-12
Any help would be appreciated.

I have been attempting to use ubuntu-drivers autoinstall, and this is what I see:

```
Need to get 0 B/86.3 MB of archives.
After this operation, 298 MB of additional disk space will be used.
Extracting templates from packages: 100%
(Reading database ... 240518 files and directories currently installed.)
Removing libcuda1-364 (364.19-0ubuntu0~gpu16.04.5) ...
Failed to stop var-lib-snapd-lib-gl.mount: Unit var-lib-snapd-lib-gl.mount not loaded.
dpkg: error processing package libcuda1-364 (--remove):
 installed libcuda1-364 package pre-removal script subprocess returned error exit status 5
Failed to get unit file state for var-lib-snapd-lib-gl.mount: No such file or directory
var-lib-snapd-lib-gl.mount is a disabled or a static unit, not starting it.
Removing nvidia-opencl-icd-364 (364.19-0ubuntu0~gpu16.04.5) ...
Failed to stop var-lib-snapd-lib-gl.mount: Unit var-lib-snapd-lib-gl.mount not loaded.
dpkg: error processing package nvidia-opencl-icd-364 (--remove):
 installed nvidia-opencl-icd-364 package pre-removal script subprocess returned error exit status 5
Failed to get unit file state for var-lib-snapd-lib-gl.mount: No such file or directory
var-lib-snapd-lib-gl.mount is a disabled or a static unit, not starting it.
Errors were encountered while processing:
 libcuda1-364
 nvidia-opencl-icd-364
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by james_xxx on 2018-05-20
bump

---

### Post by mörgæs on 2018-05-21
There are many threads these days dealing with upgrade problems, especially for Nvidia. Few of them seem to find an elegant solution. 

Now the problem has lasted a week. Have you considered a fresh install?

---

### Post by Yellow Pasque on 2018-05-21
Might be relevant: [https://askubuntu.com/questions/783093/installing-nvidia-opencl-icd-367-breaks-the-package-manager](https://askubuntu.com/questions/783093/installing-nvidia-opencl-icd-367-breaks-the-package-manager)

---

### Post by james_xxx on 2018-05-22
Many Thanks, Temüjin!

Part 2 of the instructions by Videonauth contained in that link were the ticket. :)

---

