---
title: "I upgraded and have a few questions"
date: 2009-04-20
forum: Installation &amp; Upgrades
---

### Post by jobo1313 on 2009-04-20
I just upgrade to 8.10 and I got some questions. Why can i never find un-installed packages in the package manager. Like i wanted to get vlc and wine but when ever i search they never show up. ANother question is, why when i try to install americas army does the whole system crash. 

Thank you to all who can help.

---

### Post by Partyboi2 on 2009-04-20
Hi, for vlc and wine check in Software Sources (System>Admin>Software Sources) under the first tab that you have multiverse and universe repostories enabled. If not enable them and reload the package list then try searching for them in Synaptic.

---

### Post by jobo1313 on 2009-04-21
I got vlc from a webpage link but i still cant find wine. Also any insight into why i cant install AA would be great :popcorn:

---

### Post by Partyboi2 on 2009-04-21
> **jobo1313 said:**
> I got vlc from a webpage link but i still cant find wine. Also any insight into why i cant install AA would be great :popcorn:
I take it you have the repos enabled then?

---

### Post by jobo1313 on 2009-04-22
Yes i do, but it never shows up when i search.

---

### Post by Partyboi2 on 2009-04-22
Make sure you have reloaded the package list before searching for the packages. If that does not work then open a terminal and try
```
sudo update-apt-xapian-index
``` then restart synaptic and search for the packages.

---

### Post by jobo1313 on 2009-04-23
Thanks for the help but  a hilarious but sad thing happened :lolflag:
"Imminent Hard Drive Failure" So I'm boned and thats the reason nothing was working.:-({|=:cry: a little tip never buy sony vaio's they suck. Hard drive died in only 11 months of use. I'm on a live dvd-wr,thank goodness for linux, this pc would be totally useless otherwise. 

Thanks again for services rendered.

:cry:I want to cry ](*,)

---

