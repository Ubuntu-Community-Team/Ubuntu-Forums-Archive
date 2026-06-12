---
title: "i need to get my wireless working"
date: 2008-10-24
forum: General Help
---

### Post by M!K3_$ on 2008-10-24
I just installed debian (i know it's not ubuntu, but close enough) on my old laptop and debian didn't have any drivers for my wireless card off the install. this laptop doesn't have a wired NIC just a dlink airplus DWL-G650. 
MadWifi said that it suported my dlink, so i downloaded the drivers on another computer and transfered them to my laptop via flash stick. I went to make it on the laptop and i got this...

xsypy:/hom/mike/myPrograms/madwifi-0.9.4# make
/bin/sh: line 0: cd: /lib/modules/2.6.18-6-686/build: No such file or directory
Makefile.inc:66: *** /lib/modules/2.6.18-6-686/build is missing, please set KERNELPATH. Stop.

I don't know what this "build" is, so i want to know what it is and where to get it?

---

### Post by Crossyboi on 2008-10-24
> **M!K3_$ said:**
> I just installed debian (i know it's not ubuntu, but close enough) on my old laptop and debian didn't have any drivers for my wireless card off the install. this laptop doesn't have a wired NIC just a dlink airplus DWL-G650. 
MadWifi said that it suported my dlink, so i downloaded the drivers on another computer and transfered them to my laptop via flash stick. I went to make it on the laptop and i got this...

xsypy:/hom/mike/myPrograms/madwifi-0.9.4# make
/bin/sh: line 0: cd: /lib/modules/2.6.18-6-686/build: No such file or directory
Makefile.inc:66: *** /lib/modules/2.6.18-6-686/build is missing, please set KERNELPATH. Stop.

I don't know what this "build" is, so i want to know what it is and where to get it?

This could possibly help: 

[http://ubuntuforums.org/showthread.php?t=118062]("http://ubuntuforums.org/showthread.php?t=118062")

also 

[http://ubuntuforums.org/search.php?searchid=50235918]("http://ubuntuforums.org/search.php?searchid=50235918")

---

### Post by M!K3_$ on 2008-10-24
no, i know it is an atheros card and it is suported by madwifi, i have the drivers. i just am having problems installing them.
but thank you anyways.

-M

---

### Post by Crossyboi on 2008-10-24
Why not installed ubuntu by the way?

---

### Post by M!K3_$ on 2008-10-24
old laptop wont run it. will run xubuntu if it is dapper. so ya weak sauce

---

