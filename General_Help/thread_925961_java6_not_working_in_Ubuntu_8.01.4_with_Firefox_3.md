---
title: "java6 not working in Ubuntu 8.01.4 with Firefox 3"
date: 2008-09-21
forum: General Help
---

### Post by mpolito1969 on 2008-09-21
I think there is something not working with my installation of java6 JRE, I have installed the following packages through System -> administration -> "Synaptic package manager":

sun-java6-bin
sun-java6-jre
sun-java6-plugin

But Firefox 3 doesn't run this Java applet:

[http://meter.mclink.it/applet.html](http://meter.mclink.it/applet.html)

Can you help me troubleshooting the issue?

Ciao,
Max

---

### Post by ju2wheels on 2008-09-21
Ok so if I recall correctly once you have those installed, then open a terminal by Applications -> Accessories -> Terminal.

Then do this:
```

sudo update-java-alternatives -s java-6-sun

```

After that open /etc/jvm with an editor and make sure java 6 is the first one in the list of JVM's. Give your machine a reboot and you should be good.

```

sudo gedit /etc/jvm

```

---

### Post by mpolito1969 on 2008-09-21
> **ju2wheels said:**
> 
After that open /etc/jvm with an editor and make sure java 6 is the first one in the list of JVM's. Give your machine a reboot and you should be good.

```

sudo gedit /etc/jvm

```

After doing what you told me to do, this is the content of that file:

```

# This file defines the default system JVM search order. Each
# JVM should list their JAVA_HOME compatible directory in this file.
# The default system JVM is the first one available from top to
# bottom.

/usr/lib/jvm/java-gcj
/usr/lib/jvm/ia32-java-1.5.0-sun
/usr/lib/jvm/java-1.5.0-sun
/usr


```

Is that right?

Ciao,
Max

---

### Post by ju2wheels on 2008-09-21
Here is mines from my laptop:

```

> more /etc/jvm
# This file defines the default system JVM search order. Each
# JVM should list their JAVA_HOME compatible directory in this file.
# The default system JVM is the first one available from top to
# bottom.

/usr/lib/jvm/java-6-sun
/usr/lib/jvm/java-gcj
/usr/lib/jvm/ia32-java-1.5.0-sun
/usr/lib/jvm/java-1.5.0-sun
/usr

```

---

### Post by mpolito1969 on 2008-09-24
> **ju2wheels said:**
> Here is mines from my laptop:


Problem solved, thanks a lot.

Ciao,
Max

---

