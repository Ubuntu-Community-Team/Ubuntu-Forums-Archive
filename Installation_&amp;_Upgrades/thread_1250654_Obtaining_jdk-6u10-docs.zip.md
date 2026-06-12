---
title: "Obtaining jdk-6u10-docs.zip"
date: 2009-08-26
forum: Installation &amp; Upgrades
---

### Post by jawinterb on 2009-08-26
Hi All,

I am new to this.

I am trying to install java doc, and I keep getting give this garbage message about having down load jdk-6u10-docs.zip and jdk-6u10-ja.zip from a SUN website.

I must have read over 100 a different posts and stuff on more than 10 forums and none of them actually got me to the point where I could actually get these files so i could follow the rest of the instructions.

I am now more than a little frustrated. Please send a link to these files.

Cheers
James

---

### Post by jacob.danner on 2009-08-26
I'm assuming you've already read the following and given it a try?
""" (Its in the details pane when you select sun-java6-docs using synaptic)
This package does not contain the Java Documentation
for the Java(TM) Development Kit (JDK).  The Java Documentation
(jdk-6-doc.zip) may be downloaded from
[http://java.sun.com/javase/downloads/](http://java.sun.com/javase/downloads/) and, if placed
in /tmp (with root.root ownership), this package will
install the Java Documentation with the corresponding JDK.

Note that the Japanese version of the documentation
(jdk-6-doc-ja.zip) may alternately be used.
"""

I went to
[http://java.sun.com/javase/downloads/index.jsp](http://java.sun.com/javase/downloads/index.jsp)
and scrolled down the page to Java SE 6 documentation then clicked the download link. 
After making the required selections on the next couple of screens I was able to download the zip and after placing it in /tmp as root the package installed correctly.

HTH

---

### Post by jawinterb on 2009-08-26
Cheers.. that worked fine.
I could have sworn that i went there and didn't find it...

On well!!

Thanks!

---

### Post by upwinger on 2009-10-07
Im having the same issue but I dont understand how to
"placing it in /tmp as root"

Please help:confused:

---

### Post by Mighty_Joe on 2009-10-08
I posted step-by-step instructions [here]("http://ubuntuforums.org/showpost.php?p=7747882&postcount=6")

---

### Post by fabitencourt on 2009-10-09
:KS Thanks Joe, I hope it will solve my updating problem too. Your explanation is perfect. Could you just explain to me what does the comand «chown» do ? 

> **Mighty_Joe said:**
> I posted step-by-step instructions [here]("http://ubuntuforums.org/showpost.php?p=7747882&postcount=6")

---

### Post by Mighty_Joe on 2009-10-09
> **fabitencourt said:**
> :KS Thanks Joe, I hope it will solve my updating problem too. Your explanation is perfect. Could you just explain to me what does the comand «chown» do ?

You can type "man <command>" to get an explanation of a command ("man" is short for manual).  The man page for chown is [online too]("http://www.manpagez.com/man/8/chown/")

---

### Post by Richiegs on 2009-10-20
Would anyone tell me how to copy jdk-6u10-docs.zip  to the /tmp directory?
I already downloaded jdk-6u10-docs.zip on the desktop. I appreciate any help.

---

### Post by Mighty_Joe on 2009-10-20
> **Richiegs said:**
> Would anyone tell me how to copy jdk-6u10-docs.zip  to the /tmp directory?


When you open a terminal, it usually starts in your home directory. From your home directory the command would be:
```
sudo cp Desktop/jdk-6u10-docs.zip /tmp
```

---

### Post by davidbilla on 2009-10-30
Hi, I have the same problem but I would like to get the irritating installation failure messages out of the way without installing sun-java6-doc. In short, I want to stop Synaptic from trying to install javadoc whenever I try to install anything else. How can I go about doing it?

---

### Post by Flimm on 2010-04-07
The version on Sun's website is jdk-6u18-docs.zip, does it matter?

---

### Post by Mighty_Joe on 2010-04-08
Probably not, as the file is just a zipped-up bunch of HTML documentation.  It looks like at least [one person]("http://ubuntuforums.org/showpost.php?p=8888712&postcount=17")has had success renaming the documentation file to the expected version and installing.  There shouldn't be any large changes to the API in a minor version update.

---

### Post by shOt1436 on 2010-09-27
Hi, i am new to ubuntu., i hav downloaded the file jdk-6u10-docs.zip and copied it to the /tmp directory. Then if i use the command:

sudo chown root jdk-6u10-docs.zip

I am getting the error:

chown: cannot access `jdk-6u10-docs.zip': No such file or directory

Plz tell me what to do. Thanx

---

### Post by mal99 on 2010-09-30
You're probably in the wrong directory, the "cd" command will bring you into the desired directory.
So just enter
```
cd /tmp
```into the terminal before installing.

---

