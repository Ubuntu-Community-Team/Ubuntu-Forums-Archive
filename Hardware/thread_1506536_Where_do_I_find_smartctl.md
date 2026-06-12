---
title: "Where do I find smartctl?"
date: 2010-06-10
forum: Hardware
---

### Post by lwalper on 2010-06-10
I'm working on a Toshiba Satellite laptop that appeared to have a failed 250Gb WD HDD. I ran the WD HDD utilities to check drive function and they said there were so many sectors out of maximum fault tolerance that the testing utility would not even run.

I have now replaced the WD drive with a new Seagate 250Gb drive. The customer wants me to install WinXP, but for some reason it won't partition and format the drive.

I have installed Ubuntu 10.04 on the system - I'm using it now to write this - and wanted to run smartctl to check the drive, but for some reason can't find it. Where is smartctl? I've looked in the repositories and in the manual and don't seem to be able to locate the file/command.

---

### Post by gordintoronto on 2010-06-10
Run Accessories/Terminal, and enter the command:
smartctl

Then follow the instructions.

Smartctl is part of the smartmontools, installed by default in the version I am using. If it's not in 10.04, use Synaptic to install it.

---

