---
title: "Ubuntu 9.04 Java JRE and JDK wont Install"
date: 2009-09-04
forum: Installation &amp; Upgrades
---

### Post by therocco2k on 2009-09-04
[CENTER]**My Version: **Ubuntu Jaunty 9.04
[/CENTER]
Hello All, I have a headache on my hands and I cannot figure it out for the life of me.
I installed a bunch of files from Synpatic Manager that said Java trying to get Java JRE and JDK to install, so I can run Vuze, and other Java Programs as well as Write and COMPILE Java programs on my own... 

I've run into a problem I CANNOT get past, It keeps giving me errors, I even tried to use the Famous Java Terminal Install Command: 
[FONT=BankGothic Lt BT][COLOR=Black][SIZE=2]sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts[/SIZE] [/COLOR][/FONT]
[B]
But it doesnt work
Console Output Error I get EACH time after I run that above command, or Try to uninstall or install any Java 6 JRE or JDK files[/B]
```

rcastoro@rcastoro-desktop:~$  sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libcommons-cli-java libswt-gtk-3.4-java libswt-gnome-gtk-3.4-jni
  libcommons-lang-java libswt-cairo-gtk-3.4-jni libswt-gtk-3.4-jni
  libswt-mozilla-gtk-3.4-jni
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  sun-java6-bin
The following NEW packages will be installed:
  sun-java6-bin sun-java6-fonts sun-java6-jre sun-java6-plugin
0 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/35.5MB of archives.
After this operation, 101MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Preconfiguring packages ...
Selecting previously deselected package sun-java6-jre.
(Reading database ... 203343 files and directories currently installed.)
Unpacking sun-java6-jre (from .../sun-java6-jre_6-14-0ubuntu1.9.04_all.deb) ...
sun-dlj-v1-1 license has already been accepted
Selecting previously deselected package sun-java6-bin.
Unpacking sun-java6-bin (from .../sun-java6-bin_6-14-0ubuntu1.9.04_i386.deb) ...
sun-dlj-v1-1 license has already been accepted
Selecting previously deselected package sun-java6-fonts.
Unpacking sun-java6-fonts (from .../sun-java6-fonts_6-14-0ubuntu1.9.04_all.deb) ...
Selecting previously deselected package sun-java6-plugin.
Unpacking sun-java6-plugin (from .../sun-java6-plugin_6-14-0ubuntu1.9.04_i386.deb) ...
Processing triggers for shared-mime-info ...
Unknown media type in type 'all/all'

Unknown media type in type 'all/allfiles'

Unknown media type in type 'uri/mms'

Unknown media type in type 'uri/mmst'

Unknown media type in type 'uri/mmsu'

Unknown media type in type 'uri/pnm'

Unknown media type in type 'uri/rtspt'

Unknown media type in type 'uri/rtspu'

Unknown media type in type 'fonts/package'

Unknown media type in type 'interface/x-winamp-skin'

Setting up sun-java6-doc (6-14-0ubuntu1.9.04) ...
This package is an installer package, it does not actually contain the
JDK documentation.  You will need to go download one of the
archives:

    jdk-6u10-docs.zip jdk-6u10-docs-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    http://java.sun.com/javase/downloads/

now and download.  The file should be owned by root.root and be copied
to /tmp.

[Press RETURN to try again, 'no' + RETURN to abort] 
```I even tried to go to the JAVA web-site and I downloaded the latest files:
jre-6u16-linux-i586-rpm.bin and jdk-6u16-linux-i586-rpm.bin but do not know how to install them, I think I tried and got the same result.


Somebody PLEASE help me, I've done something to make my Ubuntu Install NOT want to have anything to do with JAVA JRE, JDK, or JAVA ANYTHING.

Can somebody please save me a ever growing headache and walk me through fixing and installing the java jre and jdk please. I Appreciate it.

---

### Post by zvacet on 2009-09-04
Try to install from synaptic.Type sun in search box and you will find packages you are looking for.You have to accept Java licence agreement.If synaptic shows that packages are installed reinstall it to get to the licence.

---

### Post by erenay on 2009-09-07
I have the same problem but I don't have access to synaptic.
Any suggestions?? What might be the reason of this error?

> Do you agree with the DLJ license terms? yes


Selecting previously deselected package odbcinst1debian1.
Unpacking odbcinst1debian1 (from .../odbcinst1debian1_2.2.11-16build3_i386.deb) ...
Selecting previously deselected package unixodbc.
Unpacking unixodbc (from .../unixodbc_2.2.11-16build3_i386.deb) ...
Selecting previously deselected package sun-java6-bin.
Unpacking sun-java6-bin (from .../sun-java6-bin_6-14-0ubuntu1.9.04_i386.deb) ...
debconf: unable to initialize frontend: Dialog
debconf: (Dialog frontend will not work on a dumb terminal, an emacs shell buffer, or with
out a controlling terminal.)
debconf: falling back to frontend: Readline
sun-dlj-v1-1 license has already been accepted
Selecting previously deselected package sun-java6-jdk.
Unpacking sun-java6-jdk (from .../sun-java6-jdk_6-14-0ubuntu1.9.04_i386.deb) ...
debconf: unable to initialize frontend: Dialog
debconf: (Dialog frontend will not work on a dumb terminal, an emacs shell buffer, or with
out a controlling terminal.)
debconf: falling back to frontend: Readline
sun-dlj-v1-1 license has already been accepted
Selecting previously deselected package gsfonts-x11.
Unpacking gsfonts-x11 (from .../gsfonts-x11_0.21_all.deb) ...
Processing triggers for shared-mime-info ...
Unknown media type in type 'all/all'

Unknown media type in type 'all/allfiles'

Unknown media type in type 'uri/mms'

Unknown media type in type 'uri/mmst'

Unknown media type in type 'uri/mmsu'

Unknown media type in type 'uri/pnm'

Unknown media type in type 'uri/rtspt'

Unknown media type in type 'uri/rtspu'

Unknown media type in type 'fonts/package'

Unknown media type in type 'interface/x-winamp-skin'

Processing triggers for man-db ...
Processing triggers for doc-base ...
Processing 1 added doc-base file(s)...
Registering documents with scrollkeeper...
Setting up odbcinst1debian1 (2.2.11-16build3) ...

Setting up unixodbc (2.2.11-16build3) ...

Setting up gsfonts-x11 (0.21) ...

Setting up sun-java6-bin (6-14-0ubuntu1.9.04) ...

Setting up sun-java6-jre (6-14-0ubuntu1.9.04) ...

Setting up sun-java6-jdk (6-14-0ubuntu1.9.04) ...
debconf: unable to initialize frontend: Dialog
debconf: (Dialog frontend will not work on a dumb terminal, an emacs shell buffer, or with
out a controlling terminal.)
debconf: falling back to frontend: Readline

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
root@(none):/#

---

### Post by Mighty_Joe on 2009-09-08
> **therocco2k said:**
> 

Setting up sun-java6-doc (6-14-0ubuntu1.9.04) ...
This package is an installer package, it does not actually contain the
JDK documentation.  You will need to go download one of the
archives:

    jdk-6u10-docs.zip jdk-6u10-docs-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    [http://java.sun.com/javase/downloads/](http://java.sun.com/javase/downloads/)

now and download.  The file should be owned by root.root and be copied
to /tmp.


[I've seen this problem before]("http://ubuntuforums.org/showpost.php?p=7747882&postcount=6")

---

