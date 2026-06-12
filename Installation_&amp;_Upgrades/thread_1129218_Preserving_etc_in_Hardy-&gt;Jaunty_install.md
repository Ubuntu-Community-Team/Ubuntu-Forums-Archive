---
title: "Preserving /etc in Hardy-&gt;Jaunty install"
date: 2009-04-18
forum: Installation &amp; Upgrades
---

### Post by lenticular on 2009-04-18
I'm looking at doing a clean install on my 4 PCs that currently run Hardy.  I can migrate user data with no problems, and have a handy lists of packages that need to be reinstalled, but I am wondering about some of the config files in /etc.

Can I safely overwrite Jaunty /etc files and subdirectories with the ones from Hardy?  If not, how do I identify and copy only the ones that I need?

For instance, it seems like my /etc/samba config stuff should be the same between versions, but I wonder if other config files in /etc are jaunty-specific and should not be overwritten.

Thanks,
 John

---

### Post by lemming465 on 2009-04-19
If you want automatic updates to your /etc files, you need to follow the hardy -> intrepid -> jaunty upgrade path.  Otherwise the safest thing to do is make backup copies of the hardy files (e.g. mv  etc etc.hardy, from a live CD; or cp -a etc etc.hardy) and install clean copies of the jaunty ones.  Overwriting jaunty files on top of existing hardy files will mostly work, yes.  However, there are bound to be a few glitches if you do it that way.  You can do that if you have strong confidence in your troubleshooting skills.

---

