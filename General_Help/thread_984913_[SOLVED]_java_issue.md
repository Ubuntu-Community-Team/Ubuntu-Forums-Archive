---
title: "[SOLVED] java issue"
date: 2008-11-17
forum: General Help
---

### Post by porchrat on 2008-11-17
Hi all

trying to install netbeans and I'm having a little trouble.  No matter what jre I'm running all I get is a blank frame when I run the .sh installer.

Any idea how to solve this?  Otherwise I'll need to get the netbeans off the repositories and I really don't need the ruby, php etc. functionality and don't want to waste bandwidth downloading it.

---

### Post by reality1011 on 2008-11-17
I have always downloaded it directly from Sun... never had any problems.

---

### Post by porchrat on 2008-11-17
> **reality1011 said:**
> I have always downloaded it directly from Sun... never had any problems.

I grabbed the SE from sun.  I've looked into it and basically when I attempt to run the installer (a .sh file) i get this:

```
Configuring the installer...
Searching for JVM on the system...
Extracting installation data...
Running the installer wizard...
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0x7fd08f25797c]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x24) [0x7fd08f257a84]
#2 /usr/lib/libX11.so.6(_XReply+0x10f) [0x7fd08f6a1f4f]
#3 /usr/lib/jvm/java-1.5.0-sun-1.5.0.15/jre/lib/amd64/xawt/libmawt.so [0x7fd08fb97d7b]
#4 /usr/lib/jvm/java-1.5.0-sun-1.5.0.15/jre/lib/amd64/xawt/libmawt.so [0x7fd08fb84e9c]
#5 /usr/lib/jvm/java-1.5.0-sun-1.5.0.15/jre/lib/amd64/xawt/libmawt.so [0x7fd08fb84ffe]
#6 /usr/lib/jvm/java-1.5.0-sun-1.5.0.15/jre/lib/amd64/xawt/libmawt.so(Java_sun_awt_X11GraphicsEnvironment_initDisplay+0x9) [0x7fd08fb851c9]
#7 [0x7fd0abb0af7b]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0x7fd08f25797c]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x15) [0x7fd08f257a15]
#2 /usr/lib/libX11.so.6 [0x7fd08f6a1323]
#3 /usr/lib/libX11.so.6(XGetVisualInfo+0x2c) [0x7fd08f69872c]
#4 /usr/lib/jvm/java-1.5.0-sun-1.5.0.15/jre/lib/amd64/xawt/libmawt.so [0x7fd08fb841f7]
#5 /usr/lib/jvm/java-1.5.0-sun-1.5.0.15/jre/lib/amd64/xawt/libmawt.so [0x7fd08fb84431]
#6 /usr/lib/jvm/java-1.5.0-sun-1.5.0.15/jre/lib/amd64/xawt/libmawt.so [0x7fd08fb85099]
#7 /usr/lib/jvm/java-1.5.0-sun-1.5.0.15/jre/lib/amd64/xawt/libmawt.so(Java_sun_awt_X11GraphicsEnvironment_initDisplay+0x9) [0x7fd08fb851c9]
#8 [0x7fd0abb0af7b]
```

Seems to be a problem with the libraries.  Looks like it is trying to use 1.5 instead of 1.6, both of which are installed, however 1.6 is active.  I would remove 1.5, but I like to keep it around for a few older programs I have that dislike 1.6 for some reason.

I have read up on it and a few people have recommended using sed to replace a line in the library libxcb-xlib to stop it checking which jre version you're running, but that seems a little dangerous to me, although it does seem to solve their problems.

However their problems are not identical to mine, their java programs fail to start entirely, mine loads a frame, but fails to display anything in the frame.

EDIT:  Which version of Ubuntu are you running?

---

### Post by porchrat on 2008-11-18
bump

---

### Post by reality1011 on 2008-11-19
I am running 7.10

```

cappetta@Linux-Box:/etc/apache2$ lsb_release -dc
Description:    Ubuntu 7.10
Codename:       gutsy
cappetta@Linux-Box:/etc/apache2$


cappetta@Linux-Box:/etc/apache2$ java -version
\java version "1.5.0_14"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_14-b03)
Java HotSpot(TM) Client VM (build 1.5.0_14-b03, mixed mode, sharing)

cappetta@Linux-Box:/etc/apache2$ javac -version
javac 1.5.0_14

```


I am going to try to get 1.6 now...

---

### Post by reality1011 on 2008-11-19
ok so I just installed the most recent java by doing the following:

