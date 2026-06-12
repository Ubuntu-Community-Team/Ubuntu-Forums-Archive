---
title: "Help with frostwire and isntalling jre"
date: 2008-09-04
forum: General Help
---

### Post by wisedrunkard on 2008-09-04
When I try to run frostwire in the terminal the following comes up:

Starting FrostWire...
Java exec found in PATH. Verifying...
OOPS, you don't seem to have a valid JRE. FrostWire works best with Sun JRE available at [http://www.java.com](http://www.java.com)
OOPS, unable to locate java exec in  /usr/lib/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
ls: cannot access /usr/java/j*: No such file or directory
OOPS, unable to locate java exec in  /usr/java/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
ls: cannot access /opt/j*: No such file or directory
OOPS, unable to locate java exec in  /opt/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)

I've tried installing Jre but can't seem to get it right. How can I upgrade Jre and get frostwire running again?!

Thanks in advance.

---

### Post by Denestria on 2008-09-04
If you have 1.5 or higher installed and Frostwire is still giving this message...

What I had to do when I was getting this message was to create a symlink in /usr/lib to java.
```

sudo ln -s /usr/lib/jvm/java-6-sun /usr/lib/java

```

Oh, forgot to mention...

You'll need to change the command to whatever version of java you have installed (java-5-sun).

---

### Post by fooman on 2008-09-04
did java install properly? ...try running this command in a terminal:

```
java -version
```

if its installed,  you should see output like this:

```
java version "1.6.0_07"
Java(TM) SE Runtime Environment (build 1.6.0_07-b06)
Java HotSpot(TM) Server VM (build 10.0-b23, mixed mode)
```

if its not installed,  try it from the repositories.  you may need to enable the multiverse repos first, so....go to system > administration > synaptic package manager

when synaptic opens, go in the toolbar to settings > repositories

under the ubuntu software tab,  make sure that the first 4 choices are checked off (main - universe - restricted - multiverse). click on the close button.  you will see a box telling you that the repos have changed...close that box as well.  click the "mark all upgrades" button to update the new repositories you just enabled.

then close synaptic, open a terminal and type or copy/paste the following:

```
sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts
```

for jre6,  if you want jre5...then try this one instead:

```
sudo apt-get install sun-java5-jre sun-java5-plugin sun-java5-fonts
```

hope that helps.

---

### Post by wisedrunkard on 2008-09-04
OK, for those having the same problem, the solution was in the following command:

sudo update-java-alternatives -s java-6-sun

---

