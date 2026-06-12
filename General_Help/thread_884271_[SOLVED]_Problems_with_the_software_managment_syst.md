---
title: "[SOLVED] Problems with the software managment system"
date: 2008-08-08
forum: General Help
---

### Post by camujica on 2008-08-08
I followed some web instruction and that cause the following problem when I try to add/remove programs:

[COLOR="Blue"]Failed to check for installed and available applications

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.
[/COLOR]

and when I try to open synaptic package manager the following error appear:
[COLOR="Blue"]E: Type '--15:29:02--' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.[/COLOR]

can anybody help me?????

thanks in advance!!!

---

### Post by drs305 on 2008-08-08
Let's start by trying to fix the Medibuntu repository:
The way to include the Medibuntu repository changed with the introduction of Hardy and you may have  used old commands to add it the medibuntu.list.

The following will install  the Medibuntu Repository following the guidance from [https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu"). [I]These instructions are for Hardy.
[/I]
```

sudo mv /etc/apt/sources.list.d/medibuntu.list /etc/apt/sources.list.d/medibuntu.list-old 
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
sudo apt-get install medibuntu-keyring && sudo apt-get update 

```

Then try running things again and we'll move on to the next error. I've left off "&& sudo apt-get upgrade" from the last command, waiting to see if the "apt-get update" produces errors. If it doesn't, you can run "sudo apt-get upgrade" if you wish.

---

### Post by camujica on 2008-08-09
> **drs305 said:**
> Let's start by trying to fix the Medibuntu repository:
The way to include the Medibuntu repository changed with the introduction of Hardy and you may have  used old commands to add it the medibuntu.list.

The following will install  the Medibuntu Repository following the guidance from [https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu"). [I]These instructions are for Hardy.
[/I]
```

sudo mv /etc/apt/sources.list.d/medibuntu.list /etc/apt/sources.list.d/medibuntu.list-old 
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
sudo apt-get install medibuntu-keyring && sudo apt-get update 

```

Then try running things again and we'll move on to the next error. I've left off "&& sudo apt-get upgrade" from the last command, waiting to see if the "apt-get update" produces errors. If it doesn't, you can run "sudo apt-get upgrade" if you wish.
Thanks a lot for your help!!!
everything is working propertly now, thanks again!

---

