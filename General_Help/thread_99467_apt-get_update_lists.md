---
title: "apt-get update lists"
date: 2005-12-05
forum: General Help
---

### Post by Chris Tucker on 2005-12-05
I run on that old pitiful dialup, and have 3 computers running ubuntu.
(my ISP is supposed to be putting in the ADSL/DSL hardware in this area soon so this is temporary)
My apt-get update runs me just under 5 megabytes.. on this amazingly fast connection, that means just under a half hour to apt-get update, per computer! thats an hour and a half! 
i am wondering if there is a way to copy the sources lists that apt-get update stores, and copy them (scp or rsync, or the like) from computer to computer? All the computers have the same dist, and same sources.list. I am completely able to get the files moved, if i know where they are, and if doing this works.

---

### Post by Bandit on 2005-12-05
Synaptic does have a option to download the updates and dave them to the hard drive for you. That way you can place them on a CD and quickly update the other PCs.

---

### Post by Chris Tucker on 2005-12-05
no no, i do that stuff manually all the time, by simply copying all debs in /etc/cache/apt/archives  from computer to computer. but i am talking about just the apt-get update function data... not apt-get upgrade

---

