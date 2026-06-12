---
title: "Error when trying to uninstall a package."
date: 2009-07-17
forum: Installation &amp; Upgrades
---

### Post by stewartm82 on 2009-07-17
Hi I am getting the following error when trying to uninstall nginx.  Any suggestions as to how I might fix it. I am out of ideas. 

```

stewart@stewart:/var/cache/apt/archives$ sudo apt-get remove nginx
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  nginx
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 676kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 33726 files and directories currently installed.)
Removing nginx ...
Stopping nginx: invoke-rc.d: initscript nginx, action "stop" failed.
dpkg: error processing nginx (--remove):
 subprocess pre-removal script returned error exit status 1
Errors were encountered while processing:
 nginx
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by dstew on 2009-07-17
It looks like nginx was running at the time removal was attempted, and could not be stopped by the removal script. Make sure the program is stopped, then try again.

---

### Post by stewartm82 on 2009-07-18
I am not sure how to shut nginx down.  I cant find any processes that mention it.

---

### Post by running_rabbit07 on 2009-07-18
Try opening System Monitor and going to the Proccesses tab and finding the program and click to kill process. I don't know what that program is but if it is a system required program you may want to leave it be.

I would also recommend upgrading to a supported version of Ubuntu if possible.

---

### Post by stewartm82 on 2009-07-19
Its a remote server that i dont have access too.  I have tried using ps -aux and htop to see what processes are runing but no luck. I was wondering if a restart would help although the only problem is that i am not sure how to stop nginx from starting at boot.  Can some one tell me how to stop nginx loading at boot?

---

### Post by dstew on 2009-07-20
Look in System --> Preferences --> (Sessions in some versions) --> Startup Programs. If you see this program there, you can edit the startup preferences for it. You can also look in System --> Administration --> Services, and uncheck it if it is there. If none of these work, there are some command line things you can try.

---

### Post by stewartm82 on 2009-07-21
It will have to be command line as the system is a VPS that i own.  Could you tell me how to do this in the command line? I restarted and I still get the same problem but I would suggest that could be because Nginx does not shut down correctly for some reason.

---

