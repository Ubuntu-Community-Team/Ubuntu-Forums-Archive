---
title: "Ubuntu node cluster"
date: 2009-06-20
forum: Installation &amp; Upgrades
---

### Post by b89.smith on 2009-06-20
I am thinking about building a cluster out of some old computers. I am do not know much about clusters and how to run applications so they take advantage of the computing power available in the cluster.

I was wondering if any of you know of a way to install ubuntu server onto all the nodes in my cluster and then install a vm onto the entire cluster. So that I can run ubuntu desktop in the vm and take advantage of the entire cluster while running programs designed for a single machine.

Any help would be greatly appreciated.

---

### Post by PilotJLR on 2009-06-20
That's not how virtual machines work... regardless of the platform, virtual machines are run on only one host at a time. They can migrate between physical hosts, but one VM won't be using resources on all hosts at once.

One example of high performance computing would be Beowulf:
[http://www.beowulf.org/](http://www.beowulf.org/)

Applications on HPC need to be designed for it... so this is not a trivial setup.

---

