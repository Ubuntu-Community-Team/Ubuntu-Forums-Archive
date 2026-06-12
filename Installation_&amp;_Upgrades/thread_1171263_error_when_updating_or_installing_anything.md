---
title: "error when updating or installing anything"
date: 2009-05-27
forum: Installation &amp; Upgrades
---

### Post by help-me on 2009-05-27
help whenever i try to install or update anything this error comes up

An unresolvable problem occurred while initialising the package information.

Please report this bug for the 'update-manager' package and try to include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/ubuntu.mi.hs-heilbronn.de_other_opendicom_._Packages, E:The package lists or status file could not be parsed or opened.'

i have seen similar problems but none of the solutions have worked

please help me i have no clue what to do apart from a clean install(which i don't want to do again)

---

### Post by help-me on 2009-05-27
help whenever i try to install or update anything this error comes up

An unresolvable problem occurred while initialising the package information.

Please report this bug for the 'update-manager' package and try to include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/ubuntu.mi.hs-heilbronn.de_other_opendicom_._Packages, E:The package lists or status file could not be parsed or opened.'

i have seen similar problems but none of the solutions have worked

---

### Post by help-me on 2009-05-27
help whenever i try to install or update anything this error comes up

An unresolvable problem occurred while initialising the package information.

Please report this bug for the 'update-manager' package and try to include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/ubuntu.mi.hs-heilbronn.de_other_opendicom_._Packages, E:The package lists or status file could not be parsed or opened.'

i have seen similar problems but none of the solutions have worked

---

### Post by drs305 on 2009-05-27
Have you tried changing to another server? There is a problem in the list being presented by the heilbronne server. It's possible, although I don't know how likely, another server's version doesn't contain the same error. 

To change servers, in either Software Sources or Synaptic: Settings, Repositories, Download From: Other, then select another server.  Press "Select Server" and then Reload from the Synaptic menu.

You could also either disable the entry for this server in sources.list, although this solution would prevent you from getting packages from that source.

---

### Post by overdrank on 2009-05-27
Threads merged :)

---

### Post by help-me on 2009-05-27
thanks its working now it was really annoying

---

### Post by help-me on 2009-05-27
thanks all working now

---

