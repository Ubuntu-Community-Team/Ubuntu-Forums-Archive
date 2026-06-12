---
title: "VMware-server install"
date: 2009-06-03
forum: Installation &amp; Upgrades
---

### Post by jodrre on 2009-06-03
Okay, I feel like an idiot...

I downloaded VMware Server 2.0 from vmware.com, and I downloaded the rpm, thinking I could use alien and make it a deb. 

```
sudo alien -d -c ./vm.rpm
```that made the deb package I needed, and I installed it with GDebi (the default)

However, I went to try and find it, and it wasn't working. Couldn't even get to the main installer. So I open GDebi again to reinstall. Froze my system. I pull up Synaptic to manually remove it to download the tarball and do it that way, and synaptic (even apt) gives me the following error:

> me@mycomp:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: The package vmware-server needs to be reinstalled, but I can't find an archive for it.I can't pull up synaptic because it gives me that error and then kills itself, and that's a quote from apt (obviously)...

Any suggestions? I don't know how to manually get rid of this package without a manager and a reformat is out of the question. It takes me forever to download updates for this thing.

---

### Post by zvacet on 2009-06-05
```
sudo apt-get --purge remove vmware-server
```

When you remove it read [this]("http://ubuntuforums.org/showthread.php?t=973756") to install VMware server.

---

### Post by jodrre on 2009-06-07
darn, i was hoping that would work

it still gives me the same error. i've also tried a combination of what you gave me with -f and -m

still says that it can't find the archive. is there a way to manually point it to the download page as an archive?

---

### Post by jodrre on 2009-06-21
as an ex-mod, i used to hate these posts... but...

i still have a problem. i can't get updates, and when I click on the big red error button next to the time, it says i need to run a partial upgrade. it then says that vmware-server is in an unstable state and needs to be re-installed, and i tell it to delete it, and then it errors out again.

Is there really only one person in the English community that has any remote idea how to fix this problem?

---

