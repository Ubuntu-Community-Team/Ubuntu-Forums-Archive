---
title: "Installing Latest Java"
date: 2008-07-17
forum: General Help
---

### Post by dstein on 2008-07-17
I am trying to install the latest version of Java. I am installing sun-java6-jre from the repositories. However, when I go to [http://www.java.com/en/download/installed.jsp?detect=jre&try=1](http://www.java.com/en/download/installed.jsp?detect=jre&try=1), the applet tells me that I am using an older version of Java.

How should I go about installing the latest version of Java. Ordinarily, I would not care, but I am trying to connect to my work computer, which seems to work through a java applet that requires the latest runtime environment.

Any help would be greatly appreciated. Thanks.

---

### Post by txcrackers on 2008-07-18
First, use the package-manager of your choice and remove **everything** that has to do with Java, except *java-common* and those packages that only mention Java as a sideline (like *dbus*). Then install *sun-java6-plugin* and it's dependencies. Then try your applet - the chances are extremely good that the version of Java 6 (release 6) available from the repositories is more than adequate for your needs.

If you still have problems, talk to the techs at work and ask them what the deal is. I sincerely doubt you need the absolutely newest version.

---

### Post by tinny on 2008-07-18
Install all of Java 6 (everything Java 6 related)

```

sudo apt-get install sun-java6*

```

Test what version of Java is being used by default.

```

java -version

```

Change what default Java version is being used

```

sudo update-alternatives --config java

```

Also, what browser are you using? Firefox 3?

---

