---
title: "source for j2re?"
date: 2005-11-03
forum: General Help
---

### Post by pickarooney on 2005-11-03
I'm trying to install java (to be honest I don't understand the difference between java, j2re, jsdk etc.) following the instructions [here](http://ubuntuguide.org/#jre).

I get this:
```

sudo apt-get install sun-j2re1.5
Password:
Reading package lists... Done
Building dependency tree... Done
Package sun-j2re1.5 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-j2re1.5 has no installation candidate

```

Can anyone help me find the right package?

---

### Post by Moonbuzz on 2005-11-03
From the top, then.

Sun Java is not available from the repositories, being proprietary of Sun. You can install a different version of Java called Blackdown Java. You can get it by doing ```
sudo apt-get install j2re1.4
```.

If you really want to get Sun Java, you should follow [. You should refer to the new [url="http://help.ubuntu.com/starterguide/C/faqguide-all.html"]Starter Guide]("https://wiki.ubuntu.com/RestrictedFormats#head-55315677ab8f9890825549fa2ecebdde4bc68087"these instructions[/url), now that ubuntuguide.com is dated.

As for your other question, Java is the programming language which is used in many different application. The language is multi-platform, meaning the same code can be executed on Linux, Windows, Mac, and others. This is made possible through the Java Runtime Environment (JRE) which intermediate between the Java class and the Operating System. To develop and create Java application, like with any other language, you need the Software Development Kit (SDK), or Java Development Kit (JDK) - Both are the same. While it includes the latest JRE, don't bother with it if you're not planning on writing Java code.

---

### Post by pickarooney on 2005-11-03
Perfect, thank you :)

---

