---
title: "Server installation - ext3 or ext4?"
date: 2009-06-17
forum: Installation &amp; Upgrades
---

### Post by mocka on 2009-06-17
Hi, I'm about to do a fresh install of Ubuntu Server on my server. After having read both good and bad reviews (most of them fairly old, therefore recent updates may have fixed the problems presented) I decided to ask here: should I install ext3 or ext4? As it is a server, stability comes over performance.

---

### Post by lemming465 on 2009-06-18
A lot depends on the performance profile of the server load, how hard access to the server is for recovery purposes, and how much you value stability.  Phone companies, who really value stability, often have a policy of running release N-2 when a vendor puts release N out.  They would use ext3, deeming ext4 too new to trust.  If the server is in some far away colo, you might feel the same.  I've been running some desktop workloads on ext4 for several months with complete satisfaction; if you are feeling more adventurous or have a work load involving creating lots of small files or deleting large ones ext4 might perform a lot better for you.

---

