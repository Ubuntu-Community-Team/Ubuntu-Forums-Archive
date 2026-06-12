---
title: "bash: gcc: command not found"
date: 2005-12-03
forum: General Help
---

### Post by WebDrake on 2005-12-03
When I try to gcc some code, I get the error message:

bash: gcc: command not found

... which is bizarre, since according to the Synaptic Package Manager, gcc-4.0, gcc-4.0-base, and gcc-4.0-doc are all installed.

Any ideas what the problem is ... ? :confused: 

Many thanks,

         -- Joe

---

### Post by taurus on 2005-12-03
How did you install GCC 4.0 on your system?  Maybe you need to run these

sudo apt-get update
sudo apt-get install build-essential

---

### Post by WebDrake on 2005-12-03
Many thanks! :-)

---