1.  Download the bin file ( not the rpm.bin) from here:[DOWNLOAD FROM SUN]("http://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_Developer-Site/en_US/-/USD/VerifyItem-Start/jdk-6u10-linux-i586.bin?BundledLineItemUUID=kDtIBe.pnFAAAAEda_pSvLfj&OrderID=NylIBe.pObIAAAEdVPpSvLfj&ProductID=7GBIBe.pq0AAAAEb4aMQVbLE&FileName=/jdk-6u10-linux-i586.bin")

2. chmod 755 and move this file into the top level directory where java is installed... in my case it is in /usr/local/

```

cappetta@Linux-Box:~/internet-downloads$ which java
/usr/bin//java
cappetta@Linux-Box:~/internet-downloads$ ll /usr/bin/java
lrwxrwxrwx 1 root root 31 2008-02-16 19:59 /usr/bin/java -> /usr/local/jdk1.5.0_14/bin/java
cappetta@Linux-Box:~/internet-downloads$ 


```

3. execute 
```
sudo ./jdk-6u10-linux-i586.bin 
```

4. press space until you are required to type yes... then press enter... wait press enter again

5.  Remove the links and recreate them: 

```
cappetta@Linux-Box:/usr/local$ which java
/usr/bin//java
cappetta@Linux-Box:/usr/local$ ll /usr/bin/java
lrwxrwxrwx 1 root root 31 2008-02-16 19:59 /usr/bin/java -> /usr/local/jdk1.5.0_14/bin/java
cappetta@Linux-Box:/usr/local$ sudo rm /usr/bin/java
cappetta@Linux-Box:/usr/local$ sudo ln -s /usr/local/jdk1.6.0_10/bin/java /usr/bin/java
cappetta@Linux-Box:/usr/local$ ll /usr/bin/java
lrwxrwxrwx 1 root root 31 2008-11-19 22:25 /usr/bin/java -> /usr/local/jdk1.6.0_10/bin/java
cappetta@Linux-Box:/usr/local$ ll /usr/bin/javac
lrwxrwxrwx 1 root root 32 2008-02-16 19:59 /usr/bin/javac -> /usr/local/jdk1.5.0_14/bin/javac
cappetta@Linux-Box:/usr/local$ sudo rm /usr/bin/javac
cappetta@Linux-Box:/usr/local$ sudo ln -s /usr/local/jdk1.6.0_10/bin/javac /usr/bin/javac
cappetta@Linux-Box:/usr/local$ ll /usr/bin/javac
lrwxrwxrwx 1 root root 32 2008-11-19 22:25 /usr/bin/javac -> /usr/local/jdk1.6.0_10/bin/javac
cappetta@Linux-Box:/usr/local$ java -version
java version "1.6.0_10"
Java(TM) SE Runtime Environment (build 1.6.0_10-b33)
Java HotSpot(TM) Client VM (build 11.0-b15, mixed mode, sharing)
cappetta@Linux-Box:/usr/local$ javac -version
javac 1.6.0_10
cappetta@Linux-Box:/usr/local$ 

```

---

### Post by porchrat on 2008-11-20
Thanks reality1011 that seems very promising as it eliminates the whole need to run the java-based installer.  Can't see how that won't work.

I'll give it a go when I find the time (probably tomorrow).  Do you have any information on this particular problem?

I do experience problems like this quite frequently (where an empty frame opens up), however it normally requires me to re-execute whatever caused the error again and it opens a functional frame.

Anyway thanks again.  Anyone else with any more information please let me know.

---

### Post by reality1011 on 2008-11-20
Yea it shouldnt really cause any problems.  As for the other problem, Im not really sure... my guess is there is a problem with the installer getting information to the x11server... I say this because I see the following:

usr/lib/jvm/java-1.5.0-sun-1.5.0.15/jre/lib/amd64/xawt/libmawt.so(Java_sun_awt[COLOR="Red"]**_X11GraphicsEnvironment**_initDisplay[/COLOR]+0x9) [0x7fd08fb851c9]

---

### Post by porchrat on 2008-11-21
> **reality1011 said:**
> Yea it shouldnt really cause any problems.  As for the other problem, Im not really sure... my guess is there is a problem with the installer getting information to the x11server... I say this because I see the following:

usr/lib/jvm/java-1.5.0-sun-1.5.0.15/jre/lib/amd64/xawt/libmawt.so(Java_sun_awt[COLOR="Red"]**_X11GraphicsEnvironment**_initDisplay[/COLOR]+0x9) [0x7fd08fb851c9]

