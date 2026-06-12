---
title: "Upgrading individual packages to newer dist withut full dist-upgrade"
date: 2009-07-27
forum: Installation &amp; Upgrades
---

### Post by reg2117 on 2009-07-27
Forum Members,

I'm trying to open a range of ports on a 8.04 LTS server using ufw. It's exactly the same problem as [[COLOR="Blue"]_this thread_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=886693"). 

Unfortunately, port ranges aren't supported in the 8.04 LTS version (0.16.2). ([[COLOR="Blue"]_UbuntuFirewall Wiki_[/COLOR]]("https://wiki.ubuntu.com/UbuntuFirewall#Command-line%20Interface")).

Is there a method for upgrading the ufw package to the 9.04 version without
1. breaking the system
2. a full upgrade
3. this being a complete science project

Any help would be appreciated.

---

### Post by Sef on 2009-07-27
System > Administration > Software Sources > Updates > tic Unsupported Updates

---

### Post by reg2117 on 2009-07-29
Thanks for the reply.
I am running Kubuntu desktop. Unsupported updates was already checked in the adept manager and the 0.16.2.4 version is installed. There does not appear to be any mechanism for upgrading this package.
Any way method to force this package to the 9.04 version (0.27-0ubuntu2)?
Thanks in advance.

---

