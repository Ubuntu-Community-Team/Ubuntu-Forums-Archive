---
title: "Hard drive or Ubuntu problem?"
date: 2009-12-09
forum: Hardware
---

### Post by novice1969 on 2009-12-09
My machine shut down and when I rebooted I got the following:

[B]Screen init failed

Gave up waiting for root device. common problems:
   -Boot args (cat/proc/cmdline)
     -check rootdelays = (did the system wait long enough?)
     -check root (did the system wait for the right device?)
 
missing modules (cat/proc/modules)  ls/dev


ALERT! /dev/disk/by-uuid/ade5eaa2-2aba-4d7a does not exist
Dropping to a shell!

BusyBox v1.13.3 (ubuntu 1:1.13.3-1 ubuntu7) built in shell

Extra 'help' for a list of built in commands.[/B]


I did a self check on the hard drive and it came back as fine.  What else could I do to get this machine to boot up?

---

### Post by Dave67 on 2009-12-09
I am not by any means an expert what if any does this command post back

ls -l /dev/disk/by-uuid

looks like for some reason your HD drive ID has changed names for some reason ( I google it )  :)

the above command will show us what the links that point to your /dev/hd?x or /dev/sd?x than a member who knows more can help with this.

dave

---

### Post by novice1969 on 2009-12-09
Okay,

Here's what I get back when I use that command.  


**1 0   0 10  9c33cb6-526e-4038-869f-ce53d8077ee  -> ./../sda5**


What does that mean?

Thanks

---

### Post by novice1969 on 2009-12-09
h

---

