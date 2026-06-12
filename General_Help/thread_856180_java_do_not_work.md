---
title: "java do not work"
date: 2008-07-11
forum: General Help
---

### Post by Oddgeir on 2008-07-11
My java do not work and the Java updates wont install it's the sun java doc who will not install whit ubuntu update and i cannot loginto my bank for instance...

ive been trying for months now to make java work but with no luck can anyone take the time to help me?

(:i'm totaly noob tho so please be patient:)

here is the output of "dpkg -l sun-java* > dpkg-l.txt"
```
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-f/Unpacked/Failed-cfg/Half-inst/t-aWait/T-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name                                       Version                                            Description
+++-==========================================-==================================================-============================================
un  sun-java5-jre                              <none>                                             (no description available)
ii  sun-java6-bin                              6-06-0ubuntu1                                      Sun Java(TM) Runtime Environment (JRE) 6 (ar
iF  sun-java6-doc                              6-06-0ubuntu1                                      Sun JDK(TM) Documention -- integration insta
ii  sun-java6-fonts                            6-06-0ubuntu1                                      Lucida TrueType fonts (from the Sun JRE)
un  sun-java6-jdk                              <none>                                             (no description available)
ii  sun-java6-jre                              6-06-0ubuntu1                                      Sun Java(TM) Runtime Environment (JRE) 6 (ar
un  sun-java6-plugin                           <none>                                             (no description available)
```

When i try upating i can't install and after pressing NO+Return i get:
E: sun-java6-doc: subprocess post-installation script killed by signal (Interrupt)

and during the update this is what popps:

```
Preconfiguring packages ...
(Reading database ... 190127 files and directories currently installed.)
Preparing to replace sun-java6-jre 6-06-0ubuntu1 (using .../sun-java6-jre_6-06-0ubuntu1_all.deb) ...
sun-dlj-v1-1 license has already been accepted
Unpacking replacement sun-java6-jre ...
Setting up sun-java6-doc (6-06-0ubuntu1) ...
This package is an installer package, it does not actually contain the
JDK documentation.  You will need to go download one of the
archives:

    jdk-6-doc.zip jdk-6-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    http://java.sun.com/javase/downloads/

now and download.  The file should be owned by root.root and be copied
to /tmp.

[Press RETURN to try again, 'no' + RETURN to abort] ^Xdpkg: error processing sun-java6-doc (--configure):
 subprocess post-installation script killed by signal (Interrupt)
Setting up sun-java6-jre (6-06-0ubuntu1) ...

Errors were encountered while processing:
 sun-java6-doc
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up sun-java6-doc (6-06-0ubuntu1) ...
This package is an installer package, it does not actually contain the
JDK documentation.  You will need to go download one of the
archives:

    jdk-6-doc.zip jdk-6-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    http://java.sun.com/javase/downloads/

now and download.  The file should be owned by root.root and be copied
to /tmp.

[Press RETURN to try again, 'no' + RETURN to abort] no
Abort installation of JDK documentation
dpkg: error processing sun-java6-doc (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 sun-java6-doc
```

any Idea's? realy need java to work on my computer...
and if you are going to tell me to download and install jdk-6-doc.zip jdk-6-doc-ja.zip tell me exactly where to DL it and how to install please.

---

### Post by paulo.monk on 2008-07-11
You should try to select your jre version by typing

<CODE>
sudo update-alternatives --config java
</CODE>

You can either check if there's some links to the java commands (java, javaw, javac) and to the jvm in your /usr/bin directory.

If you want to set the JAVA_HOME variable, you can edit the /etc/environment or /home/USERNAME/.profile and add the following line:

<CODE>
export JAVA_HOME="[PATH_TO_JAVA]"
</CODE>

Otherwise, you should reinstall your jre by typing in terminal:

<CODE>
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
</CODE>

---

### Post by paulo.monk on 2008-07-11
Sorry for the bad formatting of my reply.
Its one of the first times I post on this forum.

---

### Post by Oddgeir on 2008-07-11
First command give me:
```
There is only 1 program which provides java
(/usr/lib/jvm/java-6-sun/jre/bin/java). Nothing to configure.
```
 so i guess that's okey then.

sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin say this:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
sun-java6-jre is already the newest version.
Package sun-java6-plugin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-java6-plugin has no installation candidate

```

Witch is the firefox plugin who do not work or exist i guess and fro what i hear the ice-tea plugin don't work with home banking and stuff
any idea on how to get the sun java plugin installed?

---

### Post by jamesstansell on 2008-07-11
The message you see about no installation candidate for sun-java6-plugin sounds like you run a 64-bit system.  Is that right?

There is no 64-bit Java plugin from Sun.  You could try the icedtead-gcjwebplugin package, but you are correct that a lot of the banking applets don't work with it.  I'd recommend taking a look in the 64-bit users forum, especially at the sticky.  You might also try using Konquerer instead of Firefox.

Of course if you're not running a 64-bit system then there's something else to figure out.

Also, if you're still getting error messages about the sun-java6-doc package then just delete or purge it.  It's not a normal package and you very likely don't care about it anyway.

---

