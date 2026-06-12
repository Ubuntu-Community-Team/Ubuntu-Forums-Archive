---
title: "ccsd: Unable to connect to cluster infrastructure after 583560 seconds."
date: 2005-12-21
forum: Installation &amp; Upgrades
---

### Post by RikBlankestijn on 2005-12-21
Hi!

I'm seeing this in the log (/var/log/syslog) ```
Dec 20 20:48:24 localhost ccsd[8281]: Unable to connect to cluster infrastructure after 583500 seconds.
Dec 20 20:48:55 localhost ccsd[8281]: Unable to connect to cluster infrastructure after 583530 seconds.
Dec 20 20:49:25 localhost ccsd[8281]: Unable to connect to cluster infrastructure after 583560 seconds.

```

I keep seeing a new line every 10 seconds or so.

Can anyone help me to fix this? I found that ccsd is "The daemon used to access CCS cluster configuration files.", but I can't find out much more.

---

### Post by hotdoog on 2007-11-08
I have the same problem - nobody has figured it out in 2 years!???

---

### Post by hotdoog on 2007-11-08
Well I googled around a bit. Seems ccsd is the daemon of ccs. Its a cluster thing. its part of a redhat cluster suite of packages. I don't know why it is on our systems. I know when I first got ubuntu I was trigger happy with synaptic and installed all these things just on their cool names... But i don't think this was that. All of the writing about this stuff is very technical and cryptic. But the general idea is clustering computers together to act as one - I guess for example a web server that appears as one computer but actually is many - to make it go faster overall. Anyways... i deleted all the cluster packages. There were a lot. If i have any problems I'll tell ya but I doubt I will. How this got on my system is beyond me.:confused: There is some descriptions of changing your localhost and also your ccs configuration xml file - if you actually need to be running ccsd. But I can't see any point it being on my desktop machine. I don't think ssh xdmcp or samba needs it, and that's all the networking I do.

---

### Post by emery on 2008-03-15
If you wan to remove ccsd from startup :

```
sudo update-rc.d -f cman remove
```

---

