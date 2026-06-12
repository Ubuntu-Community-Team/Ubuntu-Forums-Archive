---
title: "VMWare Error"
date: 2005-11-24
forum: General Help
---

### Post by Bahawolf on 2005-11-24
I recieved this error during the install.. I'm a newbie, although I checked for a similiar problem and haven't been able to find one. All help is appreciated, thank you.

In which directory do you want to install the library files?
[/lib/vmware] /lib/vmware

The path "/lib/vmware" does not exist currently. This program is going to createit, including needed parent directories. Is this what you want? [yes] yes

In which directory do you want to install the manual files?
[/man] /man

The path "/man" does not exist currently. This program is going to create it,
including needed parent directories. Is this what you want? [yes] yes

Unable to get the access rights of source file "./man".

Execution aborted.

---

### Post by xavierh on 2005-11-24
[QUOTE=Bahawolf]I recieved this error during the install.. I'm a newbie, although I checked for a similiar problem and haven't been able to find one. All help is appreciated, thank you.

In which directory do you want to install the library files?
[/lib/vmware] /lib/vmware

The path "/lib/vmware" does not exist currently. This program is going to createit, including needed parent directories. Is this what you want? [yes] yes

In which directory do you want to install the manual files?
[/man] /man

The path "/man" does not exist currently. This program is going to create it,
including needed parent directories. Is this what you want? [yes] yes

Unable to get the access rights of source file "./man".

Execution aborted.[/QUOTE]

this looks like a permission issue. Make sure htat you are running the vmware-install.pl script under the "root" user.

---

### Post by Bahawolf on 2005-11-24
I've tried it with sudo and under the username root... same error.

---

### Post by xavierh on 2005-11-24
[QUOTE=Bahawolf]I've tried it with sudo and under the username root... same error.[/QUOTE]

this is strange indeed, since I have never seen this error. I'm currently running VMWare workstation 5 on my ubuntu box with no problem.

Try this site:
[https://wiki.ubuntu.com/VmWare]("https://wiki.ubuntu.com/VmWare")

ans see if there is anything that could help you with this problem

---

