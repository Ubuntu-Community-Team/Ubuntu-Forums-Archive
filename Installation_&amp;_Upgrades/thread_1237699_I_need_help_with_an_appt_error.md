---
title: "I need help with an appt error"
date: 2009-08-11
forum: Installation &amp; Upgrades
---

### Post by BigCityCat on 2009-08-11
Please help

This is from adept

> Download failed.
The list of errors is attached. The recovery for this case is currently not implemented. If you see 404 errors, it might be useful to try fetching package lists (see the Sources tab) and retrying the operation.

The error was: 
APT Error. Context:
    Package download failed, 
    I wasn't able to locate a file for the sun-java6-bin package. This might mean you need to manually fix this package. (due to missing arch), 
    I wasn't able to locate a file for the sun-java6-jre package. This might mean you need to manually fix this package. (due to missing arch), 

---

### Post by BigCityCat on 2009-08-11
And this is from Kpackagekit

> var/cache/apt/archives/sun-java6-jre_6-14-0ubuntu1.9.04_all.deb Preconfiguring packages ... Preconfiguring packages ... Preconfiguring packages ... (Reading database ... dpkg: serious warning: files list file for package `sun-java6-jre' missing, assuming package has no files currently installed. dpkg: serious warning: files list file for package `sun-java6-bin' missing, assuming package has no files currently installed. 148354 files and directories currently installed.) Preparing to replace sun-java6-jre 6-14-0ubuntu1.9.04 (using .../sun-java6-jre_6-14-0ubuntu1.9.04_all.deb) ... sun-dlj-v1-1 license could not be presented try 'dpkg-reconfigure debconf' to select a frontend other than noninteractive 

---

### Post by stlsaint on 2009-08-11
have you checked the repos for re-installation of packages or boot to live cd for the repair of broken packages?

---

### Post by BigCityCat on 2009-08-11
no, can you tell me how do I use the cd for that?

---

### Post by BigCityCat on 2009-08-11
here is what happened when i try to uninstall the packages

It seems that the recovery has failed. Please fix manually (try dpkg --configure -a and/or apt-get -f install) in terminal... 

The error was: 
APT Error. Context:
    Running dpkg, 
    [ /usr/bin/dpkg, --status-fd, 3, --configure, -a ], 
    Sup-process returned error code 1, 
    Error processing chkrootkit : subprocess post-installation script returned error exit status 1.

---

