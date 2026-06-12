---
title: "Installing JWSDP from Sun download"
date: 2009-02-18
forum: Installation &amp; Upgrades
---

### Post by java_man on 2009-02-18
Hello world,

I need to use JAXB in my Eclipse installation of Java 1.5. 
I have downloaded jwsdp-2_0-unix.sh from Sun
When I run the install script I get the error below.

What's up with that? Please tell me it's something simple.
For now JAXB is all I want - is there an easier way? 
In a perfect world Synaptic could go grab Java 1.6 AND JAXB before breakfast - alas.

error>>
Using /var/tmp as temporary directory...
Searching for Java(TM) 2 Platform, Standard Edition...
tail: cannot open `+368' for reading: No such file or directory
Initializing InstallShield Wizard...
Exception in thread "main" java.lang.NoClassDefFoundError: JWSDP
   at gnu.java.lang.MainThread.run(libgcj.so.81)
Caused by: java.lang.ClassNotFoundException: JWSDP not found in gnu.gcj.runtime.SystemClassLoader{urls=[file:/var/tmp/jwsdp-2_0-unix.sh.11500.jar], parent=gnu.gcj.runtime.ExtensionClassLoader{urls=[], parent=null}}
   at java.net.URLClassLoader.findClass(libgcj.so.81)
   at gnu.gcj.runtime.SystemClassLoader.findClass(libgcj.so.81)
   at java.lang.ClassLoader.loadClass(libgcj.so.81)
   at java.lang.ClassLoader.loadClass(libgcj.so.81)
   at gnu.java.lang.MainThread.run(libgcj.so.81)
<<end error

---

### Post by theDaveTheRave on 2009-02-18
java_man

Have you tried installing from a bundled package?

and are you sure it isn't an issue with eclipse not "seeing" the java classpath, as the error message looks to be reminiscent of that type of problem.

David

---

### Post by theDaveTheRave on 2009-02-21
java_man

are you still having this problem?

if not what was your solution? I am interested as I run a lot of java programs (development etc), and I may come up with this issue in the future, so it would be good to learn from your experience.

Thanks

David

---

### Post by java_man on 2009-02-26
DaveTheRave,
Yes - still. I think I will need to drop the dime and get support from Sun.  I don't think JWSDP is available (yet) as a bundled package but I agree that would be the best approach. Eclipse seems to see the java classpath ok - its doing all of its ordinary java things very well.

I don't quite understand the licensing details between Sun and Ubuntu but I have made many downloads from Sun before and this has been one of the more difficult. 
I'm a little spoiled because I work in a large information systems company and there I HAVE PEOPLE to take care of downloads and licensing issues. When we decided to use JAXB it was ready for me by the end of the day.

I will get back to this later today - thanks for your help.

---

### Post by endysea on 2009-03-10
Try

```
$ export _POSIX2_VERSION=199209
$ ./jwsdp-2_0-unix.sh
```

---

### Post by tendonstrength on 2010-01-28
endysea's solution worked for me.

---

### Post by ruwan.jayaweera on 2010-06-22
> **endysea said:**
> Try

```
$ export _POSIX2_VERSION=199209
$ ./jwsdp-2_0-unix.sh
```

endysea, Thank you. This works for me too. But what does this actually do?

---

### Post by ppetrovic on 2011-01-06
unfortunately, export _POSIX2_VERSION=199209 does not help in my case, but the same error is detected.
---------
(I have also fixed the bug with the tail command,
using "tail --lines=+386" instead of "tail +376", which
does not work on Ubuntu), but the exception is still coming
---------


./jwsdp-2_0-unix.sh

For help, type './jwsdp-2_0-unix.sh -help'

Using /var/tmp as temporary directory...
Searching for Java(TM) 2 Platform, Standard Edition...
Initializing InstallShield Wizard...
Exception in thread "main" java.lang.NoClassDefFoundError: JWSDP
Caused by: java.lang.ClassNotFoundException: JWSDP
        at java.net.URLClassLoader$1.run(URLClassLoader.java:202)
        at java.security.AccessController.doPrivileged(Native Method)
        at java.net.URLClassLoader.findClass(URLClassLoader.java:190)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:307)
        at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:301)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:248)
Could not find the main class: JWSDP.  Program will exit.

---

### Post by ppetrovic on 2011-01-06
ok, sorry, downloading again and applying the export again fixed it. thanks!

---

### Post by ppetrovic on 2011-01-06
anyway, it does not help. the archive is not able to install with tomcat6, it only complains there is no tomcat5, and one has to choose "no web container", but then it does not unpack anything from the archive as it seems.

---

### Post by Segaman on 2011-04-10
I got this error after ```
export  _POSIX2_VERSION=199209
```

```
The wizard cannot continue because of the following error: could not load wizard specified in /wizard.inf (104)
```

---

### Post by slyblade900 on 2011-05-08
Thank you all for these replies. I'm hving this problem too. Can some admin help on setting up jwsdp ? I'm running on natty. I have succesfully set the java environment variable.

---

### Post by Tony_Harrison on 2011-08-02
Also running Natty here.

Having same issue as Segaman. Has anyone solved this one yet?

:(

---

### Post by aguizar on 2011-09-03
> **Segaman said:**
> I got this error after export  _POSIX2_VERSION=199209:
The wizard cannot continue because of the following error: could not load wizard specified in /wizard.inf (104)

If you run the jwsdp install script as shown below, it will print the reason why it fails.
```
sh jwsdp-2_0-unix.sh -is:debug 1
``` In my case the output is:
```
com.jxml.quick.QPE; lineNumber: 0; columnNumber: 0; java.lang.ClassNotFoundException: sun.beans.editors.BoolEditor
```followed by a stack trace.

In my computer, the install script is detecting and using OpenJDK 6 to run the JWSDP installer. Unfortunately it seems to rely on this sun.beans.editors.BoolEditor class which is not part of the Java API. The rt.jar shipped with OpenJDK 6 includes sun.beans.editors.BooleanEditor but not BoolEditor.

My solution was to tell the installer to use Sun JDK 5 to run the JWSDP installer, as follows.
```
sh jwsdp-2_0-unix.sh -is:javahome /etc/alternatives/jre_1.5.0
```If needed, replace **/etc/alternatives/jre_1.5.0** with your Sun JDK 5 home directory.

---

