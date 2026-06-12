---
title: "Yugma needs Java, but"
date: 2008-07-30
forum: General Help
---

### Post by ELMIT on 2008-07-30
I found a Gotomeeting like program from Yugma, however, I also got here some problems. Tech support answered:

> On Linux, there's a few caveats when installing Java. I have never been successful installing Java from the java website - it just doesn't work that easily.
The easiest and most successful way is through Linux's package manager. You will need both sun-java-6 and sun-java-6-plugin (for browser interactivity with Java).

Please click this link. Let me know what it says in the pink box that should appear in the middle of the page:
[http://www.javatester.org/version.html](http://www.javatester.org/version.html)
It should be Sun Java 1.6 or higher.

Also please verify your Java alternatives in a Terminal:
/usr/sbin/update-alternatives --config java 

Make sure that sun java 6 is selected as default.



I tried it and got:
> $ /usr/sbin/update-alternatives --config java 

There are 5 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
*         1    /usr/lib/jvm/java-6-sun/jre/bin/java
          2    /usr/bin/gij-4.2
          3    /usr/bin/gij-4.1
 +        4    /usr/lib/jvm/java-6-openjdk/jre/bin/java
          5    /usr/lib/jvm/java-gcj/jre/bin/java

Press enter to keep the default[*], or type selection number: 


BTW what does the "+" mean?
What do I need to do to get it to work?
I use 8.04 on AMD64.

bye

Ronald

---

### Post by PmDematagoda on 2008-07-30
The + sign means that OpenJDK is selected over the default which is Sun Java according to the list. To use Sun Java, just execute the command and then enter 1 as the number. That should cause Ubuntu to use Sun Java.

---

### Post by ELMIT on 2008-07-30
Thanks, but that had no effect. The list remains exactly the same, no. 1 has a star and no 4 has a +

What can I do next?

---

### Post by PmDematagoda on 2008-07-30
Install galternatives with:-
```
sudo apt-get install galternatives
```

After that is installed, run the Alternatives Configurator in Applications>System Tools>Alternatives Configurator and then configure the java path using that.

---

### Post by ELMIT on 2008-07-31
Did not change a thing.
It is just a graphical interface now instead of a CL tool.

I am missing here something.

---

### Post by PmDematagoda on 2008-07-31
> **ELMIT said:**
> Did not change a thing.
It is just a graphical interface now instead of a CL tool.

I am missing here something.

Did you go to the Java section and try and select the Sun Java path?

---

### Post by ELMIT on 2008-07-31
1. I have installed it
2. Application/System Tools/ Alternatives Configurator
3. Scrolled down to java and select it
4. See/select in the right pan:
Choice  Priority  Options
-----------------------------------------------
  o   1061   /usr/lib/jvm/java-6-openjdk/jre/bin/java
  o   1042   /usr/lib/jvm/java-gcj/jre/bin/java
  **x**     63   /usr/lib/jvm/java-6-sun/jre/bin/java
  o     42   /usr/bin/gij-4.2
  o     41   /usr/bin/gij-4.1

5. closed it & open it (still elected)
6. try as non root again at the cl:
/usr/sbin/update-alternatives --config java 

There are 5 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
*         1    /usr/lib/jvm/java-6-sun/jre/bin/java
          2    /usr/bin/gij-4.2
          3    /usr/bin/gij-4.1
 +        4    /usr/lib/jvm/java-6-openjdk/jre/bin/java
          5    /usr/lib/jvm/java-gcj/jre/bin/java

Press enter to keep the default[*], or type selection number: 


Nothing changed! No success!

---

### Post by PmDematagoda on 2008-07-31
Run:-
```
java -version
```
what does that give?

---

### Post by ELMIT on 2008-07-31
$ java -version
java version "1.6.0_06"
Java(TM) SE Runtime Environment (build 1.6.0_06-b02)
Java HotSpot(TM) 64-Bit Server VM (build 10.0-b22, mixed mode)

---

### Post by PmDematagoda on 2008-07-31
> **ELMIT said:**
> $ java -version
java version "1.6.0_06"
Java(TM) SE Runtime Environment (build 1.6.0_06-b02)
Java HotSpot(TM) 64-Bit Server VM (build 10.0-b22, mixed mode)

According to that, you are using Sun Java. So that means that you should be able to use Java properly now.

---

### Post by DaveQB on 2009-03-24
I have the exact same situation as above.

the * means that's selected, so its all cool. I think thr + means that was the former default.

the issue I have is going to a page like [http://www.javatester.org/version.html](http://www.javatester.org/version.html) shows I have:

"Java version 1.4.2 from GNU Classpath"

What is the browser picking up to be using that version? I am not even sure which package that comes from even.

Anyone see that as well?

Thanks.

---

### Post by icecubetray on 2011-11-08
I know this post is a little old but people may be struggling trying to get this up and running like I have been.

I figured out how to get Yugma working for Ubuntu 11.10 on AMD64.

You need to install ia32-sun-java6-bin from synaptic package manager which installs the 32bit Sun JRE.

Then you need to use
$ /usr/sbin/update-alternatives --config java

 to change to the ia32-sun-java6-bin

this will get Yugma up and running under the 64bit environment.

:P

---

### Post by masgeeks on 2011-11-29
Superb...!!!  Thanks so much...!!!  Did the trick, just what I needed...!!!  :o

---

