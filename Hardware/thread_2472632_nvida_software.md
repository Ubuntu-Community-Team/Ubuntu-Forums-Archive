---
title: "nvida software"
date: 2022-03-07
forum: Hardware
---

### Post by th1bill on 2022-03-07
```
illis@willis-AX370M-DS3H:~$ sudo apt install nvidia-driver-470
Reading package lists... Done
Building dependency tree       
Reading state information... Done
nvidia-driver-470 is already the newest version (470.103.01-0ubuntu0.20.04.1).



The following packages were automatically installed and are no longer required:
  libllvm11 libllvm11:i386 shim
Use 'sudo apt autoremove' to remove them.




0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] 





Setting up amdgpu-dkms (1:5.6.0.15-1098277) ...
Removing old amdgpu-5.6.0.15-1098277 DKMS files...

------------------------------
Deleting module version: 5.6.0.15-1098277
completely from the DKMS tree.
------------------------------
Done.
Loading new amdgpu-5.6.0.15-1098277 DKMS files...
Building for 5.13.0-30-generic
Building for architecture x86_64
Building initial module for 5.13.0-30-generic
ERROR: Cannot create report: [Errno 17] File exists: '/var/crash/amdgpu-dkms-fir
mware.0.crash'
Error! Bad return status for module build on kernel: 5.13.0-30-generic (x86_64)
Consult /var/lib/dkms/amdgpu/5.6.0.15-1098277/build/make.log for more informatio
n.
dpkg: error processing package amdgpu-dkms (--configure):
 installed amdgpu-dkms package post-installation script subprocess returned erro
r exit status 10
dpkg: dependency problems prevent configuration of amdgpu:
 amdgpu depends on amdgpu-dkms (= 1:5.6.0.15-1098277); however:
  Package amdgpu-dkms is not configured yet.

dpkg: error processing package amdgpu (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup erro
r from a previous failure.
                          Errors were encountered while processing:
 amdgpu-dkms
 amdgpu
E: Sub-process /usr/bin/dpkg returned an error code (1)
willis@willis-AX370M-DS3H:~$ 
```


My screen, suddenly, went medium dark and the computer quit as I typoed on a forum.  I'm lost.

---

### Post by SeijiSensei on 2022-03-07
The best solution for installing NVIDIA drivers is always to use the "Driver Manager" that comes with Ubuntu.

---

### Post by deadflowr on 2022-03-07
You don't have an Nvidia issue. That's installed fine, according to the output.
You have an amdgpu issue for whatever reason.
We'd probably need more info about the machine or your particular setup to help figure out what is what.

---

### Post by #&amp;thj^% on 2022-03-07
> **deadflowr said:**
> You don't have an Nvidia issue. That's installed fine, according to the output.
**_You have an amdgpu issue for whatever reason._**
We'd probably need more info about the machine or your particular setup to help figure out what is what.

+1
How about showing us:
```
dkms status
```
and:
```
apt policy amdgpu amdgpu-dkms
```
**Don't do this yet!** You can also go here to get amd-drivers: [https://www.amd.com/en/support/kb/release-notes/rn-amdgpu-unified-linux-21-40-2](https://www.amd.com/en/support/kb/release-notes/rn-amdgpu-unified-linux-21-40-2)

---

### Post by th1bill on 2022-03-08
> **1fallen said:**
> +1
How about showing us:
```
dkms status
```
and:
```
apt policy amdgpu amdgpu-dkms
```
**Don't do this yet!** You can also go here to get amd-drivers: [https://www.amd.com/en/support/kb/release-notes/rn-amdgpu-unified-linux-21-40-2](https://www.amd.com/en/support/kb/release-notes/rn-amdgpu-unified-linux-21-40-2)

```
willis@willis-AX370M-DS3H:~$ dkms status
amdgpu, 5.6.0.15-1098277: added
nvidia, 470.103.01, 5.13.0-30-generic, x86_64: installed
willis@willis-AX370M-DS3H:~$ apt policy amdgpu amdgpu-dkms
amdgpu:
  Installed: 20.20-1098277
  Candidate: 20.20-1098277
  Version table:
 *** 20.20-1098277 1000
        500 file:/var/opt/amdgpu-pro-local ./ Packages
        100 /var/lib/dpkg/status
amdgpu-dkms:
  Installed: 1:5.6.0.15-1098277
  Candidate: 1:5.6.0.15-1098277
  Version table:
 *** 1:5.6.0.15-1098277 1000
        500 file:/var/opt/amdgpu-pro-local ./ Packages
        100 /var/lib/dpkg/status
```


Thank you, I was just looking for what data was needed because I had decided the samething.

---

### Post by oldos2er on 2022-03-08
Please share your system specs, particularly video hardware.

---

