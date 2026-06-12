---
title: "powernow-k8: failing targ, change pending bit set"
date: 2010-07-19
forum: Hardware
---

### Post by jschmeau on 2010-07-19
I'm posting this as a question and solution because I have spent much time searching the forums and web for a solution and wish to help anyone who may be having the same problem. 

Ubuntu 10.04 
Motherboard: K8M-800M
CPU: AMD Sempron(tm) Processor 3100+
     Socket 940
     1800MHz
     64 bits

PROBLEM:
A few seconds after login, the first console repeatedly displays "powernow-k8: failing targ, change pending bit set" nearly 5 times a second thus making it extremely difficult to run any linux commands.  (I can type commands and run them, but each letter I type is separated by several instances of the error above)

SOLUTION:  
sudo apt-get install rcconf
run rcconf and de-select "OnDemand"
save and reboot

rcconf is a Debian utility for configuring which services get started up at boot-time. It's really a front-end for the update-rc.d command.


It appears that the OnDemand service is the one that is having a problem with my mobo/cpu even though it is reported as a powernow failure.

---

