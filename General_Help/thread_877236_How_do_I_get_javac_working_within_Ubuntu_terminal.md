---
title: "How do I get javac working within Ubuntu terminal?"
date: 2008-08-01
forum: General Help
---

### Post by hamofgrey on 2008-08-01
Hi,

I'm fairly new to Ubuntu, I know the basic commands and rough structure of the file system. I've been programming Java and other bits and bobs for a year now and have recently migrated from Windows.

Now the problem:

I wish to be able to run the javac compiler and java commands within terminal. Yet have no idea how I am supposed to do this?

Within Windows I set the enviromental variables up and off I went with command prompt "java" and "java" commands. All advise and directions on tutorials would be most helpful.

I downloaded and installed my java jdk from the sun website. Then installed the .bin file to the following directory:-

~/Java/jdk1.6.0.07

I also installed Netbeans 6.1 IDE aswell, but i want to be able to use a text editor to create programs.

Thankyou for any help or guidance provided! :-)

---

### Post by TreeFinger on 2008-08-01
I think if you just installed jdk from repositories it would set up the environment variable for you. try uninstalling and then installing from the ubuntu repositories.

or, wait for an answer from a more intelligent person :)

---

### Post by hamofgrey on 2008-08-01
I have read about that not working somewhere but there is so much stuff out there on the net you just don't know what is true or false or just plan silly! lol

Hmm...that could be an idea.

Ideally I want to be able to set up the terminal myself (with the help of someone who is brilliant *nudge nudge*, as I only want myself as a user to be able to mess around with Java. Unless this can be done through the repositories?

Furthermore how would one uninstall a program from Ubuntu if they have not installed using synaptic? As there are a load of directories and rubbish that is often created in a number of places by programs.

Thanks for the amazingly quick response :-)

Anyother help by anyone else would be gr8 aswell!

---

### Post by michael_1234 on 2008-08-01
I use Sun's JDK on Ubuntu myself, along with Netbeans, and also do command-line programming & compiling as well.  (I can't comment on the JDK installed via the package manager.)

So, you've got the Sun JDK already installed -- which, as you probably discovered, was quite trivial: run the self-extracting binary into a directory of your choosing.  For other's referece, you can download that here: [http://java.sun.com/javase/downloads](http://java.sun.com/javase/downloads)

Even on non-Ubuntu sytems (ie, non-Debian systems) I have been running the jdk-6u7-linux-i586.bin installer, *not* the RPM.   Once this is extracted, you can move this around your system wherever you want.  Eg, extract into ~/temp, and move to /opt/jdk1.6 or your solution is fine, too (a "home directory" installation).

Now, the setup is pretty much just like windows.  Assuming you do have your JDK in " ~/Java/jdk1.6.0.07", just set your JAVA_HOME to point to this dir (by convention, just like windows, many apps will look for this).

$ export JAVA_HOME=~/Java/jdk1.6.0.07

Then, add the "bin" directory to your PATH,

$ export PATH=$JAVA_HOME/bin:$PATH

And... try it:

$ java -version
... should show version...

$ javac -version
 ... should show version... older javac needs to run:  javac -J-version


To make sure Netbeans is using the correct JDK, you'll have to update either your PATH & JAVA_HOME for netbeans, or tell netbeans which jdk to use: use the --jdkhome <path> option when starting NetBeans.  ( [http://wiki.netbeans.org/FaqJdkHome](http://wiki.netbeans.org/FaqJdkHome) )

Then, if run apache ant or maven from the shell, & they'll pick up JAVA_HOME as well.  Just reset JAVA_HOME to a different JDK (and then use the above commands to reset the PATH) and you can also switch back & forth between jdk versions.

-m

---

### Post by Diabolis on 2008-08-01
It will be easier to just:
```
sudo apt-get install sun-java6-jdk
```

---

### Post by michael_1234 on 2008-08-01
> **Diabolis said:**
> It will be easier to just:
```
sudo apt-get install sun-java6-jdk
```

It would be easier, that's for sure.  Though, do you run multiple jdk's concurrently?  E.g.., I run my IDE under jdk1.6, but need to compile things (eg, under maven/ant) to jdk1.5, and have my own alises for switching my shell back & forth from jdk1.5 to 1.6 (and 1.4 if necessary).  

I thought about installing the packages, but I use basically these same aliases & symlink setup on redhat/centos, fedora, cygwin, and even solaris (by symbolic links, I mean a poor man's (or, simple man's) /etc/alternatives).

