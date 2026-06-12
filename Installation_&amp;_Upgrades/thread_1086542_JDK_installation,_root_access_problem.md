---
title: "JDK installation, root access problem"
date: 2009-03-04
forum: Installation &amp; Upgrades
---

### Post by reis3k on 2009-03-04
Hello,

I downloaded latest JDK's bin to /usr/local gave the privilege of X to all users by executing "chmod +x" and extract bin there.

I modified /etc/profile like this (at the end of file looks like this)

```
export PATH

export JAVA_HOME="/usr/local/jdk1.6.0_12"
export JDK_HOME="${JAVA_HOME}"
export PATH="${JAVA_HOME}/bin:${PATH}"

umask 022
```

When I run the command "java -version", it works and shows the version on a terminal entered by my user privileges. It also works when I enter X with root account privileges.

BUT it doesn't work when I enter as a root from the terminal window which is run on X on my user privilege.

I would be glad if you suggest some help, and I also be glad if someone tell me the meanings of that PATH's stuff escpecially the last two line 

export JDK_HOME="${JAVA_HOME}"
export PATH="${JAVA_HOME}/bin:${PATH}"

Is there any optimized way of doing this, because the first "export PATH" line looks like unnecessary .

Kind regards,

---

