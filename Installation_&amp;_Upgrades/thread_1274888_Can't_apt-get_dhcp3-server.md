---
title: "Can't apt-get dhcp3-server"
date: 2009-09-25
forum: Installation &amp; Upgrades
---

### Post by tonycollinet on 2009-09-25
I get the following when trying to install dhcp-server. I am running a mythbuntu installation, but am assuming for the purposes of this problem that it is the same as normal 9.04 Ubuntu... - any ideas?

Thanks

********************

sudo apt-get install dhcp3-server

Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  dhcp3-server: Depends: dhcp3-common (= 3.1.1-5ubuntu8) but 3.1.1-5ubuntu8.1 is to be installed
E: Broken packages

---

### Post by Partyboi2 on 2009-09-25
Open a terminal and fix the boken package with
```
sudo apt-get -f install
```
If you still have problem try opening up Synaptic and searching for 'dhcp3-common' and highlight it and select "Package" and then "Force Version" and see if you can slect another package version.

---

### Post by tonycollinet on 2009-09-25
Thanks - the -f option did not help.

However, downgrading dhcp-common from 8.1 to 8 worked (at least I have dhcp3-server installed now, just have to set it up)

For anyone else with the same problem - downgrading also uninstalled dhcp3-client, and ubuntu-minimal(not sure what this is). I re-installed them both before rebooting.

Thanks again.

---

