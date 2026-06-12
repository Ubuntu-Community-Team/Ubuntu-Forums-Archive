---
title: "i cannot install ispconfig"
date: 2009-02-10
forum: Installation &amp; Upgrades
---

### Post by userkiller on 2009-02-10
cd /tmp
    wget [http://www.ispconfig.org/downloads/ISPConfig-3.0.0.8-rc1.tar.gz](http://www.ispconfig.org/downloads/ISPConfig-3.0.0.8-rc1.tar.gz)
    tar xvfz ISPConfig_3.0.0.8-rc1.tar.gz
    cd ispconfig3_install/install/

won't install it. give me a error.

---

### Post by userkiller on 2009-02-10
> **userkiller said:**
> cd /tmp
    wget [http://www.ispconfig.org/downloads/ISPConfig-3.0.0.8-rc1.tar.gz](http://www.ispconfig.org/downloads/ISPConfig-3.0.0.8-rc1.tar.gz)
    tar xvfz ISPConfig_3.0.0.8-rc1.tar.gz
    cd ispconfig3_install/install/

won't install it. give me a error.


this is what is shows me when i run the command:
root@server1:~# cd /tmp
root@server1:/tmp# wget [http://www.ispconfig.org/downloads/I...0.8-rc1.tar.gz](http://www.ispconfig.org/downloads/I...0.8-rc1.tar.gz)
--16:52:08--  [http://www.ispconfig.org/downloads/I...0.8-rc1.tar.gz](http://www.ispconfig.org/downloads/I...0.8-rc1.tar.gz)
           => `I...0.8-rc1.tar.gz'
Resolving [www.ispconfig.org](www.ispconfig.org)... 78.46.214.218
Connecting to [www.ispconfig.org|78.46.214.218|:80](www.ispconfig.org|78.46.214.218|:80)... connected.
HTTP request sent, awaiting response... 404 Not Found
16:52:09 ERROR 404: Not Found.

root@server1:/tmp# tar xvfz ISPConfig_3.0.0.8-rc1.tar.gz
tar: ISPConfig_3.0.0.8-rc1.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
root@server1:/tmp# cd ispconfig3_install/install/
bash: cd: ispconfig3_install/install/: No such file or directory

---

### Post by fuelrod on 2009-04-12
This simply means that a 404 (file not found) error was encountered when trying to retrieve the file from the web site.

---

### Post by StuartN on 2009-04-12
Try [http://downloads.sourceforge.net/ispconfig/ISPConfig-3.0.1.1.tar.gz?use_mirror=](http://downloads.sourceforge.net/ispconfig/ISPConfig-3.0.1.1.tar.gz?use_mirror=)

If you browse to [http://www.ispconfig.org/downloads.htm](http://www.ispconfig.org/downloads.htm) (the home page for the link you gave) you will find this link.

---

