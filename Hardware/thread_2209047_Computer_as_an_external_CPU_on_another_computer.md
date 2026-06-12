---
title: "Computer as an external CPU on another computer?"
date: 2014-03-03
forum: Hardware
---

### Post by Chris_Katko on 2014-03-03
Let's throw out the "let's check if he's an idiot" tests and get to the beans:

One computer. Another computer, possibly over ethernet, showing up as a "CPU" for all OS/program purposes on the first.

Is this possible in Linux? Where should I start looking? Are their projects dealing with this? I vaguely remember someone writing an ARM core emulator that utilized a rarely used feature in linux called an "external processor" which let his little microcontroller run threads.

---

### Post by tgalati4 on 2014-03-03
What I think you are describing is a cluster--combining CPU's from different machines to perform a single workload.  Yes, it can be done, but not in the way that you described.

You can always ssh into the remote computer with X-forwarding and run that computer's desktop on your desktop.  So now you have two computers--one in each workspace.  You can share data between them, but that requires setting up some dedicated file shares.

Some reading:

[https://help.ubuntu.com/community/SSH/OpenSSH/PortForwarding](https://help.ubuntu.com/community/SSH/OpenSSH/PortForwarding)

[https://help.ubuntu.com/community/Clustering](https://help.ubuntu.com/community/Clustering)  (old data, but gives some background)

[http://askubuntu.com/questions/57526/how-can-i-cluster-two-machines-to-double-the-processing-power](http://askubuntu.com/questions/57526/how-can-i-cluster-two-machines-to-double-the-processing-power)

[https://help.ubuntu.com/community/MpichCluster](https://help.ubuntu.com/community/MpichCluster)

---

