---
title: "&quot;Could not read network connection list&quot;"
date: 2005-11-23
forum: General Help
---

### Post by carlos1 on 2005-11-23
I'm installing Kubuntu on a new notebook, and I finally got X working, and logged in as root, no problems with the GUI. 
Then when I logged out and tried to log in as a normal user, after entering password I got the following error message (in a dialog box) before any splash screen started up: 
> There was an error setting up inter-process communications for KDE. 
The message returned by the system was: 

Could not read network connection list.
/home/(user)/.DCOPserver_kubuntu_0
Please check that the "dcopserver" program is running!

I checked and the dcopserver program was running, but I stopped and restarted it, and still on joy. 

Does anyone have any suggestions to get over this last hurdle?

---

### Post by mlomker on 2005-11-23
You generally can't log into KDE using root, so you must have made some modifications to do so.  My first guess would be that the permissions are wrong on the file that you mentioned.

Change into the /home/username directory and use **ls -l .D*** to view the permissions on the file.  It does appear that my file was created at bootup, though.

```

mlomker@mlomkernote:~$ ls -l .DCOPserver_mlomkernote__0
-rw-r--r--  1 mlomker mlomker 58 2005-11-23 14:35 .DCOPserver_mlomkernote__0
mlomker@mlomkernote:~$ cat .DCOPserver_mlomkernote__0
local/mlomkernote:/tmp/.ICE-unix/dcop7599-1132778116
7599

```

---

### Post by carlos1 on 2005-11-23
Thanks for the advice. 
I think you are right about the file being created at bootup.
It looks like this was just a broken install somehow, or when I was tinkering to get my graphics card working I did something else. 
so, I did a fresh install, and after installing the fglrx drivers and editing xorg.conf, (for my graphics card, not this) I rebooted and had no problems, so everything is sorted. 
Many thanks.

---

