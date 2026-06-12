---
title: "problem with remastersys and ubuntu live cd"
date: 2009-06-23
forum: Installation &amp; Upgrades
---

### Post by pythonscript on 2009-06-23
I'm trying to make a custom live CD using remastersys, but I get boot errors whenever I try to boot from the live CD I made. I'm running Ubuntu 9.04 in a virtual machine, fresh install, and I've created both a live cd using isolinux and one using grub, but when I go to boot the CD on another computer, it doesn't work. I get a disk error when I boot the isolinux, and a simple grub error when I try to boot the grub version. I can post the specific errors later when I'm back in front of my main computer. Any ideas? The CD burner in my computer works fine (I've used it to burn 7 ISO images of different things since these two failed, and those have all worked perfectly), so does anyone have any ideas? I installed the virtual ubuntu on an ext4 file system; would this have something to do with it? I know remastersys has a forum, and I'm posting this here too to try to take advantage of a wider user base. Thanks in advance!

---

### Post by ajgreeny on 2009-06-23
I would suspect the fact that your installed ubuntu is a virtual machine may be making the problem for you.  I have never used remastersys, so have no experience to really go on, but that would seem to be a possible reason.  have you managed to do this with any other OSs in a VM environment?

---

### Post by pythonscript on 2009-06-23
I haven't tried this with any other system in a virtual machine, but I don't see why that would make a difference.

---

### Post by pythonscript on 2009-09-06
The problem corrected itself after I ran remastersys again. I think it might have gotten interrupted during the creation process. Thanks for the help!

---

