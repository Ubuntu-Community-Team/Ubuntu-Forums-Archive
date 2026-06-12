---
title: "[SOLVED] How to remove java-gcj"
date: 2008-11-19
forum: General Help
---

### Post by pfdevil on 2008-11-19
```
[B]pfdevil@pfdevil-laptop:~$ limewire
Starting LimeWire...
Java exec found in PATH. Verifying...
OOPS, you don't seem to have a valid JRE. LimeWire works best with Sun JRE available at [http://www.java.com](http://www.java.com)
Java exec found in  /usr/lib/jvm/java-gcj/bin/
OOPS, you don't seem to have a valid JRE. LimeWire works best with Sun JRE available at [http://www.java.com](http://www.java.com)
Java exec found in  /usr/lib/jvm/java-6-sun-1.6.0.07/bin/
Suitable java version found  [/usr/lib/jvm/java-6-sun-1.6.0.07/bin/java = 1.6.0_07]
Configuring environment...
Loading LimeWire:[/B]
```

Hey basically when starting eclipse and limewire etc. I get the above output in terminal which is really annoying. So how can I remove java-gcj and use the java6 as default.

Thanks

---

### Post by pfdevil on 2008-11-19
Hey I answered my own question.

```
pfdevil@pfdevil-laptop:~$ sudo update-alternatives --config java

There are 3 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/lib/jvm/java-6-sun/jre/bin/java
          2    /usr/bin/gij-4.2
*+        3    /usr/lib/jvm/java-gcj/jre/bin/java

Press enter to keep the default[*], or type selection number: 1
Using '/usr/lib/jvm/java-6-sun/jre/bin/java' to provide 'java'.
pfdevil@pfdevil-laptop:~$ 
```

Just type in the terminal sudo update-alternatives --config java
and select either 1,2 or 3 depending on you preferences.

Cheers

---

