---
title: "[SOLVED] Synaptic presents error on starting, then closes."
date: 2008-11-10
forum: General Help
---

### Post by cpearless on 2008-11-10
I have been using Ubuntu for quite some time now, though recently I have just upgraded to Ubuntu 8.10. Everything has been fine, up until earlier when I tried to start the Synaptic Package Manager and we presented with an error containing this message:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
If I simply closed the window the whole synaptic manager would close, notably all other synaptics (such as the update manager) do exactly the same thing. This baffled me, so I followed the errors advice, though when I do 'dpkg --configure -a' I have absolutley no idea what to do next.

Any help will be greatly appreciated,

Chris

---

### Post by -Zeus- on 2008-11-10
umm, running that command should work by itself, and fix it.  what happened when you ran it?

---

### Post by cpearless on 2008-11-10
It freezes the console then, after about 5 minutes, says command not found, I found this particularly confusing because I have had to use this command before. I've made sure than I was using super user privileges (sudo).

Thanks for the (very) quick reply

Chris

---

### Post by -Zeus- on 2008-11-10
wow, that sounds really bad.  can you run this? tail /var/log/dpkg.log

---

### Post by cpearless on 2008-11-10
Yeah it can execute that fine, here is what results if your interested.

008-11-10 14:42:27 status unpacked flashplugin-nonfree 10.0.12.36ubuntu1
2008-11-10 14:42:27 status unpacked flashplugin-nonfree 10.0.12.36ubuntu1
2008-11-10 14:42:28 startup packages configure
2008-11-10 14:42:28 configure flashplugin-nonfree 10.0.12.36ubuntu1 10.0.12.36ubuntu1
2008-11-10 14:42:28 status unpacked flashplugin-nonfree 10.0.12.36ubuntu1
2008-11-10 14:42:28 status half-configured flashplugin-nonfree 10.0.12.36ubuntu1
2008-11-10 21:07:09 startup packages configure
2008-11-10 21:07:09 configure flashplugin-nonfree 10.0.12.36ubuntu1 10.0.12.36ubuntu1
2008-11-10 21:07:09 status half-configured flashplugin-nonfree 10.0.12.36ubuntu1
2008-11-10 21:07:22 status installed flashplugin-nonfree 10.0.12.36ubuntu1


Chris

---

### Post by -Zeus- on 2008-11-10
well, i'm not seeing any errors there.  could you post the output of the following?

```
apt-cache policy dpkg synaptic
sudo apt-get install firefox
```

---

### Post by cpearless on 2008-11-10
Here you are:
```

dpkg:
  Installed: 1.14.20ubuntu6
  Candidate: 1.14.20ubuntu6
  Version table:
 *** 1.14.20ubuntu6 0
        500 http://gb.archive.ubuntu.com intrepid/main Packages
        100 /var/lib/dpkg/status
synaptic:
  Installed: 0.62.1ubuntu10
  Candidate: 0.62.1ubuntu10
  Version table:
 *** 0.62.1ubuntu10 0
        500 http://gb.archive.ubuntu.com intrepid/main Packages
        100 /var/lib/dpkg/status
cpearless@ShinyUbuntu:~$ sudo apt-get install firefox
Reading package lists... Done
Building dependency tree       
Reading state information... Done
firefox is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 40 not upgraded.

```

Cheers for all of the help

Chris

---

### Post by -Zeus- on 2008-11-10
ok, both synaptic and dpkg look fine.  firefox didn't die, which is odd.  try doing sudo apt-get update && sudo apt-get upgrade to upgrade your packages.  if that works, then the problem is not what i first expected

---

### Post by cpearless on 2008-11-10
Bizarrely that executed fine. I have done a bit of browsing and there seems to be a problem where if Firefox fails to install a plug-in (in this case it looks like a flash plug-in) it doesn't clean up any errors left behind, possible causing a conflict.

Chris

---

### Post by -Zeus- on 2008-11-10
so, does synaptic work now?  you said that it upgraded all the packages fine?

---

### Post by cpearless on 2008-11-10
Yup, it all works great now! Still not too sure on the cause of the multiple freezes, though. Despite this it seems to be behaving fine now.
 
Thanks so much for the help, it's greatly appreciated.

Chris

---

