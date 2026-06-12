---
title: "Partition recommendation"
date: 2006-01-20
forum: Installation &amp; Upgrades
---

### Post by dannyl on 2006-01-20
Here is my situatiuon, I've been running Slackware for quite a while now and decided to try Ubuntu on an old computer I had sitting around gathering dust. It is an old PII Gateway with two 4.3 gig hard drives. I installed Ubuntu using hda as / and partitioned hdb as /home. The problem I am having is I ran out of room on hda for additional programs. Hdb is still practically empty. Since it is a new install, there is nothing that I am worried about losing so I want to re-install using a better partion setup. What would be a reasonable partition scheme for this setup.

Thanks in advance.

edit

PS. I of course also have /swap on hda

---

### Post by Sef on 2006-01-20
>  What would be a reasonable partition scheme for this setup.

I would do a server install on hda and use a lightweight widowmanager: XFCE, fluxbox, icewm.

Your swap shouldn't take up too much space unless you have upped the memory.  If you have 128 mb ram then your swap will only be 256 mb.   That will leave 4 gb for the Ubuntu and should be more than enough.

---

### Post by morphodone on 2006-01-20
The other option is to use LVM to use both hard drives as one
and then partition as you see fit...

Setting up LVM during installation isn't the easiest task but can be done.

---

### Post by dannyl on 2006-01-20
Perhaps I asked the question incorrectly. What I want to do is divide hdb into two 2gig partitons to make room for additional program installs. Whic directory(s) should I move to the additional partition?

---