This is sounding more complicated than it has to be -- so, original poster, you can ignore this if you want -- but, working in multiple environments has become kind of important for java development (in the professional sphere, anyway, where I have to listen to people who insist on using older jvm's).  

Basically, I have:

$ env | grep JAVA
JAVA6_HOME=/opt/jdk1.6
JAVA5_HOME=/opt/jdk1.5
JAVA14_HOME=/opt/jdk1.4
JAVA_HOME=/opt/jdk1.6

So that I can just do...

$ java -version
java version "1.6.0_06"

$ type java5
java5 is aliased to `JAVA_HOME=$JAVA5_HOME bash'

$ java5

$ java -version
java version "1.5.0_15"
[I]   (work in java5 for a while, do a build, etc)
[/I]
$ exit

$ java -version
java version "1.6.0_06"


Then, of course, so everything still works when I update the jdk6 or jdk5 to the latest patch / rev / build, I use the traditional:

 /opt/jdk1.5 -> /opt/java/jdk1.5.0_15
 /opt/jdk1.6 -> /opt/java/jdk1.6.0_06


It's one of those things that probably should be updated with just using plain old packages, but since it's been working for me for (many, many) years, I've gotten used to it.  As mentioned, installing sun java via packages has been hit & miss over the years,  but maybe now it's do-able -- not sure if that's the case on all distro's (I'm very cross-platform).  I'd also like to start using jpackage for all my java apps, but haven't switched over to that yet, either.

-m

**(edited) notes**: 
  ...see these (slightly out of date) links if you're just running one version of java:
  [https://jdk-distros.dev.java.net/ubuntu.html](https://jdk-distros.dev.java.net/ubuntu.html)
  [https://jdk-distros.dev.java.net/ubuntu-dev.html](https://jdk-distros.dev.java.net/ubuntu-dev.html)

 ...if you want to switch default versions of java for the system, you can run the gui for "alternatives", galternatives: [http://packages.ubuntu.com/hardy/admin/galternatives](http://packages.ubuntu.com/hardy/admin/galternatives)

---

### Post by hamofgrey on 2008-08-02
Hi again,

I'm sorry for the late reply however I fell asleep. I have tried to update the JAVA_HOME variable without success. These are the steps which I undertook were :-

opened ~/.bashrc file with a text editor.

Added the following two lines at the bottom of the file. Then saved and closed it.

export JAVA_HOME=~/Java/jdk1.6.0.07
export PATH=$JAVA_HOME/bin:$PATH

on opening terminal i typed :

```
java -version
javac -version
```

However I have clearly made a mistake somewhere has I got the annoying error:

```
 javac
The program 'javac' can be found in the following packages:
 * java-gcj-compat-dev
 * jikes-sablevm
 * gcj-4.2
 * kaffe
 * openjdk-6-jdk
 * jikes-sun
 * ecj
 * j2sdk1.4
 * jikes-classpath
 * jikes-gij
 * gcj-4.1
 * sun-java5-jdk
 * jikes-kaffe
 * sun-java6-jdk
Try: apt-get install <selected package>
bash: javac: command not found
```

I'm not really sure where I went wrong. Have I made a silly mistake by presuming to edit the .bashrc in my home directory.

By the way I am most interested in the idea of a different JDK's being run on one system. I'm a Computer Science student and messing around with things like sounds way too tempting! Perhaps I could do with a simple how to guide or step by step run through.

By the way thanks for anyone who has posted something on this thread. I was always a little critical of Linux communities and forums but the responses have certainly made me reconsider. I always thought it was a case that a person should figure it out by deduction and using google.

---

### Post by geirha on 2008-08-02
Open a new shell and print out the values of the two variables you made 
```

echo $JAVA_HOME
echo $PATH

```
Do they reflect the changes you added to .bashrc?

---

### Post by hamofgrey on 2008-08-02
I've typed the commands into terminal these are the results


```
echo $JAVA_HOME
/home/graham/Java/jdk1.6.0.07

echo $PATH
/home/graham/Java/jdk1.6.0.07/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
```

This indicates that the paths have been set up correctly. As my Java JDK is installed into that location. However when I run javac -version or java -version I get the same error as before (below):

```

javac -version
The program 'javac' can be found in the following packages:
 * java-gcj-compat-dev
 * jikes-sablevm
 * gcj-4.2
 * kaffe
 * openjdk-6-jdk
 * jikes-sun
 * ecj
 * j2sdk1.4
 * jikes-classpath
 * jikes-gij
 * gcj-4.1
 * sun-java5-jdk
 * jikes-kaffe
 * sun-java6-jdk
Try: sudo apt-get install <selected package>
bash: javac: command not found
```

Any ideas?

---

### Post by geirha on 2008-08-02
It certainly looks right. You are sure the cases are correct? I.e. Java is with capital J and not lowercase?

Does this list the content of the bin-directory or give you an error?
```
ls /home/graham/Java/jdk1.6.0.07/bin
```

---

### Post by hamofgrey on 2008-08-02
Ah! How did I not spot that! I must be an idiot!

The JDK Home directory is : /home/graham/Java/jdk1.6.0_07/bin
So I sent up the JAVA_HOME variable up wrong. Doh!

It was set up for : JAVA_HOME=~/Java/jdk1.6.0.07
I have now set it up for: JAVA_HOME=/home/graham/Java/jdk1.6.0_07/bin

Although I believe I have another problem . I have edited the .bashrc file
so it the bottom end of it looks like this :
```

JAVA_HOME=/home/graham/Java/jdk1.6.0_07/bin
PATH=$JAVA_HOME/bin:$PATH
```

The results from the echo PATH and echo JAVA HOME are this now: 

```
echo $JAVA_HOME
/home/graham/Java/jdk1.6.0_07/bin

 echo $PATH
/home/graham/Java/jdk1.6.0_07/bin/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
```

But I still get this problem, when i type javac -version:
 ```
javac -version
The program 'javac' can be found in the following packages:
 * java-gcj-compat-dev
 * jikes-sablevm
 * gcj-4.2
 * kaffe
 * openjdk-6-jdk
 * jikes-sun
 * ecj
 * j2sdk1.4
 * jikes-classpath
 * jikes-gij
 * gcj-4.1
 * sun-java5-jdk
 * jikes-kaffe
 * sun-java6-jdk
Try: sudo apt-get install <selected package>
bash: javac: command not found
```

I know I installed Java correctly. It was simple, just so you know I downloaded the latest version off Sun's site. Downloaded the .bin file.
Then made executable with chmod +z (filename) then ran it. It installed fine into the home directory but I am still getting problems being able to use javac and java commands in terminal.

Netbeans 6.1 IDE is also installed and compiles and runs fine. I am confused! Thanks for your previous help on this matter :-)

---

### Post by nnamdi on 2008-08-02
hello you could install the compiler from your repository and also install netbeans IDE or ecllipse IDE which are in your repository too.

---

### Post by geirha on 2008-08-02
In that case, JAVA_HOME should be /home/graham/Java/jdk1.6.0_07 (without /bin).

---

### Post by hamofgrey on 2008-08-02
Just for other people who posted know, i thought that I would not install stuff from the repositories as I wanted to really learn and know how Ubuntu works. Plus they seem to install stuff all over the place and it makes it difficult to manager and track. Anyway...

HEY PRESTO! IT WORKS!!! THANKS FOR YOUR HELP! :-)

That is awesome! I'm half way there to getting Ubuntu to do everything I had done in Windows before. I like Ubuntu it's one hell of a lot faster than Windows. Although I do still think XP is a good OS. Anyway enough nit natter.

Thank you to everybody who has helped it's been so helpful.

---

### Post by Aditya Bhavaraju on 2010-05-22
Hi!
Thank you for documenting "how to make javac work in the terminal" 
was a life saver.I find this documentation better than that of sun even.Thanks a lot!

---

