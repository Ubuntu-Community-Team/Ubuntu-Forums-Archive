---
title: "JVM (java virtual machine)"
date: 2009-05-30
forum: Installation &amp; Upgrades
---

### Post by bergspyder on 2009-05-30
I'm running ubuntu 8.10 on a Dell C640 & all works very well except one (government) website rejects configuration "JVM must be installed". Firefox has "Enable Java" ticked. After extensive internet search, mainly on this forum, I installed "jre-6u13-linux-i586.bin" & "jre-6u12-linux-x64.bin" in /usr/lib but no go. Incidentally, website asking for JVM accepts Windows IE but I don't want to go back to that. Thanks for any help.

---

### Post by techie2go on 2009-05-30
either install sun-java5-plugin

or copy libjavaplugin.so  from the installed java folder to /usr/lib/firefox/plugins

---

