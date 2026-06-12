---
title: "tool to check for bad sectors on hard drive"
date: 2005-05-07
forum: Hardware &amp; Laptops
---

### Post by lorap on 2005-05-07
does anybody know any tool like scandisk in microsoft?
thanks

---

### Post by kvidell on 2005-05-07
[QUOTE=lorap]does anybody know any tool like scandisk in microsoft?
thanks[/QUOTE]
 man fsck

> NAME
       fsck - check and repair a Linux file system

SYNOPSIS
       fsck [ -sAVRTNP ] [ -C [ fd ] ] [ -t fstype ] [filesys ... ] [--] [ fs-specific-options ]
Hope that helps,
- Kev

---

### Post by lorap on 2005-05-07
thanks buddy,i'll check right now.

---

### Post by lorap on 2005-05-07
nope it can't make the scan for bad sectors,
i'm looking for such tool.
thanx anyway.

---

### Post by Gandalf on 2005-05-07
[QUOTE=lorap]nope it can't make the scan for bad sectors,
i'm looking for such tool.
thanx anyway.[/QUOTE]
 man badblocks

---

### Post by lorap on 2005-05-07
thanks friend i'll check it right now.

---

### Post by Gandalf on 2005-05-07
[QUOTE=lorap]thanks friend i'll check it right now.[/QUOTE]
 no problem

---

### Post by lorap on 2005-05-07
it worked!
thanks.

---

### Post by Gandalf on 2005-05-07
[QUOTE=lorap]it worked!
thanks.[/QUOTE]
 no problem buddy

---

### Post by kvidell on 2005-05-07
[QUOTE=Gandalf]no problem buddy[/QUOTE]
 fsck == software/data corruption. badblocks == physical damage inspection (?)

---

### Post by Gandalf on 2005-05-07
[QUOTE=kvidell]fsck == software/data corruption. badblocks == physical damage inspection (?)[/QUOTE]
 exactly!

---

### Post by kvidell on 2005-05-07
Awesome! I actually need to do something like that on my Fedora box. Thank you much!
- Kev

---

