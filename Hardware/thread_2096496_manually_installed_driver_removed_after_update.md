---
title: "manually installed driver removed after update"
date: 2012-12-20
forum: Hardware
---

### Post by Hammadnadeemx on 2012-12-20
i have a hd7870 2gb on Ubuntu 12.10 64bit with the amd 12.11 beta driver installed manually . every thing was fine except for compiz crashing regularly and after a system update ( new kernel ) i was greated with ubuntu running in low graphics mode and a few options to reset default config. if i choose to run Ubuntu in low gfx mode for one session , nothing happens. i can access my drive through windows using ext4 reading software. any help would be appreciated.

---

### Post by Yellow Pasque on 2012-12-20
You need to use dkms so that kernel updates don't screw up your system: [http://wiki.cchtml.com/index.php/Ubuntu_Quantal_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29_BETA.2FEXPERIMENTAL](http://wiki.cchtml.com/index.php/Ubuntu_Quantal_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29_BETA.2FEXPERIMENTAL)

---

### Post by Hammadnadeemx on 2012-12-20
> **Temüjin said:**
> You need to use dkms so that kernel updates don't screw up your system: [http://wiki.cchtml.com/index.php/Ubuntu_Quantal_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29_BETA.2FEXPERIMENTAL](http://wiki.cchtml.com/index.php/Ubuntu_Quantal_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29_BETA.2FEXPERIMENTAL)

How can i install dkms now . i have access to ubuntu partition. please give me a step by step guide . maybe i have to re install ubuntu .

---

### Post by Hammadnadeemx on 2012-12-25
no replies so i reinstalled ubuntu 12.10 and now i installed amd 12.10 driver manually. but after reboot  there is no unity side bar (dash) , no close minimize buttons on the edges ,no top bar with time and shutdown options, just a desktop background. please help me . and please give me a step by step guide through a terminal as i can access it through ctrl alt t .

---

