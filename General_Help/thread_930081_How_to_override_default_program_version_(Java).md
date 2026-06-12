---
title: "How to override default program version (Java)"
date: 2008-09-25
forum: General Help
---

### Post by mrmorris on 2008-09-25
I wanted to use a more recent version of an application (in this case Java6u10 rather than the update 6 found in latest Ubuntu rep). Even though I remove all existing versions of Java, set JAVA_HOME, JDK_HOME and put the Java /bin directory in the PATH, I still get the following when running java from the commandline:

The program 'java' can be found in the following packages:
 * java-gcj-compat-headless
 * openjdk-6-jre-headless
 * cacao
 * j2re1.4
 * kaffe
 * jamvm
 * gij-4.1
 * gij-4.2
 * sablevm
Try: sudo apt-get install <selected package>

These hints from the package manager are usually nice, but in this case, I really just want to "hit" the custom java executable I have placed. What mechanism do I have to override/tweak in Ubuntu 8.04 in order to accomplish this?

---

### Post by Pelham123 on 2008-09-25
When you type:

```
whereis java
```

What do you get?

---

### Post by gpredrag on 2008-09-25
Ubuntu and Debian have excellent tool for something like this.
First install back regular Ubuntu's java so package management system knows that there exist java on the system if some other package depends on it. 
Put your java where the Ubuntu java is in /usr/lib/java
You might like to check update-alternatives and update-java-alternatives.

---

### Post by panayk on 2008-09-25
If you install your java in /usr/local (e.g. /usr/local/bin) it should override the version in /usr/bin

---

### Post by mrmorris on 2008-09-26
> **Pelham123 said:**
> When you type:

```
whereis java
```

What do you get?

Then I get:

java: /etc/java /usr/share/java

---

### Post by SeanHodges on 2008-09-26
> **mrmorris said:**
> The program 'java' can be found in the following packages:
 * java-gcj-compat-headless
 * openjdk-6-jre-headless
 * cacao
 * j2re1.4
 * kaffe
 * jamvm
 * gij-4.1
 * gij-4.2
 * sablevm
Try: sudo apt-get install <selected package>

This message is basically a sugar-coated way of saying "bash: java: Command not found", treat it as meaning this. You can turn off this message temporarily by doing:

```
sudo mv /usr/lib/command-not-found /usr/lib/command-not-found-disabled
```

Try typing "java" after this and you'll see the normal "command not found" response, you can turn it back on afterwards by renaming it back:

```
sudo mv /usr/lib/command-not-found-disabled /usr/lib/command-not-found
```


Type "which java" and see if it returns the path to your java binary, if it doesn't then your PATH is wrong somehow.

---

