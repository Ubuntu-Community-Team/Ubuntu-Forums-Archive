---
title: "Thinkpad t500 Ati 3650 problem"
date: 2012-04-14
forum: Hardware
---

### Post by Naut on 2012-04-14
Hi all! I have a problem here. I have t500 and I cant install drivers for my gpu. Whenever I try **apt-get install fglrx** it does this:  **Error! Bad return status for module build on kernel: 3.2.6 (i686) Consult the make.log in the build directory /var/lib/dkms/fglrx/8.723.1/build/ for more information. dpkg: error processing fglrx (--configure):  subprocess installed post-installation script returned error exit status 10 dpkg: dependency problems prevent configuration of fglrx-amdcccle:  fglrx-amdcccle depends on fglrx; however:   Package fglrx is not configured yet. dpkg: error processing fglrx-amdcccle (--configure):  dependency problems - leaving unconfigured No apport report written because the error message indicates its a followup error from a previous failure.               Processing triggers for initramfs-tools ... update-initramfs: Generating /boot/initrd.img-3.2.6 Errors were encountered while processing:  fglrx  fglrx-amdcccle E: Sub-process /usr/bin/dpkg returned an error code (1)**  Any help?

---

### Post by 2F4U on 2012-04-14
May I ask why don't you install the proprietary ATI drivers through the Additional Drivers program?

---

