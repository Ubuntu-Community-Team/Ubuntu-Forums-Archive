---
title: "Boot Failure"
date: 2021-04-02
forum: Hardware
---

### Post by CowDoctor on 2021-04-02
Dear Friends,
   My main computer failed to reboot after it displayed some weirdness opening Libre Office, and has continues to fail.  Here is the error message:

/dev/sda2 contains a file system with errors, check forced.

/dev/sda2: UNEXPECTED INCONSISTENCY: run fsck manually.
         (i.e without -a or -p options)
fsck exited with status code 4
The foot filesystem on /dev/sda2 requires a manual fsck

BusyBox v1.30.1 (Ubuntu 1:1.30.1-4ubuntu6.3) built in shell (ash)
Enter 'help' for a list of built-in commands.

(initremfs)

This is above my pay grade.  Any help or advice welcome.  Please be careful and explicit with you replies.  I am not very skilled with the terminal and need details that me be obvious to most of you.
Yours hopefully,
Joe

---

### Post by yancek on 2021-04-02
What happened when you ran fsck manually as recommended?  Many sites online explaining how to do that.

---

### Post by ajgreeny on 2021-04-02
Simply boot to a live Ubuntu system; it doesn't matter which DE version, Ubuntu, Kubuntu, Xubuntu etc etc, and from that run terminal command ```
sudo e2fsck /dev/sda2
``` and see what it reports back.

---

### Post by CowDoctor on 2021-04-02
Thank you.  All fixed.  Sorry to waste your time with such a simple question, but am most grateful.

---

### Post by CowDoctor on 2021-04-02
Thank you.  I figured out how to runs fsck and all is now well.  Much appreciated.

---

