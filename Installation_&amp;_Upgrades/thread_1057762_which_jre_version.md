---
title: "which jre version?"
date: 2009-02-02
forum: Installation &amp; Upgrades
---

### Post by bradcan on 2009-02-02
I'm just a bit confused about jre installation.

I appear to have both java-6-openjdk and java-6-sun-1.6.0.10 directories under /usr/lib/jvm (I'm running Ubuntu 8.10)

That's OK, but I wonder how to determine which applications depend on which version?

The default ie the one linked to /usr/bin/java which is linked to /etc/alternatives/java and in turn linked to /usr/lib/jvm/java-6-openjdk/jre/bin/java turns out to be version 1.6.0_0 on the other hand the version in java-6-sun-1.6.0.10/bin is err.. obviously version 1.6.0_10

I have been trying to get Mindterm, which is a cross platform ssh client written in pure java, to work. If I run it using the default java weird things happen to the app window. It just keep getting bigger and bigger! :confused:

Anyhow the fix is simple enough just run using java version 1.6.10 :D

If I attempt to un-install openjdk with the package manager it complains of dependencies. Obviously I could remove it with synaptic, but I just wonder what this will break?

I would much prefer make the default jre the later version and to force the dependency(s) to user the earlier version.

I suppose I could just switch the link in /usr/bin and see what breaks, but this seems a rather drastic approach.

---

### Post by taurus on 2009-02-02
This command will tell you which version is your default.

Applications -> Accessories -> Terminal
```
java -version
```

If you want to switch to another version that is already on your machine, you could run this command to switch it.

```
sudo update-alternatives --config java
```

---

