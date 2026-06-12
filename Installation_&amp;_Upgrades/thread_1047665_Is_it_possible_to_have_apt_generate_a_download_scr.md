---
title: "Is it possible to have apt generate a download script for all dependencies?"
date: 2009-01-22
forum: Installation &amp; Upgrades
---

### Post by tvisher on 2009-01-22
Hello Everyone,

I'm trying to get an installation of 8.10 up and running and I'm having problems with apt.  I'm not connected to the Internet and the only other box I have is a Windows machine.  I'm running Cygwin on Windows.  

Anyway, it seems like it should be fairly trivial to generate a script that will download all packages and dependencies that I want to install that I can then run anywhere.  However, I can't for the life of me figure out how to do this.  I found APTonCD but I can't figure out how to use that since the problem is getting the packages in the first place, not making a local repo once they're installed already.

Any help would be greatly appreciated as I'm completely stuck.

---

### Post by Partyboi2 on 2009-01-24
You can use Synaptic Package Manager to generate a script.
[https://help.ubuntu.com/community/Synaptic/PackageDownloadScript](https://help.ubuntu.com/community/Synaptic/PackageDownloadScript)

---

### Post by tvisher on 2009-01-26
Thanks for the tip.  That function looks like what I was looking for.  

Unfortunately, I have previously removed all of the non-CD packages from Synaptic.  Now, when I try to add them back in, I can't because it wants to download them from the Internet.  Is there anything I can do to get them back other than full out reinstalling Ubuntu?

Thanks in advance!

---

### Post by Partyboi2 on 2009-01-26
I am not sure how you could refresh the package list without Internet connection using synaptic or even if its possible. I do how ever know a different way using [[COLOR=Blue]keyrx[/COLOR]]("http://keryx.betaserver.org/"). If you decide to give Keryx ago follow their [[COLOR=Blue]tutorial[/COLOR]]("http://crashsystems.net/2009/01/keryx-tutorial/") through except just before you start, go to Software Sources (System>Admin>Software Sources) and tick all the repositories you want enabled (don't forget to enable updates as well under the update tab) then close Software Sources which will complain and give you a few error messages, when this happens just ignore it as you have still added the repostories you wanted to your sources.list.Then use keyrx to update and install the packages by following the tutorial.

---

### Post by hammer v2 on 2009-02-04
Also check out superdeb.
[http://code.google.com/p/superdeb/](http://code.google.com/p/superdeb/)

The superdeb creator will be available this weekend...

---

