---
title: "Scanner Not in Sane Whitelist"
date: 2018-08-03
forum: Hardware
---

### Post by eldavar on 2018-08-03
Hello. 

I just purchased a brand new [Avision scanner model # AW210]("http://a.co/gEcZRRo"). I selected it because the description specifically mentioned Linux as a supported OS (I'm running Ubuntu 18.04 LTS). Also, according to [hamrick.com]("https://www.hamrick.com/vuescan/avision_aw210.html"), the AW210 can be used on Linux without installing any other software. 


The scanner was automatically detected by Sane, but it won't function and isn't detected by any scanning software. I installed the driver file from the included CD, a file named "avision-sane-backend_0.1.0-17158_amd64.deb" and it had a file creation date of 06/17/2017. It installed without issue. However, the scanner is still not functional, even after all the usual basic troubleshooting steps like powering the device off and on again, and rebooting my computer. 


I followed instructions found on Ubuntu Help regarding [installing a scanner that isn't auto-detected]("https://help.ubuntu.com/community/SANE%20-%20Installing%20a%20scanner%20that%20isn%27t%20auto-detected"). Those instructions said to run ```
sane-find-scanner
``` in a terminal and make a note of the scanner's vendor ID and product ID, which I did. 

[IMG]https://drive.google.com/file/d/0B95vSnznZK-adVpJYWhEU3dCNnY4X1VNbTFFT2RXZXc2UGlF/view?usp=sharing[/IMG]
[https://asb5lg.bn.files.1drv.com/y4mUo1CnfT9zr-_CXTYaMz4qbef0kGsw61E8Nk5-iLhkesio351z6Nhl34wkOijjuIdc3faWcLMKlc5T-l8APXC8AxZ_m5U7WGwCTwduTa7kU5jlZv8QkJtbfnGABHzM209O-I45OL4qx-ZoiL4ZFl7cPVRT59iQf6fN9Ti0dze1rdGSvsGAVsf5Hjxhxw_KWIVt0Jc6JgqCbF_3s2KW6QVzQ?width=848&height=553&cropmode=none](https://asb5lg.bn.files.1drv.com/y4mUo1CnfT9zr-_CXTYaMz4qbef0kGsw61E8Nk5-iLhkesio351z6Nhl34wkOijjuIdc3faWcLMKlc5T-l8APXC8AxZ_m5U7WGwCTwduTa7kU5jlZv8QkJtbfnGABHzM209O-I45OL4qx-ZoiL4ZFl7cPVRT59iQf6fN9Ti0dze1rdGSvsGAVsf5Hjxhxw_KWIVt0Jc6JgqCbF_3s2KW6QVzQ?width=848&height=553&cropmode=none)

The next step was to edit the avision.conf file to add the vendor & product ID numbers, which I did.

[https://asb4lg.bn.files.1drv.com/y4mDehxs5dhYiRQ0ZUmi02ylbm9C0z7i7C9Mz-GddMx-0lpMRfFKCCxvZwKPmWiSGpAbJkaSGmJwnuiEYAZCUYUJwpzEcATf8QhLhoMYU3p2dbvplBY6LbdOWZA9YW6sLv2ZQ27544m45It9fKXKVyEaJCyMsz8QG8L7vxn1g8lOoZ6rdv8RKQEXmXR4GIw7F52RClF0xq6s6QLQJnyJVZDUw?width=1014&height=635&cropmode=none](https://asb4lg.bn.files.1drv.com/y4mDehxs5dhYiRQ0ZUmi02ylbm9C0z7i7C9Mz-GddMx-0lpMRfFKCCxvZwKPmWiSGpAbJkaSGmJwnuiEYAZCUYUJwpzEcATf8QhLhoMYU3p2dbvplBY6LbdOWZA9YW6sLv2ZQ27544m45It9fKXKVyEaJCyMsz8QG8L7vxn1g8lOoZ6rdv8RKQEXmXR4GIw7F52RClF0xq6s6QLQJnyJVZDUw?width=1014&height=635&cropmode=none)

However, neither XSane nor Simple Scan are detecting this device, even if I run them as root. I called the Avision tech support number, but nobody there knows anything about Linux and the rep told me it's probably best to just return the scanner and search for another one. The problem is that I can't find any other scanners with a document feeder that support Linux and don't cost upwards of $300 (this one was $150 and would be perfect if it worked). 

Does anybody here know how to make this scanner work? Is there a way I can edit the "whitelist" that the Sane error mentions? Or, would that attempt be just a total waste of time? 

Thanks!

---

### Post by bigpicturemachine on 2018-08-03
Hey, add the sane stable and git ppa : sudo add-apt-repository ppa:rolfbensch/sane-git  , his other ppa is listed on that ppa page then update, full upgrade and reboot.

---

### Post by eldavar on 2018-08-04
I added those PPAs but it seems like that may have created even more problems. 

Now, when I try to run [FONT=courier new]**scanimage -L**[/FONT] it returns [FONT=courier new][B]Segmentation fault (core dumped)

[/B][/FONT]It also pops up the error box "Sorry, the application scanimage has stopped unexpectedly." I'm not sure exactly what parts of the details are necessary here, but here's the basics that might be relevant:

```
ExecutablePath
   /usr/bin/scanimage

Package
   sane-utils 1.0.27+git20180730-bionic0 [origin: LP-PPA-rolfbensch-sane-git]

Problem Type
   Crash

Title
   scanimage crashed with SIGSEGV in __pthread_initialize_minimal_internal()

Architecture
   amd64

Date
   Sat Aug 4 11:55:42 2018

DistroRelease
   Ubuntu 18.04

ProcCmdline
   scanimage -L

SegvAnalysis
   Segfault happened at: 0x7f96fc047edb <_pthread_initialize_minimal_internal+91>:   mov   0x968(%rbp),%rax
   PC (0x7f96fc047edb) ok
   source "0x968(%rbp)" (0x00000968) not located in a known VMA region (needed readable region)!
   destination "%rax" ok

SegvReason
   reading NULL VMA

StacktraceTop
   __pthread_initialize_minimal_internal () at nptl-init.c:294
   _init () at ../sysdeps/x86_64/crti.S:72
   ?? ()

Tags
   bionic third-party-packages

Uname
   Linux 4.15.0-29-generic x86_64

Unreportable Reason
   This is not an official Ubuntu package. Please remove any third party package and try again.
```

The SegvAnalysis references a readable region (looks like that's missing?). Please let me know if anything here is helpful in getting this resolved, or if there's more info that's necessary!

---

