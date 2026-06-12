---
title: "Frost Wire Doesnt STarts!"
date: 2008-10-18
forum: General Help
---

### Post by gtmario on 2008-10-18
[FONT="Comic Sans MS"][COLOR="YellowGreen"]I installed [COLOR="Cyan"]frostwire[/COLOR] and the latest version of java....LIMEWIRE runs well but frostwire doesnt.[/COLOR][/FONT]
:confused:
Thats what i got:
```


Starting FrostWire...
Java exec found in PATH. Verifying...
OOPS, you don't seem to have a valid JRE. FrostWire works best with Sun JRE available at http://www.java.com
OOPS, unable to locate java exec in  /usr/lib/  hierarchy
You need to upgrade to JRE 1.5.x or newer from http://www.java.com
ls: cannot access /usr/java/j*: No such file or directory
OOPS, unable to locate java exec in  /usr/java/  hierarchy
You need to upgrade to JRE 1.5.x or newer from http://www.java.com
ls: cannot access /opt/j*: No such file or directory
OOPS, unable to locate java exec in  /opt/  hierarchy
You need to upgrade to JRE 1.5.x or newer from http://www.java.com
mario@mario-laptop:~/Desktop$ sudo frostwire
HOSTNAME IS mario-laptop
Starting FrostWire...
Java exec found in PATH. Verifying...
OOPS, you don't seem to have a valid JRE. FrostWire works best with Sun JRE available at http://www.java.com
OOPS, unable to locate java exec in  /usr/lib/  hierarchy
You need to upgrade to JRE 1.5.x or newer from http://www.java.com
ls: cannot access /usr/java/j*: No such file or directory
OOPS, unable to locate java exec in  /usr/java/  hierarchy
You need to upgrade to JRE 1.5.x or newer from http://www.java.com
ls: cannot access /opt/j*: No such file or directory
OOPS, unable to locate java exec in  /opt/  hierarchy
You need to upgrade to JRE 1.5.x or newer from http://www.java.com




```

---

### Post by shawnrgr on 2008-10-19
```
apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
```
```
sudo update-alternatives --config java
```

---

### Post by greenkernel on 2008-10-19
I've already downloaded frostwire 4.17 and installed it. But, there is an error message whenever I try to open it.
 > An unexpected error has been detected by Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x062ee7dd, pid=8409, tid=3048815504
#
# Java VM: Java HotSpot(TM) Client VM (10.0-b23 mixed mode, sharing linux-x86)
# Problematic frame:
# V  [libjvm.so+0x2ee7dd]
#
# An error report file with more information is saved as:
# /usr/lib/frostwire/hs_err_pid8409.log
#
# If you would like to submit a bug report, please visit:
#   [http://java.sun.com/webapps/bugreport/crash.jsp](http://java.sun.com/webapps/bugreport/crash.jsp)
#
/usr/lib/frostwire/runFrostwire.sh: line 140:  8409 Aborted                 ${JAVA_PROGRAM_DIR}java -ea -Dorg.apache.commons.logging.Log=org.apache.commons.logging.impl.NoOpLog -Djava.library.path=. $EXECUTABLE -jar FrostWire.jar $ARGUMENTS


******************************************************************
Something went wrong with FrostWire.
Maybe you're using the wrong version of Java?
(FrostWire is tested against and works best with with Sun's JRE, Java 1.4+)
The version of Java in your PATH is:
java version "1.6.0_07"
Java(TM) SE Runtime Environment (build 1.6.0_07-b06)
Java HotSpot(TM) Client VM (build 10.0-b23, mixed mode, sharing)

Please help me !!

---

### Post by shawnrgr on 2008-10-19
whats the output of.. 
```
update-alternatives --list java
```

---

### Post by wardrich on 2008-10-22
Thanks shawnrgr.

I was also having an issue with Frostwire (it was just coming up as an empty window).  All I had to do was grab those java packages... I guess I grabbed the wrong ones last night.  It's workin' like a charm now.  :D  You rock.  lol

---

### Post by shawnrgr on 2008-10-22
No problem!

---

