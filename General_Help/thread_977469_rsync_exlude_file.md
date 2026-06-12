---
title: "rsync exlude file"
date: 2008-11-10
forum: General Help
---

### Post by desmane on 2008-11-10
Hello people, 

I'd like to backup my computer using rsync and Kcron. 

Linux andibuntu 2.6.24-21-generic #1 SMP Tue Oct 21 23:43:45 UTC 2008 i686 GNU/Linux
Kubuntu 8.04, KDE Version 3.5.10

I created a partition that has the same size my kubuntu partition has. I first thought, I would just rsync the root folder "/" over to my backup partition, but came across the "man rsync" and INCLUDE/EXCLUDE PATTERN RULES. But how does that work??

So I thought creating the PERFECT rsync exlude file for ubuntu would help others too! 

I think, includes should be 
#############################
/home
/etc
/usr/local
/var

and excludes: 
#################

/proc
/sys
/tmp
/var/cache
/dev
/var/tmp
/dev
/media

(exclude regex )
.thumbnails
.Trash
.Cache
.cache

probably a max-size?

---

