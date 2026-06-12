---
title: "Pidgin crashing on logon [SOLVED]"
date: 2008-10-02
forum: General Help
---

### Post by SnappyU on 2008-10-02
Hi all,

I've been having repeated crashes with pidgin on logon to msn today.  Found a fix [https://answers.launchpad.net/ubuntu/+source/pidgin/+question/42608](https://answers.launchpad.net/ubuntu/+source/pidgin/+question/42608)

> 
I have same problem: pidgin not start, with same gtk error.
(it work fine many months before...).
'sudo mv .purple purple-old' is fixes problem, but deletes my settings.
I find more useful solution, (re)move the 'icons' subfolder. Pidgin now functional, without settings loss.


The icons subfolder is generated on the fly when you login again, so don't worry about it.  it contains the user picture displayed in profile.

Pidgin version: 2.4.1
Ubuntu: 8.0.4

---

