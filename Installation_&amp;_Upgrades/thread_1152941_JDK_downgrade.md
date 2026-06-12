---
title: "JDK downgrade"
date: 2009-05-08
forum: Installation &amp; Upgrades
---

### Post by doug804 on 2009-05-08
I'm completely new to Linux so please bare with me if this has been previously covered.

I have an application which has been developed in a UNIX environment, which one I'm not sure, and programmed using java version 1.5.

I have Ubuntu 8.10 and installed jdk using sudo apt-get install ubuntu-restricted-extras.

This has installed OPENjdk version 1.6

When I tried to compile the program I am getting 70 compile time warnings.

I have compiled the program in Windows and I don't get these warnings, as I am using java version 1.5.


How can I downgrade my java version?

---

### Post by taurus on 2009-05-08
One way is go into System -> Administration -> Synaptic and Search for java.  Then, remove the version that you don't want and install the one you want.

---

### Post by doug804 on 2009-05-08
Thanks taurus. 
I have gone through that, and installed sun-java5-jdk and have removed open-jdk.

I am still on:
java -version
java version "1.6.0_0"
IcedTea6 1.3.1 (6b12-0ubuntu6.4) Runtime Environment (build 1.6.0_0-b12)
OpenJDK Client VM (build 1.6.0_0-b12, mixed mode, sharing)
.

If I removed OpenJDK how does it still show up?

---

### Post by taurus on 2009-05-08
Reboot and see which version you are running then.

```
java -version
```
Otherwise, see if the one you just installed is on the list.

```
sudo update-alternatives --config java
```

---

### Post by doug804 on 2009-05-08
Sweet!
 
That's done it.
 
Thanks for the help.

---

