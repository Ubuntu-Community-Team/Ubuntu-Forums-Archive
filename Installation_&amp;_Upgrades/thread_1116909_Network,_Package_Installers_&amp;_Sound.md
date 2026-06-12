---
title: "Network, Package Installers &amp; Sound"
date: 2009-04-05
forum: Installation &amp; Upgrades
---

### Post by UnknownPal on 2009-04-05
OK so I installed Ubuntu 8.10 fine. Then I did the update thing (the red arrow) and it seemed to be fine, so I restarted as said. Now my internet is really screwed up; it can be fast then it can be slow (like never stops loading the page or timeout, 404s etc.). The only thing I did was to download the updates it said to download. The internet works fine on Windows, and no firewall is running on Ubuntu. 

I'm trying to install the proprietary drivers onto the system so that I can use compiz etc, trying to install "NVIDIA accelerated graphics driver (version 177)", the recommended one. But I tried it and I got "SystemError: Unable to lock /var/cache/apt/archives/lock" (I think from the top of my head). I looked for a solution on the internet which said to delete the file and then do it. So I deleted it, and now it has reappeared when I ran it again just now. But now when I run other package installation applications such as apt-get or aptitude etc. they say "Unable to get exclusive lock - This usually means that another package management application (like apt-get or aptitude) is already running. Please close that application first.", but I am fairly sure that one is not running as I have logged on and off a few times already. I also get the following:

```

unknown@unknown:~$ sudo aptitude update
[sudo] password for unknown: 
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
E: Could not get lock /var/lib/apt/lists/lock - open (11 Resource temporarily unavailable)
E: Couldn't lock list directory..are you root?

```

Also what do I do about sound cards, when I ran Ubuntu a few months back I could never get the sound to work properly. 

Cheers for any help, Unknown.

P.S. I would search the forums better, but my internet means that I cant do that well!

---

### Post by UnknownPal on 2009-04-08
Any ideas anyone; I'd rather not format to be honest.

---

