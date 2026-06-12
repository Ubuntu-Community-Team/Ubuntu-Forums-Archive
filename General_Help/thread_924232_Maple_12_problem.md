---
title: "Maple 12 problem"
date: 2008-09-19
forum: General Help
---

### Post by vaazu on 2008-09-19
Hey.

I Have installed Maple 12, but cant get it to work. The program starts, then comes the tip window, which is OK, but the Main worksheet window will be blank, the mouse cursor changes it´s formations there like the hand with one finger and the text area cursor etc, but the window won´t show anything. Could it be java problem (I really don´t have any justifications for that, but i haven´t upgraded my java ever).

---

### Post by ju2wheels on 2008-09-19
Yes it is a java problem. The first thing is you want to make sure you have the latest sun java 6 installed correctly and that its set as the default system JVM. After that, you will need to edit the Maple start script, or at least thats what I did to get Maple 11 working. I have 12 but as of yet I have not installed it.

So basically I installed maple to /root/maple11, and had to modify /root/maple11/bin/maple using a text editor.

Once I had the file open, I added the following two lines:
```

#override the Maple JRE Bin so it points to sun java 6
MAPLE_JRE_BIN="/usr/lib/jvm/java-6-sun/bin/"

```

In my maple file that was placed at line number 355. The first piece of code after this assigns this variable to PATH.

So find the lines of code in the maple file that look something similar to this and place the above code right before it:

```

# Set the PATH so that Maple can find its various auxiliary programs.
if [ "$MAPLE_JRE_BIN" ]
then
    PATH="$MAPLE_JRE_BIN:$PATH"
fi
PATH="$MAPLE/$MAPLE_SYS_BIN:$PATH"
export PATH

```

Also be aware that even if you install it to /root you do not need to run it using sudo for a regular user as running /root/mape11/bin/xmaple by itself will start it correctly.

---

### Post by alexeyhurricane on 2008-11-04
great man , you saved UBUNTU on my pc

---

### Post by xubis on 2008-11-19
Thanks!

---

### Post by rat_poison on 2008-11-24
In order to generalise the above solution, for any location where java is placed on your system, you can replace the code below.
> MAPLE_JRE_BIN="/usr/lib/jvm/java-6-sun/bin/"

First, find out where your java is. Fire up a terminal and type
```
$ which java
```

This will show you where is your java bin.
For example, in my system, this is what came up:

```
%%%%##@!@#$!@$:~$ which java
/usr/bin/java

```

So, I replaced > MAPLE_JRE_BIN="/usr/lib/jvm/java-6-sun/bin/"
with
```
MAPLE_JRE_BIN="/usr/bin/"
```

You can then place links in your /usr/local/bin/ to facilitate executing maple or xmaple.

---

### Post by Fhernd on 2009-03-13
Hi!

Thanks for solution **ju2wheels**, and the **rat_poison** for the improved sol. I had to re-installed Maple 12 (changing the installation folder), but that did not sol. the problem.

Now, I can work with Maple 12 to solve Math problems.

Bye!

---

### Post by las.leandro on 2009-04-07
Thanks! It worked for me too!! :guitar:

---

