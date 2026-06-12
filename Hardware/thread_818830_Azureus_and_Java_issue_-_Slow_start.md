---
title: "Azureus and Java issue - Slow start"
date: 2008-06-04
forum: Hardware
---

### Post by adamitj on 2008-06-04
I don't know why, but all Java apps are taking too much time to start, between 3 to 5 minutes.

It is possible to see clearly when trying to start Azureus and connect to Java Console.

My computer is:

HP Pavilion dv6500
AMD Turion 64 X2 TL-59 1.9 ghz
2 Gb RAM
EXT3 partition

Ubuntu 8.04 Hardy Heron

-- Installed Sun JDK/JRE 6.0 from Synaptic
-- Installed Azureus from Synaptic

Any suggestions?

---

### Post by cnb2412 on 2008-10-06
I've got the same problem.

Did you find a solution in the meantime?

---

### Post by adamitj on 2008-10-06
Yup... unfortunately I couldn't solve this problem exactly. What I did is exchange the use of Sun JDK by openJDK which came with Ubuntu repositories.

I left the Sun JDK just to use with Eclipse (to develop my applications). However, the default JDK to execute Java applications still OpenJDK.

I wonder if this problem will be fixed in Ubuntu 8.10, but until that we need to use this workaround.

If you find some better solution, please post it here. This problem occurs in x86 and x86_64 flavors.

---

### Post by daverave999 on 2008-10-24
I was having this problem and I seem to have fixed it. Azureus appears to have been trying to be started from 
/opt/azureus/azureus
rather than
/usr/bin/azureus

I'm not sure if your other java-related issues are trying to use the wrong java, I think that was why mine wasn't working? *shrug* Thought I'd share my remedy just in case it helped...

---

