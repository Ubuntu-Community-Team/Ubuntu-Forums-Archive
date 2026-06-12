---
title: "JRE installation - Problem"
date: 2005-12-27
forum: Installation &amp; Upgrades
---

### Post by noeluylee on 2005-12-27
Hi, I have the JRE/ Java Web Start 1.5 on application>Internet I installed it thru apt-get, now I am trying to install a higher version of jre which I already downloaded it from [http://java.sun.com/j2se/1.5.0/download.jsp](http://java.sun.com/j2se/1.5.0/download.jsp). 

I follow the instruction from: [https://wiki.ubuntu.com/RestrictedFormats#head-68565ae07a003332e82c9f23706638777396c249](https://wiki.ubuntu.com/RestrictedFormats#head-68565ae07a003332e82c9f23706638777396c249)  

I am having a problem on:
fakeroot make-jpkg jre-1_5_0_06-linux-i586.bin
sudo dpkg -i sun-j2re1.5_1.5.0+update06_i386.deb

Here my terminal window:
noel@NOEL-Linux:~$ fakeroot make-jpkg jre-1_5_0_06-linux-i586.bin.bin
Creating temporary directory: /tmp/make-jpkg.XXXXTOrWIs
Loading plugins: blackdown-j2re.sh blackdown-j2sdk.sh common.sh ibm-j2re.sh ibm-j2sdk.sh j2re.sh j2sdk-doc.sh j2sdk.sh j2se.sh sun-j2re.sh sun-j2sdk-doc.sh sun-j2sdk.sh

No matching plugin was found.
Removing temporary directory: done
noel@NOEL-Linux:~$ sudo dpkg -i sun-j2re1.5_1.5.0+update06_i386.deb
dpkg: error processing sun-j2re1.5_1.5.0+update06_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 sun-j2re1.5_1.5.0+update06_i386.deb

Hope you can give me suggestions.

PS - I want to update this cause I am having a problem on running the eclipse.

---

### Post by Perfect Storm on 2005-12-27
Here's my solution:

```

sudo gedit /etc/apt/sources.list 

```

add:

## Penguin Liberation Front
deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free

```

sudo apt-get update
sudo apt-get install sun-j2re1.5

```

---

### Post by rickmans on 2005-12-27
You could use [Automatix]("http://ubuntuforums.org/showthread.php?t=80295")

---

### Post by noeluylee on 2005-12-27
hey guys, Thanks so much :) will try this out. :)

Noel

---

### Post by noeluylee on 2005-12-27
I was able to install the java 1.5.

java version "1.5.0_05"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_05-b05)
Java HotSpot(TM) Client VM (build 1.5.0_05-b05, mixed mode, sharing)

Can I remove the older version of java? which is 1.4. is it safe? and how to remove it?


Thanks.

---

### Post by Perfect Storm on 2005-12-27
There should be no problem.

```

sudo apt-get remove XXXXXXXX

```

XXXXXXX=the name

---

### Post by noeluylee on 2005-12-27
hmmmmm... what is the program name of java 1.4? :(  in my "sudo update-alternatives --config java" 

There are 4 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
      1        /usr/bin/gij-wrapper-4.0
      2        /usr/lib/jvm/java-gcj/bin/java
 +    3        /usr/lib/j2se/1.4/bin/java
*     4        /usr/lib/j2re1.5-sun/bin/java

I want to remove the j2se as my system is not using it anymore.. I will have to use the j2re1.5... 

after uninstalling this, it wont mess my system, right? :)

Thanks.

---

### Post by Perfect Storm on 2005-12-27
Not what I know of. But if it do. Please post it.

---

### Post by noigeaR on 2005-12-27
[QUOTE=noeluylee]hmmmmm... what is the program name of java 1.4? :(  in my "sudo update-alternatives --config java" 
[/QUOTE]

The pacakge name is j2sdk1.4
That's the Blackdown Java SDK. You can remove it in synaptic. I think it won't hurt your system as long as you have an alternative JRE installed.

By the way, if you want to do Java programming in eclipse you will have to install the sun-j2sdk, not the sun-j2re. The j2re is only for running Java programs, not for compiling them.

---

### Post by noeluylee on 2005-12-27
Thanks. do I have to donwload the sun-j2re or thats the Blackdown Java SDK already?

Thanks a lot :)

