---
title: "JDK instalation"
date: 2008-08-03
forum: General Help
---

### Post by fenT1 on 2008-08-03
I downloaded the JDK and Netbeans bundle on my Hardy desktop but i can extract it due to the following error. Help will be appreciated since i need it for school and i start on august 18.

Could not open "jdk-6u7-nb-6_1-linux-ml.sh"

Archive type not supported.

---

### Post by zvacet on 2008-08-03
[Here]("http://monkeyblog.org/ubuntu/installing/")

---

### Post by Diabolis on 2008-08-03
Yeah, read the link above.

.sh means that is a shell script. You don't extract them, you execute them.
```
./*"script name"*
```

Make sure to make it executable:
```
chmod +x *"script name"*
```

---

### Post by fenT1 on 2008-08-04
> **Diabolis said:**
> Yeah, read the link above.

.sh means that is a shell script. You don't extract them, you execute them.
```
./*"script name"*
```

Make sure to make it executable:
```
chmod +x *"script name"*
```

ok so i did the commands and i got this output:
Configuring the installer...
Searching for JVM on the system...
Preparing bundled JVM ...
Extracting installation data...
Running the installer wizard...
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7637767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb76378b1]
#2 /usr/lib/libX11.so.6(_XReply+0xfd) [0x9772f1bd]
#3 /tmp/.nbi-1084009.tmp/_jvm/lib/i386/xawt/libmawt.so [0x9e460dce]
#4 /tmp/.nbi-1084009.tmp/_jvm/lib/i386/xawt/libmawt.so [0x9e44ad77]
#5 /tmp/.nbi-1084009.tmp/_jvm/lib/i386/xawt/libmawt.so [0x9e44aef3]
#6 /tmp/.nbi-1084009.tmp/_jvm/lib/i386/xawt/libmawt.so(Java_sun_awt_X11GraphicsEnvironment_initDisplay+0x26) [0x9e44b136]
#7 [0xb2a4bc1b]
#8 [0xb2a45b3b]
#9 [0xb2a45b3b]
#10 [0xb2a43219]
#11 /tmp/.nbi-1084009.tmp/_jvm/lib/i386/client/libjvm.so [0xb77e12bc]
#12 /tmp/.nbi-1084009.tmp/_jvm/lib/i386/client/libjvm.so [0xb78f5ed8]
#13 /tmp/.nbi-1084009.tmp/_jvm/lib/i386/client/libjvm.so [0xb77e10ef]
#14 /tmp/.nbi-1084009.tmp/_jvm/lib/i386/client/libjvm.so(JVM_DoPrivileged+0x32d) [0xb783eb9d]
#15 /tmp/.nbi-1084009.tmp/_jvm/lib/i386/libjava.so(Java_java_security_AccessController_doPrivileged__Ljava_security_PrivilegedAction_2+0x3d) [0xb75d730d]
#16 [0xb2a4b4bb]
#17 [0xb2a45a64]
#18 [0xb2a43219]
#19 /tmp/.nbi-1084009.tmp/_jvm/lib/i386/client/libjvm.so [0xb77e12bc]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7637767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb763781e]
#2 /usr/lib/libX11.so.6 [0x9772e518]
#3 /usr/lib/libX11.so.6(XGetVisualInfo+0x26) [0x977250a6]
#4 /tmp/.nbi-1084009.tmp/_jvm/lib/i386/xawt/libmawt.so [0x9e44a0b9]
#5 /tmp/.nbi-1084009.tmp/_jvm/lib/i386/xawt/libmawt.so [0x9e44a303]
#6 /tmp/.nbi-1084009.tmp/_jvm/lib/i386/xawt/libmawt.so [0x9e44afa1]
#7 /tmp/.nbi-1084009.tmp/_jvm/lib/i386/xawt/libmawt.so(Java_sun_awt_X11GraphicsEnvironment_initDisplay+0x26) [0x9e44b136]
#8 [0xb2a4bc1b]
#9 [0xb2a45b3b]
#10 [0xb2a45b3b]
#11 [0xb2a43219]
#12 /tmp/.nbi-1084009.tmp/_jvm/lib/i386/client/libjvm.so [0xb77e12bc]
#13 /tmp/.nbi-1084009.tmp/_jvm/lib/i386/client/libjvm.so [0xb78f5ed8]
#14 /tmp/.nbi-1084009.tmp/_jvm/lib/i386/client/libjvm.so [0xb77e10ef]
#15 /tmp/.nbi-1084009.tmp/_jvm/lib/i386/client/libjvm.so(JVM_DoPrivileged+0x32d) [0xb783eb9d]
#16 /tmp/.nbi-1084009.tmp/_jvm/lib/i386/libjava.so(Java_java_security_AccessController_doPrivileged__Ljava_security_PrivilegedAction_2+0x3d) [0xb75d730d]
#17 [0xb2a4b4bb]
#18 [0xb2a45a64]
#19 [0xb2a43219]
/usr/share/themes/Clearlooks/gtk-2.0/gtkrc:41: error: lexical error or unexpected token, expected valid token

---

### Post by Diabolis on 2008-08-05
I tried to google the error message and seems like its not very common.

