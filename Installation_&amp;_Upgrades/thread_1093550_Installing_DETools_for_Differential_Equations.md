---
title: "Installing DETools for Differential Equations"
date: 2009-03-11
forum: Installation &amp; Upgrades
---

### Post by mahasmb on 2009-03-11
I just thought this may help a few people with this problem (plus, I can look this up later if I have a similar problem). I called technical support and they said "they don't support linux" even though it clearly says on the CD that the software was made to work for linux. You've really got to hate that.

 Anywho...

```
$ sh ./install.bin
Preparing to install...
Extracting the JRE from the installer archive...
Unpacking the JRE...
Extracting the installation resources from the installer archive...
Configuring the installer for this system's environment...
nawk: error while loading shared libraries: libdl.so.2: cannot open shared object file: No such file or directory
dirname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
/bin/ls: error while loading shared libraries: librt.so.1: cannot open shared object file: No such file or directory
basename: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
dirname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
basename: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
hostname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory

Launching installer...

grep: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
/tmp/install.dir.16798/Linux/resource/jre/bin/java: error while loading shared libraries: libpthread.so.0: cannot open shared object file: No such file or directory

```

That was what I got when I tried to install the program.

This is the fix:

>  Re: error while loading shared libraries: libm.so.6
I ran into the same issue while installing maple 9.5 for linux on Feisty. However, searching on google, I found this fix for the same problem but for a different program

[http://www.zend.com/support/knowledg...84&view_only=1](http://www.zend.com/support/knowledg...84&view_only=1)

here are the adpated instructions to make this work for maple:

- copy the cd contents to the hard drive
- go to the directory /Linux/Disk1/InstData/VM or wherever the file [COLOR="Red"]LinuxInstaller[/COLOR].bin is located
- then do the following two commands

cp [COLOR="Red"]LinuxInstaller[/COLOR].bin [COLOR="Red"]LinuxInstaller[/COLOR].bin.bak

cat [COLOR="Red"]LinuxInstaller[/COLOR].bin.bak | sed "s/export LD_ASSUME_KERNEL/#xport LD_ASSUME_Kernel/" > [COLOR="Red"]LinuxInstaller[/COLOR].bin

- after that, run the installer as normal and it should work

And of course, in this case you'd change "LinuxInstaller" into whatever name your .bin has. I've changed them to red just for convenience.

I've got to thank user mark_sfu for that one. It was a life saver!

---

### Post by mahasmb on 2009-03-11
Okay, so you get the exact same problem when you try to run the installed program file. Just repeat the process for the installed file and it should work.

---

### Post by stickmanftw on 2009-08-23
Thank you so much for this! I've got it installed, but I see two files, DE and Differential_Equations.  I get the same error when running both.  I used the fix you posted, but now when I run either one, nothing happens, no error or anything.  Are these the main program files?

---

### Post by stickmanftw on 2009-08-23
Nevermind, I got it.

---

### Post by mahasmb on 2009-08-23
I'm glad to know that I helped at least one person :)

---

### Post by odoemer on 2010-06-15
I found that with this little script in ~/bin the installers work without having to modify the installer file, (assuming that ~/bin is in your PATH before the OOTB strings command)

[FONT=Courier New]$ cat ~/bin/strings 
#!/bin/sh

if [ "$1" = "/lib/libc.so.6" ]; then
    /usr/bin/strings $@ | grep -vi nptl
else
    /usr/bin/strings $@
fi[/FONT]

---

