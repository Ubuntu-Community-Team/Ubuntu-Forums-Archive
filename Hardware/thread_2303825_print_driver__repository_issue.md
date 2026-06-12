---
title: "print driver / repository issue?"
date: 2015-11-21
forum: Hardware
---

### Post by frogeyedan on 2015-11-21
hi
fighting to get a print driver to work i installed drivers from out of the repository. tey didnt work but now the synaptic program wont run. 
i get:  E: The package hl2230lpr:i386 needs to be reinstalled, but I can't find an archive for it.E: Internal error opening cache (1). Please report.

at the command line i get: 
 sudo apt-get install hl2230lpr:i386
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package hl2230lpr:i386 needs to be reinstalled, but I can't find an archive for it.
[[[[]]]]]] ~/Downloads $ sudo apt-get remove hl2230lpr:i386
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package hl2230lpr:i386 needs to be reinstalled, but I can't find an archive for it.
[this is a 64bit - the drivers were i386]
i deleted the installation file, thinking it didnt work and wasnt needed, but it was never from the repository anyway.  
is there a way to tell synaptic to ignore that?
thanks 
dan

---

### Post by T.J. on 2015-11-23
Did you "Apt-get update" your cache to reflect that current state of the repository?  Setting that aside, have you tried installing it manually?  

If yes to both, please let me know.

---

### Post by frogeyedan on 2015-11-25
At this point the printer is working, the problem is that synaptic isnt.  i did just retry the apt-get update at the command line and got the same result.
tried:  sudo apt-get upgradeReading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package hl2230lpr:i386 needs to be reinstalled, but I can't find an archive for it.

so i had installed it from outside the repository but now it is screwing up the apt system and the question is how to fix apt/dkpg

basically it is trying to find in the repostory, something that didnt come from there. is there a way to add a brother source to the /source.list so that it can install it and get rid of the objection?

[This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.]

---

### Post by T.J. on 2015-11-26
If you installed from an outside repository, it is possible that the scripts embedded in the package are not working properly.  This is not necessarily malicious, just sloppy programming. 

If you are using synaptic, remove the package repository, and try to update.  If that succeeds, remove them using the local tab under origin or broken tab under the status tab in synaptic.  Set them for a complete removal. If that does not work, try an "sudo apt-get purge <name>" in the terminal on the package and see if that forces a clean removal. If it does not, the next step would be to remove the package manually. It can be a bit tricky, but it can be done.

---