Does this help: [http://dmartin.org/content/running-java-web-start-apps-ubuntu-linux-amd-64](http://dmartin.org/content/running-java-web-start-apps-ubuntu-linux-amd-64) ?

---

### Post by tinny on 2008-08-05
Why dont you just install the Sun JDK from the repositories?

Enable the "universe" and "multiverse" repositories.

[https://help.ubuntu.com/8.04/add-applications/C/extra-repositories-adding.html](https://help.ubuntu.com/8.04/add-applications/C/extra-repositories-adding.html)

then...
```

sudo apt-get update
sudo apt-get install sun-java6*

```

Sun Java 6 runtime and JDK, Done.

---

### Post by fenT1 on 2008-08-06
> **tinny said:**
> Why dont you just install the Sun JDK from the repositories?

Enable the "universe" and "multiverse" repositories.

[https://help.ubuntu.com/8.04/add-applications/C/extra-repositories-adding.html](https://help.ubuntu.com/8.04/add-applications/C/extra-repositories-adding.html)

then...
```

sudo apt-get update
sudo apt-get install sun-java6*

```

Sun Java 6 runtime and JDK, Done.

The folowing error ocurred. And how do i acces repositories?

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  sun-java5-fonts: Conflicts: ttf-lucida
  sun-java6-fonts: Conflicts: ttf-lucida
E: Broken packages

---

### Post by tinny on 2008-08-06
I think this will fix your problem.

Remove and clean the Java install.

```

sudo apt-get remove --purge sun-java6*

``` 

Remove conflicting ttf fonts (Did you install these fonts at some stage?)

```

sudo apt-get remove --purge ttf-lucida

```

Reinstall Sun JDK

```

sudo apt-get clean
sudo apt-get update
sudo apt-get install sun-java6*

```

---

### Post by fenT1 on 2008-08-07
> **tinny said:**
> I think this will fix your problem.

Remove and clean the Java install.

```

sudo apt-get remove --purge sun-java6*

``` 

Remove conflicting ttf fonts (Did you install these fonts at some stage?)

```

sudo apt-get remove --purge ttf-lucida

```

Reinstall Sun JDK


```

sudo apt-get clean
sudo apt-get update
sudo apt-get install sun-java6*

```


Thanks for your replies i havent had a chance to try it but ill get it going today when i get out of work.

---

### Post by fenT1 on 2008-08-08
> **tinny said:**
> I think this will fix your problem.

Remove and clean the Java install.

```

sudo apt-get remove --purge sun-java6*

``` 

Remove conflicting ttf fonts (Did you install these fonts at some stage?)

```

sudo apt-get remove --purge ttf-lucida

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package ttf-lucida is not installed, so not removed
The following packages were automatically installed and are no longer required:
  java-common unixodbc odbcinst1debian1
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 30 not upgraded.


Reinstall Sun JDK

```

sudo apt-get clean
sudo apt-get update
sudo apt-get install sun-java6*

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting sun-java5-bin for regex 'sun-java6*'
Note, selecting sun-java5-doc for regex 'sun-java6*'
Note, selecting ia32-sun-java5-bin for regex 'sun-java6*'
Note, selecting ia32-sun-java5-plugin for regex 'sun-java6*'
Note, selecting sun-javadb-common for regex 'sun-java6*'
Note, selecting sun-java6-plugin for regex 'sun-java6*'
Note, selecting sun-java6-demo for regex 'sun-java6*'
Note, selecting sun-java5-jdk for regex 'sun-java6*'
Note, selecting sun-java5-jre for regex 'sun-java6*'
Note, selecting sun-javadb-doc for regex 'sun-java6*'
Note, selecting sun-java5-src for regex 'sun-java6*'
Note, selecting sun-java6-fonts for regex 'sun-java6*'
Note, selecting sun-java5-source for regex 'sun-java6*'
Note, selecting sun-java6-bin for regex 'sun-java6*'
Note, selecting ia32-sun-java6-plugin for regex 'sun-java6*'
Note, selecting sun-java6-doc for regex 'sun-java6*'
Note, selecting ia32-sun-java6-bin for regex 'sun-java6*'
Note, selecting sun-java6-jdk for regex 'sun-java6*'
Note, selecting sun-javadb-demo for regex 'sun-java6*'
Note, selecting sun-java6-jre for regex 'sun-java6*'
Note, selecting sun-javadb-core for regex 'sun-java6*'
Note, selecting sun-java6-src for regex 'sun-java6*'
Note, selecting sun-java6-source for regex 'sun-java6*'
Note, selecting sun-java5-demo for regex 'sun-java6*'
Note, selecting sun-javadb-javadoc for regex 'sun-java6*'
Note, selecting sun-java5-fonts for regex 'sun-java6*'
Note, selecting sun-java5-plugin for regex 'sun-java6*'
Note, selecting sun-java6-javadb for regex 'sun-java6*'
Note, selecting sun-javadb-client for regex 'sun-java6*'
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  sun-java5-fonts: Conflicts: ttf-lucida
  sun-java6-fonts: Conflicts: ttf-lucida
E: Broken packages

Really weird...

---

### Post by tinny on 2008-09-02
You will need to force the package install and then you may need to force the reinstall of ttf-lucida.

```

sudo apt-get update
sudo apt-get install sun-java6* --force-yes

```

---

