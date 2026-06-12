---
title: "Problems installing Staroffice"
date: 2008-07-20
forum: General Help
---

### Post by Fatfool on 2008-07-20
Good day,

Ubuntu (or maybe Sun) has decided to give me the fourth kick in the balls on on moving to ubuntu. (first was from getting java plugins to work in a 64 bit enviroment; second from getting google earth to work WITHOUT root privileges; third was from installing sane backends for my scanner) but i digress.

anyway, so I've downloaded the .bin from sun and here it goes according to instructions here:
[https://help.ubuntu.com/community/StarOffice](https://help.ubuntu.com/community/StarOffice)

```
jeffery@Roomcomp:~$ cd /home/jeffery/Desktop
jeffery@Roomcomp:~/Desktop$ sh so-8-pp10-bin-linux-en-US.sh 

Select the directory in which to save the unpacked files. [/var/tmp/unpack_staroffice] 

Directory /var/tmp/unpack_staroffice already exists.
Please select a new directory name.
jeffery@Roomcomp:~/Desktop$ rm -rf /var/tmp/unpack_staroffice
rm: cannot remove `/var/tmp/unpack_staroffice': Permission denied
jeffery@Roomcomp:~/Desktop$ sudo rm -rf /var/tmp/unpack_staroffice
[sudo] password for jeffery: 
jeffery@Roomcomp:~/Desktop$ sh so-8-pp10-bin-linux-en-US.sh 

Select the directory in which to save the unpacked files. [/var/tmp/unpack_staroffice] 

File is being checked for errors ...
Unpacking ...
All files have been successfully unpacked.
Unpacking...
Checksumming...
Extracting...
Done.
Running installer
InvocationTargetException in ArchiveReader constructornull
java.lang.reflect.InvocationTargetException
	at sun.reflect.NativeConstructorAccessorImpl.newInstance0(Native Method)
	at sun.reflect.NativeConstructorAccessorImpl.newInstance(Unknown Source)
	at sun.reflect.DelegatingConstructorAccessorImpl.newInstance(Unknown Source)
	at java.lang.reflect.Constructor.newInstance(Unknown Source)
	at install.instantiateArchiveReader(ArchiveClassLoader.java:203)
	at install.<init>(ArchiveClassLoader.java:143)
	at install.main(ArchiveClassLoader.java:1263)
Caused by: java.lang.RuntimeException: the /var/opt/sun/install directory does not exist.
	at com.sun.wizards.registry.XmlRegistry.<init>(XmlRegistry.java:59)
	at LinuxPlatformToolkit.attach(LinuxPlatformToolkit.java:590)
	at com.sun.wizards.core.SystemInterface.attach(SystemInterface.java:69)
	at com.sun.wizards.core.ArchiveReader.<init>(ArchiveReader.java:170)
	... 7 more
Target Exception Trace:
java.lang.RuntimeException: the /var/opt/sun/install directory does not exist.
	at com.sun.wizards.registry.XmlRegistry.<init>(XmlRegistry.java:59)
	at LinuxPlatformToolkit.attach(LinuxPlatformToolkit.java:590)
	at com.sun.wizards.core.SystemInterface.attach(SystemInterface.java:69)
	at com.sun.wizards.core.ArchiveReader.<init>(ArchiveReader.java:170)
	at sun.reflect.NativeConstructorAccessorImpl.newInstance0(Native Method)
	at sun.reflect.NativeConstructorAccessorImpl.newInstance(Unknown Source)
	at sun.reflect.DelegatingConstructorAccessorImpl.newInstance(Unknown Source)
	at java.lang.reflect.Constructor.newInstance(Unknown Source)
	at install.instantiateArchiveReader(ArchiveClassLoader.java:203)
	at install.<init>(ArchiveClassLoader.java:143)
	at install.main(ArchiveClassLoader.java:1263)
jeffery@Roomcomp:~/Desktop$ 

```
:confused: no graphical window pops up.

I tried the instructions here:
[http://ubuntuforums.org/showthread.php?t=290036&highlight=staroffice](http://ubuntuforums.org/showthread.php?t=290036&highlight=staroffice)
about not using the default folder when it extracts but the same shite message pops up.

Since I have recovered from the last 3 kicks in the nuts, I suppose there is some way of installing this....... just got to ask around as usual and hope someone can figure this out. anyone got ideas? I prefer Staroffice over Oo for its less cluttered interface and its themes for Presentation.

edit:
seems that theres a thread very similar to it...

[http://ubuntuforums.org/showthread.php?t=114387&highlight=staroffice](http://ubuntuforums.org/showthread.php?t=114387&highlight=staroffice)
but it needs to convert an RPM to .deb?!

---

### Post by Fatfool on 2008-07-20
a little help around here?

---

### Post by Fatfool on 2008-07-20
does installing Staroffice require java to be installed? mine doesn't have java from the sypnatic package manager installed as I use the 32 bit version of Firefox for java plugins.

---

### Post by Fatfool on 2008-07-21
A little help please? Staroffice isn't such a rare program to use right?

---

### Post by Fatfool on 2008-07-30
gonna bump this again....

---

### Post by tinny on 2008-08-01
Why arent you using OpenOffice? OpenOffice and StarOffice are the same thing. OpenOffice is the default office suite for Ubuntu.

Read the first paragraph of this...
[http://en.wikipedia.org/wiki/StarOffice](http://en.wikipedia.org/wiki/StarOffice)

---

### Post by Fatfool on 2008-10-12
> **tinny said:**
> Why arent you using OpenOffice? OpenOffice and StarOffice are the same thing. OpenOffice is the default office suite for Ubuntu.

Read the first paragraph of this...
[http://en.wikipedia.org/wiki/StarOffice](http://en.wikipedia.org/wiki/StarOffice)
oops sorry i thought no one answered. well, I find that staroffice is less 'cluttered'.

---

