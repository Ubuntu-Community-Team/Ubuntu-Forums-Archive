---
title: "Eclipse crashing on startup"
date: 2008-10-19
forum: General Help
---

### Post by bertram_wooster on 2008-10-19
Hi,

I am running Hardy on a little msi-wind and have been quite happy until recently with my eclipse and eclipse-cdt install. However, I have recently come a cropper with the ide crashing regularly, and more recently failing to startup. I changed workspace back to the default and things got slightly better, i,e, starting up but crashing regularly. And now even that won't work.

I have tried completely removing and reinstalling all of the packages I can think to do. Even manually removing all eclipse configuration files between uninstalling and reinstalling, but things seem to have gotten worse rather than better.

I would really appreciate some advice here. I have looked online for solutions but there seem to be many related problems, none of which seem to have solutions that will work for me. And I have probably made things worse by trying to sort the problem out by myself.

My [workspace]/.metadata/.log file gives the following:

```
!SESSION 2008-10-19 19:14:15.647 -----------------------------------------------
eclipse.buildId=M20070212-1330
java.fullversion=GNU libgcj 4.2.3 (Ubuntu 4.2.3-2ubuntu6)
BootLoader constants: OS=linux, ARCH=x86, WS=gtk, NL=en_GB
Command-line arguments:  -os linux -ws gtk -arch x86

!ENTRY org.eclipse.osgi 2 1 2008-10-19 19:14:26.823
!MESSAGE NLS missing message: initializer_error in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2008-10-19 19:14:26.844
!MESSAGE NLS missing message: fileInitializer_fileNotFound in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2008-10-19 19:14:26.844
!MESSAGE NLS missing message: fileInitializer_IOError in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2008-10-19 19:14:26.845
!MESSAGE NLS missing message: fileInitializer_missingFileName in: org.eclipse.core.internal.runtime.messages
!SESSION 2008-10-19 19:25:08.715 -----------------------------------------------
eclipse.buildId=M20070212-1330
java.fullversion=GNU libgcj 4.2.3 (Ubuntu 4.2.3-2ubuntu6)
BootLoader constants: OS=linux, ARCH=x86, WS=gtk, NL=en_GB
Command-line arguments:  -os linux -ws gtk -arch x86

!ENTRY org.eclipse.osgi 2 1 2008-10-19 19:25:17.683
!MESSAGE NLS missing message: initializer_error in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2008-10-19 19:25:17.684
!MESSAGE NLS missing message: fileInitializer_fileNotFound in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2008-10-19 19:25:17.684
!MESSAGE NLS missing message: fileInitializer_IOError in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2008-10-19 19:25:17.684
!MESSAGE NLS missing message: fileInitializer_missingFileName in: org.eclipse.core.internal.runtime.messages
!SESSION 2008-10-19 19:30:04.934 -----------------------------------------------
eclipse.buildId=M20070212-1330
java.fullversion=GNU libgcj 4.2.3 (Ubuntu 4.2.3-2ubuntu6)
BootLoader constants: OS=linux, ARCH=x86, WS=gtk, NL=en_GB
Command-line arguments:  -os linux -ws gtk -arch x86

!ENTRY org.eclipse.osgi 2 1 2008-10-19 19:30:13.585
!MESSAGE NLS missing message: initializer_error in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2008-10-19 19:30:13.585
!MESSAGE NLS missing message: fileInitializer_fileNotFound in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2008-10-19 19:30:13.586
!MESSAGE NLS missing message: fileInitializer_IOError in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2008-10-19 19:30:13.586
!MESSAGE NLS missing message: fileInitializer_missingFileName in: org.eclipse.core.internal.runtime.messages
```

All help appreciated,
Luke

---

### Post by shawnrgr on 2008-10-21
please run eclipse from a terminal and paste the output.

also please paste the output of

```
update-alternatives --list java
```

---

### Post by feydrutha on 2008-10-21
Similar problem here. Eclipse really is a big mess on ubuntu, I constantly have to tweak this and that to get it to work. I am on a 64 bit machine/kernel.

I had version 3.2.2 manually installed from a tarball, and running on I don't know what vm (because the repository versions had frequent crashes) and today (after not using it for a week or two) it was systematically crashing on startup.

So I decided to give the repos a try again. Installed eclipse-gcj, and got it to run with java-gcj vm.

It now crashes on startup with following message:

JVM terminated. Exit code=1
/usr/lib/jvm/java-gcj/bin/java
-Djava.library.path=/usr/lib/jni
-Dgnu.gcj.precompiled.db.path=/var/lib/gcj-4.2/classmap.db
-Dgnu.gcj.runtime.VMClassLoader.library_control=never
-Dosgi.locking=none
-jar /usr/lib/eclipse/startup.jar
-os linux
-ws gtk
-arch x86_64
-launcher /usr/lib/eclipse/eclipse
-name Eclipse
-showsplash 600
-exitdata 1690050
-install /usr/lib/eclipse
-vm /usr/lib/jvm/java-gcj/bin/java
-vmargs
-Djava.library.path=/usr/lib/jni
-Dgnu.gcj.precompiled.db.path=/var/lib/gcj-4.2/classmap.db
-Dgnu.gcj.runtime.VMClassLoader.library_control=never
-Dosgi.locking=none
-jar /usr/lib/eclipse/startup.jar 

From the commandline I was getting this:

