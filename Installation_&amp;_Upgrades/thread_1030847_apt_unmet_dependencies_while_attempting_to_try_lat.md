---
title: "apt unmet dependencies while attempting to try latest KDE beta"
date: 2009-01-04
forum: Installation &amp; Upgrades
---

### Post by _axiom_ on 2009-01-04
[COLOR="Red"]sudo dpkg -i --force-overwrite /var/cache/apt/archives/koffice-data-kde4_1%3a1.9.98.2-0ubuntu3~intrepid2_all.deb

That fixed it for me.  -Axiom
[/COLOR]



I was trying to install the latest KDE beta based on this instructions on this page: 
[http://www.kubuntu.org/node/58](http://www.kubuntu.org/node/58)

I skipped the step about removing the koffice-data-kde4 package (too late I regret it).

Now I am stuck in some sort of loop where apt thinks there is an unmet dependency, and apt-get -f install will not fix it.



```

Package koffice-libs is not installed, so not removed                                                    
You might want to run `apt-get -f install' to correct these:                                             
The following packages have unmet dependencies:                                                          
  koffice-libs-kde4: Depends: koffice-data-kde4 (>= 1:1.9.98.2-0ubuntu3~intrepid2) but 1:1.9.98.1-0ubuntu2 is to be installed                                                                                     
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).                
axiom@axiom:~$ sudo apt-get -f install  

```

```

$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  kplato-kde4 kdeplasma-addons-data libifp4 libnjb5
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  koffice-data-kde4
Suggested packages:
  koffice-doc-html-kde4
The following packages will be upgraded:
  koffice-data-kde4
1 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
4 not fully installed or removed.
Need to get 0B/1390kB of archives.
After this operation, 36.9kB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  koffice-data-kde4
Install these packages without verification [y/N]? y
(Reading database ... 191144 files and directories currently installed.)
Preparing to replace koffice-data-kde4 1:1.9.98.1-0ubuntu2 (using .../koffice-data-kde4_1%3a1.9.98.2-0ubuntu3~intrepid2_all.deb) ...
Unpacking replacement koffice-data-kde4 ...
dpkg: error processing /var/cache/apt/archives/koffice-data-kde4_1%3a1.9.98.2-0ubuntu3~intrepid2_all.deb(--unpack):
 trying to overwrite `/usr/share/icons/oxygen/16x16/actions/object-ungroup.png', which is also in package kde-icons-oxygen
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/koffice-data-kde4_1%3a1.9.98.2-0ubuntu3~intrepid2_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

How do I escape this madness so I can install things again?

---

### Post by abn91c on 2009-01-04
did you run sudo dpkg --configure -a

---

### Post by _axiom_ on 2009-01-04
Hmm.. I don't think that is actually doing anything.

The apt-get -f install (above) is odd, because it looks like it is going to work, but then dies on the mysterious "broken pipe" (what is that, and how would I debug?)

```
$ sudo dpkg --configure -a
dpkg: dependency problems prevent configuration of koffice-libs-kde4:
 koffice-libs-kde4 depends on koffice-data-kde4 (>= 1:1.9.98.2-0ubuntu3~intrepid2); however:
  Version of koffice-data-kde4 on system is 1:1.9.98.1-0ubuntu2.
dpkg: error processing koffice-libs-kde4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of krita-kde4:
 krita-kde4 depends on koffice-libs-kde4 (>= 1:1.9.98.2-0ubuntu3~intrepid2); however:
  Package koffice-libs-kde4 is not configured yet.
dpkg: error processing krita-kde4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kplato-kde4:
 kplato-kde4 depends on koffice-libs-kde4 (>= 1:1.9.98.2-0ubuntu3~intrepid2); however:
  Package koffice-libs-kde4 is not configured yet.
dpkg: error processing kplato-kde4 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 koffice-libs-kde4
 krita-kde4
 kplato-kde4
```

---

