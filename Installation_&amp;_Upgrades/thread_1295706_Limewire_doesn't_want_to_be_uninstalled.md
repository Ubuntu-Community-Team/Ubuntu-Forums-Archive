---
title: "Limewire doesn't want to be uninstalled"
date: 2009-10-19
forum: Installation &amp; Upgrades
---

### Post by Chad5ter on 2009-10-19
Sup people!

I need your help. I just installed Limewire and after seeing the interface, I found it so gay ... Now I'm trying to uninstall it, but doesn't work. It says this:

```

chad@chad-desktop:~$ sudo apt-get remove -f limewire-basic
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be REMOVED:
  limewire-basic
0 upgraded, 0 newly installed, 1 to remove and 19 not upgraded.
1 not fully installed or removed.
After this operation, 63.3MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 90263 files and directories currently installed.)
Removing limewire-basic ...
/var/lib/dpkg/info/limewire-basic.prerm: 6: gconf-schemas: not found
dpkg: error processing limewire-basic (--remove):
 subprocess installed pre-removal script returned error exit status 127
Errors were encountered while processing:
 limewire-basic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```Cheers!

Chad5ter
Québec-~

---

### Post by cwbar_1 on 2009-10-19
Try this.
sudo dpkg --remove limewire-basic

---

### Post by snake_eyes on 2009-11-01
Hello,

I have the same problem and I tried both commands and still getting error:

```
sudo dpkg --remove limewire-basic
(Reading database ... 139297 files and directories currently installed.)
Removing limewire-basic ...
Warning: /usr/share/gconf/schemas/limewire.schemas could not be found.
Usage: gconf-schemas --[un]register file1.schemas [file2.schemas [...]]

gconf-schemas: error: You need at least a file to (un)register.
dpkg: error processing limewire-basic (--remove):
 subprocess installed pre-removal script returned error exit status 2
Errors were encountered while processing:
 limewire-basic
```

any idea please?

---

### Post by ikt on 2009-11-01
> **Chad5ter said:**
> I need your help. I just installed Limewire and after seeing the interface, I found it so gay ... ~

[http://www.youtube.com/watch?v=sWS0GVOQPs0](http://www.youtube.com/watch?v=sWS0GVOQPs0)

;)

I just installed limewire then, to uninstall I went to system > admin > synaptic package manager > searched for: limewire > right click > set for complete removal > apply.

[IMG]http://dl.getdropbox.com/u/2161836/pictures/limewire.png[/IMG]

Ubuntu 9.10.

---

### Post by snake_eyes on 2009-11-01
I already did you suggestion, and now I tried also and got this error:
```

(Reading database ... 140334 files and directories currently installed.)
Removing limewire-basic ...
Warning: /usr/share/gconf/schemas/limewire.schemas could not be found.
Usage: gconf-schemas --[un]register file1.schemas [file2.schemas [...]]

gconf-schemas: error: You need at least a file to (un)register.
dpkg: error processing limewire-basic (--purge):
 subprocess installed pre-removal script returned error exit status 2
Errors were encountered while processing:
 limewire-basic
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:

```

I think there is an important issue which is notified here:
> Warning: /usr/share/gconf/schemas/limewire.schemas could not be found.

Any idea please....

Cheers,

---

### Post by snake_eyes on 2009-11-02
Thank you for your response, I removed it by copying the missing file from another machine...

Cheers,

---

### Post by judge jankum on 2009-11-02
Each machine must have it's own personality" "so to speak"

---

### Post by snake_eyes on 2009-11-02
This what I did and removed successfully without any warning or something else...

Cheers,

---

