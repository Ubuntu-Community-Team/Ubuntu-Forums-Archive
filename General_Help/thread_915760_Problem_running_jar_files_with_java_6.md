---
title: "Problem running jar files with java 6"
date: 2008-09-10
forum: General Help
---

### Post by sonu611 on 2008-09-10
I have a problem in running jar files in my ubuntu 8.04.
I installed java 6 (jdk) via synaptic.
Now when i run "java -jar filename.jar" nothing happens.
the command neither gives any error message nor run the file.

I was able to run the same file in ubuntu 7.10 using java 6 with no problem.
Please Help. Also simple java programs run without any problem in my current installation.

I have a 32 bit system with 512 mb ram.

---

### Post by fooman on 2008-09-10
try specifying the path to the file.  for example if it is located in your Documents folder:

```
java -jar /home/<username>/Documents/filename.jar
```

or just:

```
java -jar ~/Documents/filename.jar
```

see if that works

---

### Post by sonu611 on 2008-09-10
I ran the command from the directory in which the jar file is located, so i dont think path is necessary.
Any way i tried it and still the same result.
No error messages/ no application window(it has a gui awt)/ nothing.
just a new line in my shell

---

### Post by Marcos.Rufino on 2008-09-14
For Christ sake!!! I can't believe Ubuntu 8.04 can't do a so simple thing! I'm also having this f** problem. I try to "java -jar blablabla" and it says java could be found in a series of packages. I've installed them all and nothing. In previous Ubuntu versions I could easily run java packages but now... Man, I'm really fed up!

---

### Post by Tanker Bob on 2008-09-14
After you install Sun Java 6, sometimes you need to run:

```
sudo update-java-alternatives -s java-6-sun
```

You may also need to edit the /etc/jvm file to either add the line /usr/lib/jvm/java-6-sun to the top of the list or move it to the top if the line is already there. When all that is done, type:

```
java -version
```

It should provide about 3 lines of information on the java installation. I use the open source package and it returns:

```
java version "1.6.0_0"
OpenJDK  Runtime Environment (build 1.6.0_0-b11)
OpenJDK Server VM (build 1.6.0_0-b11, mixed mode)
```

---

### Post by sonu611 on 2008-09-15
Thank you tanker bob
That did the trick.
Could you please shed some light on what
```
sudo update-java-alternatives -s java-6-sun
```
actually does and why hardy does not do this by itself.
These little things could put off a new user very quickly.

---

### Post by jespdj on 2008-09-15
There is more than one implementation of Java available for Hardy. There's the OpenJDK version of Java 6 and there's the Sun version of Java 6.

The OpenJDK version of Java is Sun's project to make Java 100% open source. It's almost identical to Sun Java 6, but not completely. Almost everything works normally on OpenJDK Java, but some programs don't.

The update-alternatives command that Tanker Bob mentioned sets Sun Java 6 as the default Java to use on your system.

---

### Post by porchrat on 2008-09-15
you can also view which versions of java you currently have on your system with this command:

```
sudo update-alternatives --display java
```

It will show you which versions are currently installed and which version the symbolic link "java" currently points to.  Quite handy

You can do the same for the compiler:

```
sudo update-alternatives --display javac
```

---

### Post by Tanker Bob on 2008-09-15
> **sonu611 said:**
> Thank you tanker bob
That did the trick.
Could you please shed some light on what
```
sudo update-java-alternatives -s java-6-sun
```
actually does and why hardy does not do this by itself.
These little things could put off a new user very quickly.

jespdj had the answer--it sets the named java VM as primary. The issue isn't Hardy's fault, but Java's. Same with the current disconnect between Java and CUPS on printing. I doubt that the Ubuntu team has the time to rewrite Sun's code for them. I absolutely agree that it's frustrating. It's usually the java application developers that get blamed for the problems when the issues are with Sun's code. That hurts everybody.

---

### Post by sonu611 on 2008-09-16
ok I am sorry :(
I didnt look for the problem source myself. turns out, the problem wasnt hardy or java its the desktop effects thats causing the problem.
the jar file i tried to run has a gui.
I get some problem playing video files too with the desktop effects turned on.
With the desktop effects turned off, i have no problem in running jar files or video files.
 guess something wrong with my ati drivers or a particular effect.

any way thank you all for the great replies and any ideas on solving the desktop effects problem is also welcome.

---

