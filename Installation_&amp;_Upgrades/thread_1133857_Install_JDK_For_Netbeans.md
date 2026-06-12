---
title: "Install JDK For Netbeans"
date: 2009-04-23
forum: Installation &amp; Upgrades
---

### Post by ralaxmyself on 2009-04-23
I am a green hand to linux, and want to learn to use ubuntu.

I use Netbeans to develop python program. So i download EA, when i install EA, it promt me to install JDK.

So i download the jdk-6u13-linux-i586.bin from java.
i use the following commands to install the jdk.

chmod 755 /home/ralax/Documents/jdk-6u13-linux-i586.bin
sudo /home/ralax/Documents/jdk-6u13-linux-i586.bin

then install successed. The location is /home/ralax/jdk1.6.0_13

then i install the Netbeans, but it stills can not find the JVM,

I also use 
export JAVA_HOME=/home/ralax/jdk1.6.0_13
export PATH=$PATH:JAVA_HOME/bin

but it makes no sense.

I don't know how the system knows the jvm location, what should i do to resolve the problem?

And if i want to uninstall the JDK i have installed, what should i do?

Any one who can help me, please comment here!

My english is not very well. Hope i have explained clearly!

Thanks very much!

Ralax.

---

### Post by Tobi-fp on 2009-04-23
Why not just install the netbeans from the repositories?

---

### Post by ralaxmyself on 2009-04-23
> **Tobi-fp said:**
> Why not just install the netbeans from the repositories?
because i am green hand to linux.i
i do not know how to install.

---

### Post by ralaxmyself on 2009-04-25
I get the solution:

sh  /home/ralax/Documents/netbeans/netbeans-6.5.1-ml-ruby-linux.sh --javahome /home/ralax/jdk1.6.0_13

add argument --javahome

---

