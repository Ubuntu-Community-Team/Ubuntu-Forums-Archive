---
title: "Console locks up when SSH"
date: 2008-08-07
forum: General Help
---

### Post by matmcnic on 2008-08-07
Odd thing...

From the console of a remote machine I do:
ssh username@ubuntuserver

I can then work normally... except if I do anything that has a lot of lines -- then the console locks up and I have to exit the cosole (even ctrl-C does not work).

So for example if I do any of the below it causes a lockup since these generate a lot of terminal lines:
ls /dev
vi

Any ideas appretiated!

---

### Post by finer recliner on 2008-08-07
maybe your 'ubuntuserver' is low on memory, or a local process is hogging the CPU. this may make it unresponsive to commands that take longer than 1/4 of a second to run.

log on to 'ubuntuserver' locally (not via ssh), and run 
```
top
```
and see if something else is hogging resources

---

### Post by matmcnic on 2008-08-07
Thanks for your reply. 
The server is using very low resources so no problem there.
It's odd.. if I do ping someserver then that can run for 100's of lines no problem -- but if I do something like *ls /dev* then it locks. It's something that happens only when a lot of lines are fed at once to the console. This happens for SSH and RSH consoles.

More info...
-This is Ubuntu 8.0.4 server running inside of a VMWare Server

Thank you for any ideas!

---