---

### Post by noigeaR on 2005-12-27
I would install Sun's Java SDK. The pacakge name from Ubuntu PLF is **sun-j2sdk1.5**. It supports the newer language features of version 1.5 and it has better compatibility and stability with certain programs. If you've had problems with eclipse, then it's better to use the Sun version instead of Blackdown.

Just to avoid confusion with the abbreviations.

**j2re** = Java 2 Runtime Environment
This is used to **run Java programs**. From version 1.2 onwards, Sun started to call it Java 2, but lately they've dropped the 2 from the name. If you download directly from Sun, it's called JRE.

**j2sdk** = Java 2 Software Development Kit
This is used to write and **compile Java programs** yourself. The Sun version of the SDK normaly includes the runtime environment, so you don't need to install both. As with the runtime environment Sun lately dropped the 2 in the name and it's now called JDK. They're not very consistent with the name change though, so sometimes you can see both names on the same page...

---

### Post by azteech on 2005-12-27
[quote=noeluylee]Hi, I have the JRE/ Java Web Start 1.5 on application>Internet I installed it thru apt-get, now I am trying to install a higher version of jre which I already downloaded it from [http://java.sun.com/j2se/1.5.0/download.jsp]("http://java.sun.com/j2se/1.5.0/download.jsp"). 

I follow the instruction from: [https://wiki.ubuntu.com/RestrictedFormats#head-68565ae07a003332e82c9f23706638777396c249]("https://wiki.ubuntu.com/RestrictedFormats#head-68565ae07a003332e82c9f23706638777396c249")  

I am having a problem on:
fakeroot make-jpkg jre-1_5_0_06-linux-i586.bin
sudo dpkg -i sun-j2re1.5_1.5.0+update06_i386.deb

Here my terminal window:
noel@NOEL-Linux:~$ fakeroot make-jpkg jre-1_5_0_06-linux-i586.bin.bin
Creating temporary directory: /tmp/make-jpkg.XXXXTOrWIs
Loading plugins: blackdown-j2re.sh blackdown-j2sdk.sh common.sh ibm-j2re.sh ibm-j2sdk.sh j2re.sh j2sdk-doc.sh j2sdk.sh j2se.sh sun-j2re.sh sun-j2sdk-doc.sh sun-j2sdk.sh

No matching plugin was found.
Removing temporary directory: done
noel@NOEL-Linux:~$ sudo dpkg -i sun-j2re1.5_1.5.0+update06_i386.deb
dpkg: error processing sun-j2re1.5_1.5.0+update06_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 sun-j2re1.5_1.5.0+update06_i386.deb

Hope you can give me suggestions.

PS - I want to update this cause I am having a problem on running the eclipse.[/quote] 
I too was having problems with java. I uninstalled everything; then I downloded automatix and installed sun java 1.5 from there. Once I downloaded it, I was still having problems running java apps until I was lead to a particular forum message. The following solved my java problem:
[http://ubuntuforums.org/showpost.php...&postcount=223]("http://ubuntuforums.org/showpost.php?p=594437&postcount=223")

I would recommend uninstalling/removing what you installed. Then I would recommend you install automatix. After automatix is installed, you can  install sun java 1.5 jre and sdk. Then, go to [http://ubuntuforums.org/showpost.php...&postcount=223]("http://ubuntuforums.org/showpost.php?p=594437&postcount=223")
to correct what apparently is a bug in automatix (which I have been informed, will be corrected after the holidays - see Post 234 in forum entry [http://www.ubuntuforums.org/showthread.php?p=604997#post604997](http://www.ubuntuforums.org/showthread.php?p=604997#post604997) ).

---

