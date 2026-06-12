---
title: "Acer recovery cd (XP) - doesn't  rewrite the MBR"
date: 2005-11-09
forum: General Help
---

### Post by daller on 2005-11-09
Hi there,

I've installed Kubuntu on a friends laptop, but in case she want XP back, I would like to know how I get XP installed again.

After using the recovery-cd, grub is still there, and gives an error.

Any idea on how to fix this?

---

### Post by Kyral on 2005-11-09
Load into XP Recovery Mode (the command prompt one) and execute "fixmbr"

---

### Post by daller on 2005-11-09
[QUOTE=Kyral]Load into XP Recovery Mode (the command prompt one) and execute "fixmbr"[/QUOTE]

How do I do that?

---

### Post by GoldenH on 2007-11-29
fixmbr won't rewrite it to the acer mbr unfortunately (its not the normal windows one, so all the guides about how to get your windows MBR back won't work).

i haven't found a way to recover the acer mbr yet, i did find a thread  on another forum that suggested you could run "mbrwrwin install rtmbr.bin" from the C:\ drive in windows, after copying mbrwrwin.exe and rtmbr.bin to the C: drive from the recovery partitions. however not all acer recovery partitions have those programs.

---

### Post by koshari on 2008-06-16
recovering the acer mbp is a bit of a pain but can be done , 
see this guide, 

[http://forum.notebookreview.com/showthread.php?t=11476&page=23](http://forum.notebookreview.com/showthread.php?t=11476&page=23)

i would imagine making a bartsPE disc with the 2 acer mbr tools on it would be a lot easier.

---

### Post by Arthur Archnix on 2008-06-16
There's an answer on this thread. [http://ubuntuforums.org/showthread.php?t=463534&highlight=Ted+Nancy](http://ubuntuforums.org/showthread.php?t=463534&highlight=Ted+Nancy)

Essentially, you're gonna need a live grub cd to boot windows if it's already installed. Then you gotta download the app listed on that page. And run it but for Xp.

---

### Post by koshari on 2008-06-18
unfortinately though arthor the acer notebooks with eRecovery DONT have a standard MBR, its a modified one and cam only be restored with the acer fixmbr tool.

and the above linked thread shows no instruction at all on how to do such a thing.

---

