---
title: "samba-common and smbclient errors"
date: 2009-07-31
forum: Installation &amp; Upgrades
---

### Post by mcneilly on 2009-07-31
Recently while updating my system i accidentally shut off the power in the middle of the update, since that time i have received the following error when trying to update anything

```
Setting up samba-common (2:3.3.2-1ubuntu3.1) ...
update-alternatives: internal error: /var/lib/dpkg/alternatives/nmblookup corrupt: invalid update mode
dpkg: error processing samba-common (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of smbclient:
 smbclient depends on samba-common (= 2:3.3.2-1ubuntu3.1); however:
  Package samba-common is not configured yet.
dpkg: error processing smbclient (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 samba-common
 smbclient
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

i tried using synaptic to reinstall the files, but i just received the same error message, any help?

---

### Post by bugslayr on 2010-01-24
Hello mcneilly, I had the very same problem, but do not know how the situation was created.
Matter of factly 3 files were corrupt: nmblookup, net, and testparm
I copied the files from a different machine ... I know this is not a very straight forward solution, but it worked.
As long as I don't know how those files got corrupted, it is rather difficult to take countermeasures.
[FONT=monospace]
[/FONT]See also "man update-alternatives" to see how you would normally modify files in /var/lib/dpkg/alternatives.

I hope this helps!
     Martin

Here is what I added

nmblookup
```
auto
/usr/bin/nmblookup
nmblookup.1.gz
/usr/share/man/man1/nmblookup.1.gz

/usr/bin/nmblookup.samba3
0
/usr/share/man/man1/nmblookup.samba3.1.gz


```

net
```
auto
/usr/bin/net
net.8.gz
/usr/share/man/man8/net.8.gz

/usr/bin/net.samba3
10
/usr/share/man/man8/net.samba3.8.gz


```

testparm
```
auto
/usr/bin/testparm
testparm.1.gz
/usr/share/man/man1/testparm.1.gz

/usr/bin/testparm.samba3
10
/usr/share/man/man1/testparm.samba3.1.gz


```

---

