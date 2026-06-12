---
title: "Java won't compile"
date: 2008-07-19
forum: General Help
---

### Post by PoopLoops on 2008-07-19
I have no idea where to post this, sorry.  I looked over the different forums and I couldn't find a place for this.

I'm a fairly new Linux/Ubuntu user, only about 2 months now and I'll be taking a Java class.  It's a 2nd quarter Java class and I've only ever had C/C++ and some FORTRAN, so I decided to play around with Java to get used to the syntax and stuff.

Anyway, I can't compile anything right now.  So this is what I do, I make a file called "HelloWorld.java", with the following:

```
public class HelloWorld {
    public static void main(String[] args) {
        System.out.println("Hello, World!");
    }
}
```

and then compile and this is what I get:

```
tomek@tomek-laptop:~/Desktop$ javac HellowWorld.java 
HellowWorld.java:1: class HelloWorld is public, should be declared in a file named HelloWorld.java
public class HelloWorld {
       ^
1 error
tomek@tomek-laptop:~/Desktop$ 
```

Now, here is my java version:

```
tomek@tomek-laptop:~/Desktop$ java -version
java version "1.6.0_06"
Java(TM) SE Runtime Environment (build 1.6.0_06-b02)
Java HotSpot(TM) Server VM (build 10.0-b22, mixed mode)
tomek@tomek-laptop:~/Desktop$ 

```

So I don't know what I need to do.  I'm using Ubuntu 8.04 HH.

---

### Post by jamesdcarroll on 2008-07-19
I get the exact same return from java -version and I copy/pasted your code into a file, compiled, and ran it with no problem.  

What are you using to edit the file?  I used gedit.  Maybe there's some hidden character messing it up.

---

### Post by PoopLoops on 2008-07-19
I also use gedit.  No hidden characters that I can find.

---

### Post by jamesdcarroll on 2008-07-19
Rats!  :(

Have you considered getting Eclipse and trying it out there? Might be helpful for your class anyways.

---

### Post by PoopLoops on 2008-07-19
I'll try that.  I installed BlueJ but got confused and just quit.

BREAKING NEWS:  I'M AN IDIOT

I named the file Hello**w**World.java 

So it's weird that file names matter in Java, but I didn't follow directions. :(

---