Well I mean it makes sense that the awt library would contain lines about communicating with the Xserver as awt is a graphics frontend. That doesn't look like an installer problem to me, it looks like the awt library itself is having a problem communicating with X.

I do experience this problem from time to time with other java apps so this isn't exactly an isolated incident, however this is the first time that simple restart doesn't fix the problem.  (because a simple restart was required I never bothered to check any exceptions, this could've been happening for a while with other apps and I haven't noticed)

EDIT:  Hang on a second I didn't read your earlier post properly there.  I don't need the new jdk I just need netbeans.  My 1.6 is running and compiling java and has been for months.  I have 1.6 and 1.5, perhaps 1.6 uses the 1.5 libraries...who knows.  I merely would like the IDE to make life a little easier.  Do you know of a way to download the netbeans binaries and build it seperately as opposed to using this java-based installer?

---

### Post by reality1011 on 2008-11-21
it does look like you need to relink the java libraries....  It looks like you have hava **[COLOR="Red"]1.5.0.15[/COLOR]**

> Before you install the IDE, the Java SE Development Kit (JDK) 5 Update 16 **[COLOR="Red"](version 1.5.0_16)[/COLOR]** or newer (including JDK 6 Update 7) must be installed on your system. If you do not have an installation of JDK 5 Update 16 or newer, you cannot proceed with the installation. For more information about the required JDK version, see the Required Software section in the NetBeans IDE 6.5 Release Notes. 


Yet I just installed Netbeans successfully using my 1.5.0.14 jre?




This is what I did... 

I downloaded netbeans 6.5 from [  Here  ]("http://services.netbeans.org/bouncer/index.php?product=netbeans-6.5&os=linux")

chmod 755 the /tmp/netbeans-6.5-ml-linux.sh file

sudo /tmp/netbeans-6.5-ml-linux.sh

It installed without any problems?

Now like I said I installed it with java 1.5.0.14 being used as my java / javac ... At one point it had asked me about what java libraries I wanted to use and they were pointing to the .14 package....

Did you do an integrity check?  Maybe the file downloaded corruptly?

ie:  Sun says the md5 checksum for this file is:
> NetBeans 6.5 Installer for Linux/English (en)
netbeans-6.5-ml-linux.sh (244.5 MB)
MD5: [COLOR="Red"]**29a55133ef3ba0383c08fef1f091fc28**[/COLOR]


I see my checksum is 
> 
cappetta@Linux-Box:/usr/local/netbeans-6.5/bin$ md5sum /tmp/netbeans-6.5-ml-linux.sh 
[COLOR="Red"]**29a55133ef3ba0383c08fef1f091fc28**[/COLOR]  /tmp/netbeans-6.5-ml-linux.sh


looks good on my end


Also what version ubuntu are you using?

---

### Post by porchrat on 2008-11-24
Checked my symlinks and they all seem fine:

```
ls -l /usr/bin/java
lrwxrwxrwx 1 root root 22 2008-07-14 15:33 java -> /etc/alternatives/java

ls -l /etc/alternatives/java
lrwxrwxrwx 1 root root 36 2008-11-21 17:10 java -> /usr/lib/jvm/java-6-sun/jre/bin/java

ls -l /usr/bin/javac
lrwxrwxrwx 1 root root 23 2008-07-14 15:33 javac -> /etc/alternatives/javac

ls -l /etc/alternatives/javac
lrwxrwxrwx 1 root root 33 2008-11-21 17:09 javac -> /usr/lib/jvm/java-6-sun/bin/javac
```

trimmed it down slightly to save some space, but they all seem fine and a version check shows:

```
java -version
java version "1.6.0_07"
Java(TM) SE Runtime Environment (build 1.6.0_07-b06)
Java HotSpot(TM) 64-Bit Server VM (build 10.0-b23, mixed mode)
```

```
javac -version
javac 1.6.0_07

```

---

### Post by reality1011 on 2008-11-24
So is there still a problem?

---

### Post by porchrat on 2008-11-25
Thought I'd come back and finish of this thread once and for all.  Seems like my initial download of netbeans was corrupted as I downloaded the 6.5 off Sun's website yesterday afternoon and it worked straight away.

Well at least it is working now, thanks very much for your help and advice it is much appreciated.

---

### Post by reality1011 on 2008-11-25
not a problem

---

