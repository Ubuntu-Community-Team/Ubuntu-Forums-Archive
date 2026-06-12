---
title: "A new utility for MBR backup and restore"
date: 2009-11-11
forum: Installation &amp; Upgrades
---

### Post by IgnorantGuru on 2009-11-11
I have added a new 'mbrback' script for download from
[http://igurublog.wordpress.com/downloads/script-mbrback/](http://igurublog.wordpress.com/downloads/script-mbrback/)

This is a script I've been using for some time to maintain my systems, so I polished it up a bit.  It lets you create MBR and partition table backups, and also restore from them.  It is particularly useful when something overwrites the MBR boot code (ie grub) and you want to quickly restore it.

The commands in the script are actually simple - most of the script consists of safety checks and warnings.  So it's mostly just a convenience so you don't have to type complex commands to do these things.

Please use this script with caution.  This is an advanced topic and improper use can render your computer unbootable or render the data on your drive unreadable.  The script will give you applicable warnings before it writes anything to disk.  Please read the instructions carefully.

---

