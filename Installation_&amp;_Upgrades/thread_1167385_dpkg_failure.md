---
title: "dpkg failure"
date: 2009-05-22
forum: Installation &amp; Upgrades
---

### Post by Oded on 2009-05-22
Hello,
While I was trying to install virtualbox (.deb) I encountered an error..
It install dependencies I was missing:
Python2.5, Python2.5-minimal
and failed with the latter printing out:```
Errors were encountered while processing:
 python2.5-minimal
E: Sub-process /usr/bin/dpkg returned an error code (1)
```
Now when I try to remove/reinstall python2.5-minimal I get the following:```

Setting up python2.5-minimal (2.5.4-1ubuntu4) ...
Linking and byte-compiling packages for runtime python2.5...
update-binfmts: /var/lib/binfmts/jar corrupt: out of binfmt data reading
package 
dpkg: error processing python2.5-minimal (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 python2.5-minimal
E: Sub-process /usr/bin/dpkg returned an error code (1)
```
I've searched the forums and didn't come up with a solution
Help please?
Edit: forgot to mention for what it's worth I'm using Jaunty 64amd with ext4

---

### Post by pytheas22 on 2009-05-23
What is the output of:
```

cat /var/lib/binfmts/jar
ls -l /var/lib/binfmts/jar
```

---

### Post by Oded on 2009-05-23
Here:```

oded@oded-laptop:~$ cat /var/lib/binfmts/jar
oded@oded-laptop:~$ ls -l /var/lib/binfmts/jar
-rw-r--r-- 1 root root 0 2009-05-23 01:15 /var/lib/binfmts/jar
```
Thanks

---

### Post by pytheas22 on 2009-05-23
It looks like your /var/lib/binfmts/jar file is empty, which is probably the problem.  Please open it up in a text editor by typing:
```

sudo gedit /var/lib/binfmts/jar
```

Then paste this into it:
```

sun-java6
magic
0
PK\x03\x04

/usr/lib/jvm/java-6-sun-1.6.0.13/jre/lib/jexec
```

Then save the file, and try installing your program again.

I have no idea what the contents of the file do, but on my system (also 64-bit Jaunty) that's what I have inside /var/lib/binfmts/jar, and I assume it's not supposed to be empty.

---

### Post by Oded on 2009-05-23
I've done as you suggested and it didn't work (gave the same error),
I then thought I'd go ahead and reinstall java but now the problem got worse:```
oded@oded-laptop:~$ sudo apt-get autoremove
[sudo] password for oded: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
5 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up sun-java6-bin (6-13-1) ...
update-alternatives: error or eof reading /var/lib/dpkg/alternatives/ControlPanel for update_mode ()
dpkg: error processing sun-java6-bin (--configure):
 subprocess post-installation script returned error exit status 2
Setting up openjdk-6-jre (6b14-1.4.1-0ubuntu7) ...
update-alternatives: error or eof reading /var/lib/dpkg/alternatives/pluginappletviewer for update_mode ()
dpkg: error processing openjdk-6-jre (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of icedtea6-plugin:
 icedtea6-plugin depends on openjdk-6-jre (= 6b14-1.4.1-0ubuntu7); however:
  Package openjdk-6-jre is not configured yet.
dpkg: error processing icedtea6-plugin (--configure):
 dependency problems - leaving unconfigured
Setting up python2.5-minimal (2.5.2-2ubuntu4.1) ...
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                            File "/usr/lib/python2.5/encodings/cp863.py", line 411
    REEK SMALL LETTER DELTA
       ^
SyntaxError: invalid syntax
Linking and byte-compiling packages for runtime python2.5...
update-binfmts: /var/lib/binfmts/jar~ corrupt: out of binfmt data reading
package 
dpkg: error processing python2.5-minimal (--configure):
 subprocess post-installation script returned error exit status 2
Setting up rhino (1.7R1-2) ...
No apport report written because MaxReports is reached already
                                                              update-alternatives: error or eof reading /var/lib/dpkg/alternatives/js for update_mode ()
dpkg: error processing rhino (--configure):
 subprocess post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 sun-java6-bin
 openjdk-6-jre
 icedtea6-plugin
 python2.5-minimal
 rhino
E: Sub-process /usr/bin/dpkg returned an error code (1)
```
At this point I guess I'm leaning towards a complete Ubuntu reinstall unless someone can come up with a solution

---

### Post by pytheas22 on 2009-05-23
hmmm, I'm sorry but I don't know how to make sense out of that.  A reinstallation might be your best option at this point...

---

### Post by Oded on 2009-05-23
Thanks for trying either way

---

### Post by freakalad on 2009-05-24
I'm getting similar issues on my 64-bit Hardy LTS system.
Started with my last KVM update, and since then nothing quite been able to install or upgrade properly.

[Details posted here]("http://ubuntuforums.org/showthread.php?t=1169061")

At first I thought it was a [bad patch]("http://ubuntuforums.org/showthread.php?t=1157830") from KVM, but since the problem/errors/bug is growing in scope to include other apps/installers, I'm starting to suspect it may lie in the package manager itself.

Of course I don't know enough behind-the-curtains magic to make a authoritative determination one way or another, so I can only provide "symptoms"

I really hope there's a simple solution to this, cause I'd rather prefer not to do an install from scratch.

---

