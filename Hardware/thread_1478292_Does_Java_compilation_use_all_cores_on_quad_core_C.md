---
title: "Does Java compilation use all cores on quad core CPU?"
date: 2010-05-09
forum: Hardware
---

### Post by r-senior on 2010-05-09
Does anyone build Java applications on a quad core processor with Ubuntu? Is it sufficiently parallel to use all the cores?

I'm particularly interested in NetBeans/Maven and whether they take advantage of having four cores rather than two. I can see that my current setup (Lucid, NetBeans 6.8, Maven 2.2.1) uses both cores on my dual core laptop with both cores maxing up to near 100% when Netbeans scans a project or Maven does a build.

Any experiences welcome, especially of these two tools.

---

### Post by fishtoprecords on 2010-05-09
It depends on which compiler you are using. I'm pretty sure that parallel compilation is a very hard task, you tend to get a lot of interdependencies in non-trivial code.

I can say that my recently built Core2Quad with 8GB of ram is amazingly faster than my old core-2 duo with 2GB of ram, both using Netbeans to drive the compilation. Its at least four times faster. Now the new machine has more memory, faster disks, etc and each core of the quad is faster then each in the duo.

Once you are running, the JVM can support multiple cores, again, its specific to which JVM you are using.

Of course, writing proper threaded code is made easier by the java.util.concurrent stuff, that is not at all the same as making it easy to write parallel code

---

