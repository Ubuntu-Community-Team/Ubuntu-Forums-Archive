---
title: "Dpkg broken - unable to install any packages"
date: 2009-01-30
forum: Installation &amp; Upgrades
---

### Post by dashinganicool007 on 2009-01-30
I can't install any packages because the following 3 packages are not properly configured. When I try to configure the following is the output:
> 
$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 88 not upgraded.
3 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up linux-image-2.6.27-9-generic (2.6.27-9.19) ...
Running depmod.
/usr/sbin/update-initramfs: 1: curity4cert15X509CRLSelector14setDateAndTimeEJvPNS_4util4DateE_ZN4java8security4cert15X509CRLSelector22getCertificateCheckingEJPNS1_15X509CertificateEv_ZN4java8security4cert15X509CRLSelector22setCertificateCheckingEJvPNS1_15X509CertificateE_ZN4java8security4cert15X509CRLSelector8toStringEJPNS_4lang6StringEv_ZN4java8security4cert15X509CRLSelector6class: File name too long
Failed to create initrd image.
dpkg: error processing linux-image-2.6.27-9-generic (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.27-9-generic:
 linux-restricted-modules-2.6.27-9-generic depends on linux-image-2.6.27-9-generic; however:
  Package linux-image-2.6.27-9-generic is not configured yet.
dpkg: error processing linux-restricted-modules-2.6.27-9-generic (--configure):
 dependency problems - leaving unconfigured
Setting up console-setup (1.25ubuntu4) ...
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                           * Saving console font and keymap for next boot...                                                                          [ OK ] 
/usr/sbin/update-initramfs: 1: curity4cert15X509CRLSelector14setDateAndTimeEJvPNS_4util4DateE_ZN4java8security4cert15X509CRLSelector22getCertificateCheckingEJPNS1_15X509CertificateEv_ZN4java8security4cert15X509CRLSelector22setCertificateCheckingEJvPNS1_15X509CertificateE_ZN4java8security4cert15X509CRLSelector8toStringEJPNS_4lang6StringEv_ZN4java8security4cert15X509CRLSelector6class: File name too long
dpkg: error processing console-setup (--configure):
 subprocess post-installation script returned error exit status 127
Errors were encountered while processing:
 linux-image-2.6.27-9-generic
 linux-restricted-modules-2.6.27-9-generic
 console-setup
E: Sub-process /usr/bin/dpkg returned an error code (1)


Help please!
TIA

---

### Post by lemming465 on 2009-02-01
Does```
sudo -i
apt-get clean
apt-get update
apt-get upgrade --fix-broken
``` improve things any?

---

