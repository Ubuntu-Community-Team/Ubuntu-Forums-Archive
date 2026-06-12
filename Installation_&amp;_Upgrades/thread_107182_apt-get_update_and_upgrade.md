---
title: "apt-get update and upgrade"
date: 2005-12-22
forum: Installation &amp; Upgrades
---

### Post by hardbop200 on 2005-12-22
Hello,

I am curious about using apt-get upgrade on my default install of Breezy.  I have not added any sources to my list *with the exception of* the universe and restricted repositories.

I do install the security updates, so what will apt-get upgrade do for me?  Will it bring me up to the most recent devel version of Ubuntu?

Thanks for any advice you may have,

Josh

---

### Post by towsonu2003 on 2005-12-22
apt-get update will update the list of programs that your computer knows are available... apt-get upgrade will actually download and install those updates (includes security updates) for your current version of ubuntu.

---

### Post by hardbop200 on 2005-12-22
Has anyone actually tried this?  Or is this basically what the update manager does?

---

### Post by towsonu2003 on 2005-12-22
[QUOTE=hardbop200]Has anyone actually tried this?  Or is this basically what the update manager does?[/QUOTE]
I am assuming you know how to use synaptic (package manager in System > Administration > Synaptic), so:

sudo apt-get update is the same thing as hitting the reload button in synaptic. 

sudo apt-get upgrade is the same thing as selecting all items with available update in synaptic and hitting apply to download and install them. 

some people like and use synaptic (easy to use), some like and use command line apt-get (faster - do not wait for GUI to open) and some like both equally (like me).

The update manager (the round red thingy with white arrows which appears out of no where at the upper right side of desktop when there are updates available), in my system, does the following: it updates its list of known software from repos (apt-get update), compares and downloads all updates without my consent (see man apt), and waits for my consent to install those updates.

---

### Post by az on 2005-12-22
[QUOTE=hardbop200]Has anyone actually tried this?  Or is this basically what the update manager does?[/QUOTE]
Yes.  A lot of people, all the time.

Security updates are packages with fixes from that release.  To get any developmental release packages, you need to have developmental release entries in your sources.list.  This is not your case.

Currently, Dapper is developmental.  You do not have any Dapper entries.  When Dapper is released as stable, you can change your entries to point to it to upgrade to it.

---