searching for compatible vm...
  testing /usr/lib/jvm/java-gcj...found
Could not create /usr/local/lib/eclipse/.eclipseextension. Please run as root:
    touch /usr/local/lib/eclipse/.eclipseextension
    chmod 2775 /usr/local/lib/eclipse/.eclipseextension
    chown root:staff /usr/local/lib/eclipse/.eclipseextension

I followed the instructions, and now I am only getting this:

searching for compatible vm...
  testing /usr/lib/jvm/java-gcj...found

But I still get the same crash. By the way it crashes before it even asks where my workspace is so it doesn't depend on my workspace.

I also had similar results with sun java 6, and the normal eclipse package, although the crash was happening later (during workspace load).

So which combination of eclipse/virtual machine should one use for a 64 bit machine? there are too many options to try them all!!! Should I try the ia32 vm packages?

---

### Post by feydrutha on 2008-10-21
By the way:

~$ update-java-alternatives -l
ia32-java-1.5.0-sun 53 /usr/lib/jvm/ia32-java-1.5.0-sun
ia32-java-6-sun 63 /usr/lib/jvm/ia32-java-6-sun
java-6-openjdk 1061 /usr/lib/jvm/java-6-openjdk
java-6-sun 63 /usr/lib/jvm/java-6-sun
java-gcj 1042 /usr/lib/jvm/java-gcj


~$ cat /etc/eclipse/java_home 
# This file determines the search order the Eclipse Platform uses to find a
# compatible JAVA_HOME. This setting may be overridden on a per-user basis by
# altering the JAVA_HOME setting in ~/.eclipse/eclipserc.

#/usr/lib/jvm/java-7-icedtea
/usr/lib/jvm/java-gcj
/usr/lib/kaffe/pthreads
/usr/lib/jvm/java-6-sun
/usr/lib/jvm/java-1.5.0-sun
/usr/lib/j2se/1.5
/usr/lib/j2se/1.4
/usr/lib/j2sdk1.5-ibm
/usr/lib/j2sdk1.4-ibm
/usr/lib/j2sdk1.6-sun
/usr/lib/j2sdk1.5-sun
/usr/lib/j2sdk1.4-sun

---

### Post by feydrutha on 2008-10-21
Solved for me, more or less..

It seems that using the eclipse (rather than eclipse-gcj) package, toghether with the gcj jvm works. Rather counter-intuitive, but hey.. I thing the ia32 packages of sun's jvm would probably work too, I might try that later.

---

### Post by jespdj on 2008-10-21
Make sure that you are running Eclipse on Sun Java or OpenJDK Java, and not on the old, slow and incomplete GNU Java. Install Sun Java 6 like this:
```
sudo apt-get install sun-java6-jdk
```
Then make sure that it's used by default:
```
sudo update-alternatives ---config java
```
Select Sun Java 6 in the menu that appears.

---

### Post by feydrutha on 2008-10-21
> **jespdj said:**
> Make sure that you are running Eclipse on Sun Java or OpenJDK Java, and not on the old, slow and incomplete GNU Java. Install Sun Java 6 like this:
```
sudo apt-get install sun-java6-jdk
```
Then make sure that it's used by default:
```
sudo update-alternatives ---config java
```
Select Sun Java 6 in the menu that appears.

First of all, eclipse totally ignores the java-alternatives thing. To make it choose which java to use you need to edit the /etc/eclipse/java_home file.

Second, I have tried eclipse on sun-java6-jdk and it never worked properly on a 64 bit machine. Maybe I should try the ia32 java package, but the 64 bit sun java 6 is badly broken. 

I think the real alternatives are either ia32 sun java 5 or, as you say, open-jdk, which I just tested and works.

---

### Post by bertram_wooster on 2008-10-22
Hi all, and thankyou for all the help,

I am sorry I didn't reply before or post  the requested output, but I have since sorted the problems out along the lines suggested by some of you.

I had a conflict with some of the gcj packages I think, and after using my new favourite command:

```

sudo apt-get purge...

```

and reinstalling the sun java libraries and the basic eclipse and eclipse-cdt I was on my way again.

Thanks again,
Luke

P.S. and BTW: do any of you know how to get the files ordered by type in the C/C++ Projects window of the cdt perspective.

At the moment they are ordered like so:

Project
 |- Aardvark.h
 |- ...
 |- Zulu.h
 |- Aardvark.cpp
 |- ...
 `- Zulu.cpp

and I would prefer that they were ordered like so:

Project
 |- Aardvark.h
 |- Aardvark.cpp
 |- ...
 |- ...
 |- Zulu.h
 `- Zulu.cpp


I had it on the old install but cannot seem to find the option on the new one. On windoze systems it normally falls under something like:

view --> order_by --> name/type

---

### Post by save2 on 2009-03-28
I downloaded Eclipse 3.4 and while trying to start it (when it got the the workspace loading) it crashed with a blank pop up window.
I solved this issue by : uninstalling xulrunner package.

BTW: I use Sun's 1.6 JVM

---

### Post by johnh10000 on 2012-04-25
> **save2 said:**
> I downloaded Eclipse 3.4 and while trying to start it (when it got the the workspace loading) it crashed with a blank pop up window.
I solved this issue by : uninstalling xulrunner package.

BTW: I use Sun's 1.6 JVM

cheers that helped, works on zenwalk too

---

