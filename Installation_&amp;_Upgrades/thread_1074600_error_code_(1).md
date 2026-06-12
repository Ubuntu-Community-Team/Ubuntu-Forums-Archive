---
title: "error code (1)"
date: 2009-02-19
forum: Installation &amp; Upgrades
---

### Post by frozie on 2009-02-19
Please help me,
I have a problem:

Setting up acpid (1.0.4-5ubuntu9.1) ...
usage: update-rc.d [-n] [-f] <basename> remove
       update-rc.d [-n] <basename> defaults [NN | sNN kNN]
       update-rc.d [-n] <basename> start|stop NN runlvl [runlvl] [...] .
		-n: not really
		-f: force
dpkg: error processing acpid (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of acpi-support:
 acpi-support depends on acpid (>= 1.0.4-1ubuntu4); however:
  Package acpid is not configured yet.
dpkg: error processing acpi-support (--configure):
 dependency problems - leaving unconfigured
Setting up snmpd (5.4.1~dfsg-4ubuntu4.2) ...
usage: update-rc.d [-n] [-f] <basename> remove
       update-rc.d [-n] <basename> defaults [NN | sNN kNN]
       update-rc.d [-n] <basename> start|stop NN runlvl [runlvl] [...] .
		-n: not really
		-f: force
dpkg: error processing snmpd (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 acpid
 acpi-support
 snmpd
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by Crash54 on 2009-03-01
It is quite possible that this is caused by having some 3rd party software repository activated.  

See [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)
for a discussion on this.

On the other hand, I happened to find the culprit that was causing this particular problem before I came across the 3rd party software activation that was causing the rest of my problems (ie: when I cured the acpid problem, others still existed that needed further attention).
So, getting back to my comments, here is what I found that cured this problem.

It turns out, that the error I kept getting when trying to install various packages:

Setting up acpid (1.0.4-5ubuntu9.1) ...
usage: update-rc.d [-n] [-f] <basename> remove
       update-rc.d [-n] <basename> defaults [NN | sNN kNN]
       update-rc.d [-n] <basename> start|stop NN runlvl [runlvl] [...] .
        -n: not really
        -f: force
dpkg: error processing acpid (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 acpid

Was due to a script, /var/lib/dpkg/info/acpid.postinst , that had a deprecated usage of update-rc.d in it:

       update-rc.d multiuser 10 21 


As described in the posting at:

[https://lists.ubuntu.com/archives/ubuntu-devel-announce/2008-June/000430.html](https://lists.ubuntu.com/archives/ubuntu-devel-announce/2008-June/000430.html)


What fixed it for me was to edit this line and replace it with:

       update-rc.d acpid start 10 2 3 4 5 . stop 21 1 .

I'm afraid I don't know exactly what it means, but it worked for me.

---

