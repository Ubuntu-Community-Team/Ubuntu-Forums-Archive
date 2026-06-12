---
title: "[SOLVED] Pidgin Backport Error"
date: 2008-11-08
forum: General Help
---

### Post by Yashiro on 2008-11-08
Anyone else have an unresolved dependencies issue with the latest backported Pidgin? (pidgin-data 12502)
Looks like it was pushed to the update system before the AMD64 build was complete. As such there are not compatible binaries and you end up with no Pidgin installed.

---

### Post by azteech on 2008-11-08
At this point it would appear that Pidgin can't be updated through backports, due to dependency issues. Am receiving dependency errors for libpurple0 and pidgin-data.
It isn't just an issue with the AMD64 system. Even though I have an AMD64, I am running the i386 version of Ubuntu, and use Pidgin on that platform as well. When Update manager attempted to accomplish the Pidgin update, it game me a "Partial Update" warning, as well.

> **Yashiro said:**
> Anyone else have an unresolved dependencies issue with the latest backported Pidgin? (pidgin-data 12502)
Looks like it was pushed to the update system before the AMD64 build was complete. As such there are not compatible binaries and you end up with no Pidgin installed.

---

### Post by exploder on 2008-11-08
You might try going to getdeb.net and see what version of Pidgin is available there. I have 2.5.2 installed in Hardy but the backports repo only has 2.5.0. Getdeb.net includes all of the dependencies you need to install.

---

### Post by gururise on 2008-11-08
Same Problem here... I'm on Ubuntu Hardy AMD64 System... had anyone filed a bug report yet?

---

### Post by imbrian on 2008-11-08
Same problem here - also 64-bit.  I can't find the Ubuntu Bug Tracker - did they get rid of it?  I could have sworn they used bugzilla.

---

### Post by azteech on 2008-11-08
Seems someone posted a bug report regarding the upgrade issue; Can be seen here: [https://bugs.launchpad.net/ubuntu/+source/pidgin/+bug/273314](https://bugs.launchpad.net/ubuntu/+source/pidgin/+bug/273314)
But it is not specific to the AMD64 version.

For what it is worth, I have added my input to the above bug report. If folks are having issues with AMD64 version, would recommend filing a new bug against it.

> **gururise said:**
> Same Problem here... I'm on Ubuntu Hardy AMD64 System... had anyone filed a bug report yet?

---

### Post by Yashiro on 2008-11-08
Someone just needs to upload the corresponding libpurple and associated stuffs. Just pushing 'pidgin-data' onto the update system is pretty weak.

This ppa has s correctly built 2.5.1 version.
[https://launchpad.net/~andreas-moog/+archive](https://launchpad.net/~andreas-moog/+archive)


This page has info on the releases in the official backports list
[https://launchpad.net/ubuntu/hardy/+source/pidgin](https://launchpad.net/ubuntu/hardy/+source/pidgin)

---

### Post by azteech on 2008-11-08
Yashiro, adding the ppa you listed still doesn't resolve the issue. Still get the following: 

xxxxxx@xxxxxxxxxxxxxxxxxxxx:~$ sudo apt-get install pidgin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  pidgin: Depends: libpurple0 (>= 1:2.5.1-0ubuntu1) but it is not going to be installed
          Depends: pidgin-data (< 1:2.5.1-z) but 1:2.5.2-0ubuntu1~hardy1 is to be installed
E: Broken packages

> **Yashiro said:**
> Someone just needs to upload the corresponding libpurple and associated stuffs. Just pushing 'pidgin-data' onto the update system is pretty weak.

This ppa has s correctly built 2.5.1 version.
[https://launchpad.net/~andreas-moog/+archive]("https://launchpad.net/%7Eandreas-moog/+archive")


This page has info on the releases in the official backports list
[https://launchpad.net/ubuntu/hardy/+source/pidgin](https://launchpad.net/ubuntu/hardy/+source/pidgin)

---

### Post by Yashiro on 2008-11-08
No it wont resolve the issue because the pidgin-data package is broken.

Remove it. Disable Backports repo.
Re-install the base Pidgin from Hardy.
Add that ppa and upgrade.
It works.

---

### Post by azteech on 2008-11-08
You were correct. Using apt-get to remove "pidgin-data" package, disabling the backports repo, and adding the ppa listed above, does allow one to re-install pidgin.

It would appear that doing this does not affect one's configs/profile. Found I could still get to my saved logs, and all subscribed channels were still in place.

> **Yashiro said:**
> No it wont resolve the issue because the pidgin-data package is broken.

Remove it. Disable Backports repo.
Re-install the base Pidgin from Hardy.
Add that ppa and upgrade.
It works.

---

### Post by Yashiro on 2008-11-10
This is possibly fixed as of 10th November. Check Backports for 2.5.2.

---

