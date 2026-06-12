---
title: "Cannot Update, Cannot Install Apps"
date: 2009-06-12
forum: Installation &amp; Upgrades
---

### Post by Crunchy the Headcrab on 2009-06-12
Hey all.  I'm new to Linux.  I decided that I'd give OpenSuse 11.1, Kubuntu/ubuntu 9.04 a try.  After using all three I am pretty confident that I want to use the Gnome interface of ubuntu 9.04.  However, after reinstalling it I now have errors any time I try to update or install any apps.  I have this error regardless of whether I use the terminal or the synaptic GUI.

> Failed to check for installed and available applications

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.

> Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_jaunty_universe_binary-amd64_Packages, E:The package lists or status file could not be parsed or opened.'

Weird that I never had this problem before I tried the other distros and now after 3 attempts at reinstalling I am still having them.

---

### Post by Crunchy the Headcrab on 2009-06-12
Whatever, it's working now.  Man that's annoying.

Edit: No, actually it's not.  Says the update failed but now when I try to update it says my system is up to date.  How about some consistency :@

---

