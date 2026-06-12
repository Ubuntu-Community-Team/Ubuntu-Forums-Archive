---
title: "OpenOffice Loading Time"
date: 2008-10-15
forum: General Help
---

### Post by sondosia on 2008-10-15
I have Ubuntu 8.04 running on a laptop with a 1.1 gH processor, and yet any openoffice app (I've tried word processor, presentation, and spreadsheet) takes a REALLY long time to open, sometimes as much as five minutes. 

I thought it might be because I often have Firefox running and it's a memory hog, so I closed it, but it still took a really long time. Any ideas?

---

### Post by hyper_ch on 2008-10-15
[http://lifehacker.com/software/optimization/speed-up-openoffice-270775.php](http://lifehacker.com/software/optimization/speed-up-openoffice-270775.php)

Then also go to the Java section and disable Java environment completely.

---

### Post by _sAm_ on 2008-10-15
"five minutes.", that's insane! 

There are some settings you can try, go to Tools>Options
1. Under "Java" uncheck "Use a Java runtime enviroment".
2. Under "Memory" insert:
    Number of steps: 100
    Use for OpenOffice.org: 128
    Memory per object: 20
    Number of objects: 20 

If it still sucks try the programs Abiword and Gnumeric witch can replace OOo Writer and OOo Spreadcheet. You can find both in Synaptic packagemanager.

---

### Post by Sycron on 2008-10-15
It can be because of low ram memory sistem. I have 630Mhz and openoffice loads in 15secs.

---

