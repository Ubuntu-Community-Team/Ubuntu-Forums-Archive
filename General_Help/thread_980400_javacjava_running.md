---
title: "javac/java running"
date: 2008-11-12
forum: General Help
---

### Post by Robo495 on 2008-11-12
I've installed java packages over and over, tried so many things I can't even remember them all anymore, in short I have java and javac resources installed, but cannot run the commands.

Using Ubuntu heron, bash.

I've done these things (that I can remember):
apt-get install sun-java6-jdk
adding the paths to $PATH and exporting
using synaptic to install it

(I'm just retyping what I get from shell so yes the % are silly)

Here is some of what I get:
% whereis javac
javac: /usr/bin/javac
% whereis java
java: /usr/lib/java /usr/share/java
% java
The program 'java' can be found in the following packages:
..... (list of packages)
% javac
The program 'javac' can be found in the following packages:
..... (list of packages)
% echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games


Help please?

---

### Post by ju2wheels on 2008-11-12
```

sudo apt-get install sun-java6-jdk sun-java6-jre
sudo update-java-alternatives -s java-6-sun
gksudo gedit /etc/jvm

```

Make this the first line listed in /etc/jvm:

```

/usr/lib/jvm/java-6-sun

```

Then run
```

java -version

```

And make sure you get something similar too:
```

java version "1.6.0_10"
Java(TM) SE Runtime Environment (build 1.6.0_10-b33)
Java HotSpot(TM) 64-Bit Server VM (build 11.0-b15, mixed mode)

```

Of course yours would say 32bit if you are using 32bit Ubuntu.

---

### Post by Robo495 on 2008-11-12
Did all that, this happens when I do java-version

% java -version
The program 'java' can be found in the following packages 
.... (list of packages again :( )

---

### Post by ju2wheels on 2008-11-12
Its probably a package configuration issue. Have you tried completely uninstalling the packages (including residual config files) and reinstalling?

---

### Post by Robo495 on 2008-11-12
ok I removed packages through synaptics, did it all, 

java command works.

javac still can't be found.

more info:
% sudo update-alternatives --list javac
/usr/lib/jvm/java-6-sun/bin/javac

%sudo update-alternatives --list java
/usr/lib/jvm/java-6-sun/jre/bin/java

---

### Post by Robo495 on 2008-11-12
bump, added more info

---

### Post by ju2wheels on 2008-11-12
Would you mind posting the output of this:

```

more /etc/jvm

```

It sounds as if reinstalling fixed the configuration for your JRE but not the JDK.

---

### Post by Robo495 on 2008-11-12
$ more /etc/jvm
# This file defines the default system JVM search order. Each
# JVM should list their JAVA_HOME compatible directory in this file.
# The default system JVM is the first one available from top to
# bottom.

/usr/lib/jvm/java-6-sun
/usr/lib/jvm/java-gcj
/usr/lib/jvm/ia32-java-1.5.0-sun
/usr/lib/jvm/java-1.5.0-sun
/usr

---

### Post by ju2wheels on 2008-11-12
I really still think its just the configuration thats messed up, since reinstalling fixed the JRE which didnt work before. The output you posted is fine so there is no problem with that part of it.

Force a reconfigure and see if that helps:
```

sudp dpkg-reconfigure sun-java6-jdk sun-java6-jre

```

---

### Post by Robo495 on 2008-11-12
Tried that (I knew to use sudo :D), java still works, javac still broken.

Are there settings in some other place maybe?

---

### Post by ju2wheels on 2008-11-12
Hmmm weird indeed, javac works fine for me on the command line.

Did you follow any additional instructions when you first installed java that I didnt list above?

What do you get as output for these:
```

file /usr/bin/javac
file /etc/alternatives/javac
file /usr/lib/jvm/java-6-sun/bin/javac

```

At a minimum the last one should obviously be there. The first one id assume is the one that is missing on your setup.

On my machine the first two are symbolic links as follows:
/usr/bin/javac to /etc/alternatives/javac
/etc/alternatives/javac to /usr/lib/jvm/java-6-sun/bin/javac

So worst case just add the symbolic links in by hand.

There are no additional places that I know of for configurations settings. I dont think java creates any per user directory settings (I dont have any on my machine anyway..).

---

### Post by Robo495 on 2008-11-12
$ file /usr/bin/javac
/usr/bin/javac: directory

$ file /etc/alternatives/javac
/etc/alternatives/javac: ERROR: cannot open '/etc/alternatives/javac' (No such file or directory)

$ file /usr/lib/jvm/java-6-sun/bin/javac
/usr/lib/jvm/java-6-sun/bin/javac: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), for GNU/Linux 2.2.5, dynamically linked (uses shared libs), not stripped


I'm not smart enough to know how to add symbolic links by hand.

---

### Post by ju2wheels on 2008-11-12
Errr that is a hot mess. Javac should definitely not be a directory.

Ok here goes nothing:
```

sudo rm /usr/bin/javac
sudo update-java-alternatives -s java-6-sun
file /etc/alternatives/javac

```

If the last command gives you the same error as it did the first time, then do the following:
```

sudo ln -s /usr/lib/jvm/java-6-sun/bin/javac /etc/alternatives/javac

```

Then the last command is:
```

sudo ln -s /etc/alternatives/javac /usr/bin/javac

```

---

### Post by Robo495 on 2008-11-12
Uhm quick issue

$ sudo rm /usr/bin/javac
rm: cannot remove '/usr/bin/javac': Is a directory

---

### Post by ju2wheels on 2008-11-12
Sorry that should have been rmdir

---

### Post by Robo495 on 2008-11-12
It just keeps going :(

$ sudo rmdir /usr/bin/javac
rmdir: failed to remove '/usr/bin/javac': Directory not empty

---

### Post by dfgilbert on 2008-11-12
Well, you need to set the paths.

if you type 
```

echo $JAVA_HOME

```

and it comes back blank, that lets you know the path is not set to it.

Now, I tried
```

export JAVA_HOME=<link to java>

```

This did not work for me.

Do this
```

sudo gedit /etc/environment

```

wherever you installed Java to should be added as
```

JAVA_HOME="<java dir>/bin/java"

```

Then add that same link to your path.

I installed Java by downloading it from sun.com, unzipping and moving it to /opt/jdk1.6.0_10

So my environment file looks like this
```

PATH="/opt/jdk1.6.0_10/bin/java:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
JAVA_HOME="/opt/jdk1.6.0_10/bin/java"

```

I hope this helps you.

---

### Post by ju2wheels on 2008-11-12
Do you have openjdk-6-jdk installed? If you do can you uninstall it...

Edit: The above should not be necessary at all. The /opt path will most likely not exist on his machine, unless he did some other modifications. JAVA_HOME might be needed by some applications but will not fix your current issue.

---

### Post by Robo495 on 2008-11-12
synaptic shows no openjdk packages installed.

---

### Post by ju2wheels on 2008-11-12
Ok I guess next step is to determine whats in that folder to see if it can go then. Its weird because it shouldnt really be a directory there. The bin folder typically either holds the executables or links to them.

```

ls -alR /usr/bin/javac

```

---

### Post by Robo495 on 2008-11-12
Alright I tried rm -rf and that removed it, ran the commands, now:

Javac works. Huge thanks man. HUGE! :D

---

