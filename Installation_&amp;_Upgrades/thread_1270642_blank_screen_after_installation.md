---
title: "blank screen after installation"
date: 2009-09-19
forum: Installation &amp; Upgrades
---

### Post by talkingtree on 2009-09-19
hi,

I have installed ubuntu and now after starting up, and loading ubuntu, it gets stuck at a blank screen showing beige colour. What happened??

---

### Post by grundygreen on 2009-09-19
> **talkingtree said:**
> hi,

I have installed ubuntu and now after starting up, and loading ubuntu, it gets stuck at a blank screen showing beige colour. What happened??

Which version of ubuntu?
Server or desktop? 
Which platform/chip?(X86< PPC, ARM, Sparc)
Which DE/GUI?

---

### Post by talkingtree on 2009-09-30
hi, thanks for the reply

version 8.1 (but it works for another computer)
desktop
(what is platform and chips?, intel pentium 4?)
GUI

oh yea, I've also tried installing between *automatically log in, and not automatically log in*, the screen only get stuck after the log in phase

---

### Post by rreese6 on 2009-09-30
When you installed Ubuntu, did you make sure you had enough space in the partition. the default partition is too small once you upgrade.
for grins, run the boot-info-script:

To help you with your problem, more information is needed.

1. Boot up with LiveCD. Once you are on the Desktop, got to this link and download:
```
[Download Boot Information Script]("http://sourceforge.net/projects/bootinfoscript/")
```
This Script will gather your current configuration and make a report.
This gives us a better idea of what your problem is and how to fix it.

2. Open up terminal and type:

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will make a file called "Readme.txt" on your desktop.

3. Post the contents of that file here.

---

### Post by talkingtree on 2009-10-31
> **rreese6 said:**
> When you installed Ubuntu, did you make sure you had enough space in the partition. the default partition is too small once you upgrade.
for grins, run the boot-info-script:

To help you with your problem, more information is needed.

1. Boot up with LiveCD. Once you are on the Desktop, got to this link and download:
```
[Download Boot Information Script]("http://sourceforge.net/projects/bootinfoscript/")
```
This Script will gather your current configuration and make a report.
This gives us a better idea of what your problem is and how to fix it.

2. Open up terminal and type:

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will make a file called "Readme.txt" on your desktop.

3. Post the contents of that file here.

I've tried rebooting using liveCD as you said, but it gave me this

stdin:error0 (repeated like ~50 times or so)
BusyBox v1.13.3(Ubuntu 1:1.13.3-1Ubuntu7)built-in shell (ash)
Enter help for a list of commands
(initramfs)Unable to find medium contain live file system

edit: this is using Ubuntu9.10 liveCd

---

