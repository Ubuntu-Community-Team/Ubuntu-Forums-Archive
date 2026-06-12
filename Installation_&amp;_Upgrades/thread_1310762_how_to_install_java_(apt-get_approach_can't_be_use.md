---
title: "how to install java (apt-get approach can't be used)"
date: 2009-11-02
forum: Installation &amp; Upgrades
---

### Post by alfonz19 on 2009-11-02
Hi,

I've recently installed kubuntu 9.04 and xubuntu 9.10 on two different computers, both sharing same behavior. Unability to install java.

I need to install more versions then just the current one (and 1.5.* version is not in 9.10 repositories) AND I would like to install enterprise edition pack (never were in repositories).

So I have to download .bin file from java.sun.com. But it cannot be installed on either system because when executed with root privileges (needed to install into /usr/ instead of home directory) the binary crashes. When run as a normal user everything is ok. (on 9.10 I've to download required libstdc++5 from manually downloaded .deb since it's not present in repositories anymore).

Why's that happening?
thanks in advance.

---

### Post by bogdan.veringioiu on 2009-11-02
Hi.
Can you paste the error details when the install crashes?
Cheers.
Bogdan

---

### Post by alfonz19 on 2009-11-02
of course. After printing this execution hangs ups and has to be killed ( -9).

```

Checking available disk space...                       
Checking Java(TM) 2 Runtime Environment...                                 
Extracting Java(TM) 2 Runtime Environment files...                         
glibc detected *** ./java_app_platform_sdk-5_07-jdk-6u16-linux.bin: double free or corruption (!prev): 0x087e1e40 ***                                                                                                                            
======= Backtrace: =========                                                                                                            
/home/martin/../../lib/tls/i686/cmov/libc.so.6[0xb7d84604]                                                                              
/home/martin/../../lib/tls/i686/cmov/libc.so.6(cfree+0x96)[0xb7d865b6]                                                                  
./java_app_platform_sdk-5_07-jdk-6u16-linux.bin(GetPublicJREPath+0x6df)[0x8054269]                                                      
./java_app_platform_sdk-5_07-jdk-6u16-linux.bin(main+0x8f8)[0x804e37c]                                                                  
/home/martin/../../lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5)[0xb7d2b775]                                                      
./java_app_platform_sdk-5_07-jdk-6u16-linux.bin(dlopen+0x41)[0x804c9f5]                                                                 
======= Memory map: ========                                                                                                            
08048000-08061000 r-xp 00000000 08:03 2880108    /home/martin/java_app_platform_sdk-5_07-jdk-6u16-linux.bin                             
08061000-08063000 rw-p 00018000 08:03 2880108    /home/martin/java_app_platform_sdk-5_07-jdk-6u16-linux.bin                             
087d2000-08804000 rw-p 087d2000 00:00 0          [heap]                                                                                 
4271b000-42728000 r-xp 00000000 08:03 100887319  /lib/libgcc_s.so.1                                                                     
42728000-42729000 r--p 0000c000 08:03 100887319  /lib/libgcc_s.so.1                                                                     
42729000-4272a000 rw-p 0000d000 08:03 100887319  /lib/libgcc_s.so.1                                                                     
b7b00000-b7b21000 rw-p b7b00000 00:00 0                                                                                                 
b7b21000-b7c00000 ---p b7b21000 00:00 0                                                                                                 
b7cb9000-b7cf8000 r--p 00000000 08:03 101971496  /usr/lib/locale/cs_CZ.utf8/LC_CTYPE                                                    
b7cf8000-b7d14000 r--p 00000000 08:03 35367879   /usr/lib/locale/cs_CZ.utf8/LC_COLLATE                                                  
b7d14000-b7d15000 rw-p b7d14000 00:00 0                                                                                                 
b7d15000-b7e71000 r-xp 00000000 08:03 33717582   /lib/tls/i686/cmov/libc-2.9.so                                                         
b7e71000-b7e72000 ---p 0015c000 08:03 33717582   /lib/tls/i686/cmov/libc-2.9.so                                                         
b7e72000-b7e74000 r--p 0015c000 08:03 33717582   /lib/tls/i686/cmov/libc-2.9.so                                                         
b7e74000-b7e75000 rw-p 0015e000 08:03 33717582   /lib/tls/i686/cmov/libc-2.9.so                                                         
b7e75000-b7e79000 rw-p b7e75000 00:00 0                                                                                                 
b7e79000-b7e9d000 r-xp 00000000 08:03 33717586   /lib/tls/i686/cmov/libm-2.9.so                                                         
b7e9d000-b7e9e000 r--p 00023000 08:03 33717586   /lib/tls/i686/cmov/libm-2.9.so                                                         
b7e9e000-b7e9f000 rw-p 00024000 08:03 33717586   /lib/tls/i686/cmov/libm-2.9.so                                                         
b7e9f000-b7f4f000 r-xp 00000000 08:03 101151541  /usr/lib/libstdc++.so.5.0.7                                                            
b7f4f000-b7f54000 rw-p 000af000 08:03 101151541  /usr/lib/libstdc++.so.5.0.7                                                            
b7f54000-b7f59000 rw-p b7f54000 00:00 0
b7f5a000-b7f5b000 rw-p b7f5a000 00:00 0
b7f5b000-b7f5c000 r--p 00000000 08:03 35367877   /usr/lib/locale/cs_CZ.utf8/LC_NUMERIC
b7f5c000-b7f5d000 r--p 00000000 08:03 35367878   /usr/lib/locale/cs_CZ.utf8/LC_TIME
b7f5d000-b7f5e000 r--p 00000000 08:03 35367880   /usr/lib/locale/cs_CZ.utf8/LC_MONETARY
b7f5e000-b7f5f000 r--p 00000000 08:03 68828971   /usr/lib/locale/cs_CZ.utf8/LC_MESSAGES/SYS_LC_MESSAGES
b7f5f000-b7f60000 r--p 00000000 08:03 101971502  /usr/lib/locale/cs_CZ.utf8/LC_PAPER
b7f60000-b7f61000 r--p 00000000 08:03 35367881   /usr/lib/locale/cs_CZ.utf8/LC_NAME
b7f61000-b7f62000 r--p 00000000 08:03 35367882   /usr/lib/locale/cs_CZ.utf8/LC_ADDRESS
b7f62000-b7f63000 r--p 00000000 08:03 35367883   /usr/lib/locale/cs_CZ.utf8/LC_TELEPHONE
b7f63000-b7f64000 r--p 00000000 08:03 101971498  /usr/lib/locale/cs_CZ.utf8/LC_MEASUREMENT
b7f64000-b7f6b000 r--s 00000000 08:03 33717578   /usr/lib/gconv/gconv-modules.cache
b7f6b000-b7f6c000 r--p 00000000 08:03 35367884   /usr/lib/locale/cs_CZ.utf8/LC_IDENTIFICATION
b7f6c000-b7f7e000 r-xp 00000000 08:03 33717597   /lib/tls/i686/cmov/libresolv-2.9.so
b7f7e000-b7f7f000 r--p 00011000 08:03 33717597   /lib/tls/i686/cmov/libresolv-2.9.so
b7f7f000-b7f80000 rw-p 00012000 08:03 33717597   /lib/tls/i686/cmov/libresolv-2.9.so
b7f80000-b7f82000 rw-p b7f80000 00:00 0
b7f82000-b7f8b000 r-xp 00000000 08:03 33717584   /lib/tls/i686/cmov/libcrypt-2.9.so
b7f8b000-b7f8c000 r--p 00008000 08:03 33717584   /lib/tls/i686/cmov/libcrypt-2.9.so
b7f8c000-b7f8d000 rw-p 00009000 08:03 33717584   /lib/tls/i686/cmov/libcrypt-2.9.so
b7f8d000-b7fb5000 rw-p b7f8d000 00:00 0
b7fb5000-b7fb7000 r-xp 00000000 08:03 33717585   /lib/tls/i686/cmov/libdl-2.9.so
b7fb7000-b7fb8000 r--p 00001000 08:03 33717585   /lib/tls/i686/cmov/libdl-2.9.so
b7fb8000-b7fb9000 rw-p 00002000 08:03 33717585   /lib/tls/i686/cmov/libdl-2.9.so
b7fb9000-b7fce000 r-xp 00000000 08:03 33717596   /lib/tls/i686/cmov/libpthread-2.9.so
b7fce000-b7fcf000 r--p 00014000 08:03 33717596   /lib/tls/i686/cmov/libpthread-2.9.so
b7fcf000-b7fd0000 rw-p 00015000 08:03 33717596   /lib/tls/i686/cmov/libpthread-2.9.so
b7fd0000-b7fd4000 rw-p b7fd0000 00:00 0
b7fd4000-b7fd5000 r-xp b7fd4000 00:00 0          [vdso]
b7fd5000-b7ff1000 r-xp 00000000 08:03 100843760  /lib/ld-2.9.so
b7ff1000-b7ff2000 r--p 0001b000 08:03 100843760  /lib/ld-2.9.so
b7ff2000-b7ff3000 rw-p 0001c000 08:03 100843760  /lib/ld-2.9.so
bfcde000-bfcf3000 rw-p bffeb000 00:00 0          [stack]
Deleting temporary files...
```

---

### Post by bogdan.veringioiu on 2009-11-02
Hi.
Take a look at this link:
[http://forums.sun.com/thread.jspa?threadID=5256679](http://forums.sun.com/thread.jspa?threadID=5256679)

They suggest to do a:
```
export MALLOC_CHECK_=0
```
then run the installer.

Cheers.
Bogdan

---

### Post by alfonz19 on 2009-11-02
ok, I do not know why the error is occuring and will be glad if someone could explain it to me.

if I try to do
```
sudo -i
export MALLOC_CHECK_=0
```
and then run the binary, then it will not fail like before, but instead of it following error is print out
```
Exception in thread "Thread-1" java.lang.NoClassDefFoundError: Could not initialize class sun.awt.X11GraphicsEnvironment
```
which I believe is caused by executing it from root console (but I may be wrong).

So what's the correct way to enforce MALLOC_CHECK=0 before running that binary as a root without using root -i ?

---

### Post by bogdan.veringioiu on 2009-11-02
Hi.
You could try this:
```
xhost +
sudo -i
export DISPLAY=:0.0
export MALLOC_CHECK_=0
./runInstaller...
```

Let me known.
Bogdan

---

### Post by Mighty_Joe on 2009-11-02
> **alfonz19 said:**
>  I would like to install enterprise edition pack (never were in repositories).


You don't need the Java Enterprise Edition unless you are developing J2EE applications, and if you are developing J2EE apps, you should probably be using a J2EE server like [Glassfish]("https://glassfish.dev.java.net/") or [JBoss]("https://glassfish.dev.java.net/"), which *are *in the repository.

---

### Post by alfonz19 on 2009-11-02
Is it? Ok, my bad. 

Nevertheless this not solve the problem, since jdk 4 and 5 cannot be found (again in default repositories) any more (for 9.10 version). Or are there just not available yet, but they will be?

---

### Post by alfonz19 on 2009-11-02
Hi, 

my answer from 12:55 PM about MALLOC I've actually posted before readingt post of bogdan.veringioiu, where he posted link from sun.

I've finally found enough time to read it to the end and there was hint which actually helped me - to supply parameter "javahome" pointing to some existing jre installation  directory.

Since I'm currently trying it from pc where I have java installed in user space (since I have to start working NOW and cannot play with this error), I've run that binary this way

```
sudo ./java_app_platform_sdk-5_07-jdk-6u16-linux.bin -javahome /home/martin/java_SDK/jdk/jre
```

and installation program started & finished without a problem.
---

so, thank you all guys very much for helping hints with java installation and for notice about existing JBoss, glassfish etc etc packages.

---

### Post by duleep on 2009-11-02
i used 9.04 plz help to this problem  

> 
duleep@duleep-desktop:~$ sudo apt-get install sun-java6-jdk
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
duleep@duleep-desktop:~$ 

---

### Post by alfonz19 on 2009-11-03
i do not know in what circumstances you ran that command, but it looks like you've got synaptic or another package manager running while trying to run this command.

---

### Post by duleep on 2009-11-04
ya i forgot close Synaptic when installing ,

after i close
now give this message

> duleep@duleep-desktop:~$ sudo apt-get install sun-java6-jdk
[sudo] password for duleep: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  sun-java6-jdk: Depends: sun-java6-bin (= 6-06-0ubuntu1) but it is not going to be installed
E: Broken packages
duleep@duleep-desktop:~$

[IMG]http://ubuntuforums.org/images/icons/icon9.gif[/IMG]
now what i do next

---

### Post by alfonz19 on 2009-11-04
try to run same command with "-f" switch

---

### Post by duleep on 2009-11-04
i think you saying

> duleep@duleep-desktop:~$ sudo apt-get -f install sun-java6-jdk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  sun-java6-jdk: Depends: sun-java6-bin (= 6-06-0ubuntu1) but it is not going to be installed
E: Broken packages
duleep@duleep-desktop:~$ 


but still problem

---

### Post by alfonz19 on 2009-11-04
sorry, I'm not wise enought to help you actually without being present at your computer. I know what's wrong, but I hate solving this, since it's always unclear what will help and what will not. You can try remove that broken package and install it again, clean cache of packages and try it again etc. (I think it depends how that package gets broken).

For example here is some advices
[http://fixunix.com/ubuntu/521352-help-trying-fix-broken-packages.html](http://fixunix.com/ubuntu/521352-help-trying-fix-broken-packages.html)
good luck.

---

### Post by duleep on 2009-11-05
i found the solution 

1. download jdk bin file in my home
2.> chmod +x jdk1.6.0_13
3..> /jdk1.6.0_13
4.> export JAVA_HOME='/home/duleep/jdk1.6.0_13'
PATH=.:$JAVA_HOME/bin:$JAVA_HOME/jre/bin:$PATH

this told by one of my collage friend

---

### Post by alfonz19 on 2009-11-05
yes, this can be a way. But probably not THE way.

The sole problem is that you still did not get rid of broken package and bypassed packaging system to manage your java installation. But if you don't mind, then it's not a problem. Your java installation will work this way (actually I've installed my java enterprise edition exactly in this way).

---

### Post by doas777 on 2009-11-05
the first thing I do after encountering any apt error (well most anyway) is 
```
sudo apt-get update && sudo apt-get upgrade
``` to refresh the repo list and get any pending updates installed before trying again. usually works.

---

