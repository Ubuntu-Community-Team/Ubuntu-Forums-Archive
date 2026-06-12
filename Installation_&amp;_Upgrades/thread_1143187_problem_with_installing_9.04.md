---
title: "problem with installing 9.04"
date: 2009-04-29
forum: Installation &amp; Upgrades
---

### Post by iggynig on 2009-04-29
Hi,

I have been having major problems since trying to install 9.04

i left my webbook on overnight to install the update, but it crashed before it was complete.

I now have a resolution which is far to big for the screen and changing the display settings doesn't seem to help.

I have tried entering a lot of commands though the Termonal which other forum members have siggested, but none of them have worked.
  Everytime i run a command it comes up with libchipcardexit error 1 message.

below is an example of this.


Processing triggers for doc-base ...
Processing 1 changed doc-base file(s)...
Registering documents with scrollkeeper...
Setting up libchipcard-tools (4.1.3-2ubuntu1) ...
Starting libchipcard daemon: invoke-rc.d: initscript libchipcard-tools, action "start" failed.
dpkg: error processing libchipcard-tools (--configure):
subprocess post-installation script returned error exit status 1
Setting up acpid (1.0.6-9ubuntu4.9.04.2) ...
* Stopping Hardware abstraction layer hald [ OK ] 
* Loading ACPI modules... [ OK ] 
* Starting ACPI services... [ OK ] 
* Starting Hardware abstraction layer hald [ OK ] 

Setting up libfreetype6 (2.3.9-4ubuntu0.1) ...

Setting up libfreetype6-dev (2.3.9-4ubuntu0.1) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
libchipcard-tools
E: Sub-process /usr/bin/dpkg returned an error code (1)
iggynig@ubuntu:~$
    	

Any one have any ideas how to fix this ?

Also, before anyone mentions reinstalling, i have tried downloading the version again but it won't let me run it. It only gives me the option of burning a disk, and as my webbook has no cd/dvd drive it's not really an option for me. 

is there a way to reinstall ubuntu from a usb stick ?

---

### Post by ronparent on 2009-04-29
Yes, use unetbootin to tranfer an iso image to a bootable usb stick.

---

### Post by KJH on 2009-05-04
I've found a solution that worked for me with the screen resolution thing, check here [http://ubuntuforums.org/showthread.php?p=7212041](http://ubuntuforums.org/showthread.php?p=7212041)

---

