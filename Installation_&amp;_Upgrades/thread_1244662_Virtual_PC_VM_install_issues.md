---
title: "Virtual PC VM install issues"
date: 2009-08-19
forum: Installation &amp; Upgrades
---

### Post by terence_b on 2009-08-19
Hi, I'm new to Linux and wanted to setup an env using Virtual PC. I managed (in the end) to get Ubuntu installed, but when I try to boot for the first time, the OS lists a load of bumf, then the last line states:
 
1.416003] ---[ end trace 4eaa2a86a8e2da22 ]---
 
I did have this same message at first when trying to setup, but 
[COLOR=black][FONT=Verdana][SIZE=2]Removed the option "quiet splash --" and replace it with "vga=791 noreplace-paravirt" instead. This hasn't worked since.[/SIZE][/FONT][/COLOR]

[COLOR=black][FONT=Verdana][SIZE=2]Has anyone had the same issue? Any advise, would be most welcome.[/SIZE][/FONT][/COLOR]

---

### Post by aesis05401 on 2009-08-19
I'm afraid you will not be finding good news at the end of this tunnel... 

Virtual PC is moving toward lightweight, Windows only guests for compatibility within Windows host environment.  This is probably a blessing, as the old Virtual PC products never really achieved credibility even with the .NET development houses I worked with.

Anyhow, the MS virtch solutions that wil be handling Linux should be from Viridian line.  Hyper-V is the brand name I think.  You will find better forums for answers related to those products on Microsoft oriented help forums... 

Finally, MS is pushing for Linux distros that want to run in the Hyper-V branded line VMs to build in support for running in 'paravirtualization' mode...  I'm sure we will be hearing more about this in the near future, but for the time being you should just know that linux support in MS hypervisor is sketchy by design.  

Hope this helps.  Good luck.

---

### Post by running_rabbit07 on 2009-08-19
Try [Sun Virtual Box 3.0]("http://www.virtualbox.org/wiki/Downloads"). Works great with loading Ubuntu. I don't know how well it works on MS for loading Ubuntu but I am sure that it will do fine.

---

