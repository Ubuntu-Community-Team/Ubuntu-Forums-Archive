---
title: "Evolution-Exchange broken since Jaunty upgrade"
date: 2009-04-28
forum: Installation &amp; Upgrades
---

### Post by belim on 2009-04-28
Ok so I upgraded to Jaunty by means of a fresh install. Everything so far is great. Only issue is the evolution-exchange plugin is broken again!... 

I have found a bug which was opened for 7.04 back in June 07. See here: [https://bugs.launchpad.net/ubuntu/+source/evolution-exchange/+bug/119886](https://bugs.launchpad.net/ubuntu/+source/evolution-exchange/+bug/119886). This is my exact problem, except it seemed to be resolved while I was running 8.10 (I cant say before that as I only switched to Ubuntu recently). 

It is massively annoying and I am actually considering moving back to 8.10 as I need exchange support and it is irritating to say the least having to run a VM for outlook! :lolflag: 

I dont understand why it has gone from being fixed to being broken in a newer version?! I have done all proposed updates and still no fix and apparently I shouldn't downgrade evolution, is that right? 

Other than that though, Jaunty is great! :) :lolflag: Thats why I am so annoyed about the fact that I might need to downgrade... Any suggestions? :)

---

### Post by Morm on 2009-04-29
Have you tried using the evolution-mapi extension? It worked for me after renaming /etc/samba/smb.conf (as mentioned in another post)

---

### Post by garymansell on 2009-05-01
Hi,

I can confirm that Evolution Exchange Connector has regressed from working fine in 8.10 to very unstable in 9.04.

This is a real nuisance as in an office environment, Exchange Connector is critical.

Any ideas? I presume it would be too much of an effort to try and shoehorn the 8.10 version of Exchange into 9.04?

Rgds

---

### Post by djcrash1981 on 2009-05-15
Hey there, I'm having the same issue here.

Anyone knows how to solve it??

---

