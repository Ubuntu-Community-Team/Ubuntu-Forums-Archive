---
title: "Trouble running Frostwire"
date: 2008-10-08
forum: General Help
---

### Post by NuNn DaDdY on 2008-10-08
I recently installed Frostwire, however whenever I try to run it from the terminal I receive the following error:

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


But I have made sure my java is up to date so I'm unsure as to why I am receiving these messages.  Should I make a symbolic link to the directories Frostwire is trying to look in pointing the the actual directories?

---

### Post by Therion on 2008-10-08
Have you tried using the latest version of Frostwire?  Meaning the version that's on their homepage...  Some of the older versions of Frostwire had just such "java issues" as what you're describing.

---

### Post by NuNn DaDdY on 2008-10-08
I double checked by re-installing the newest stable version of both but I am still receiving the same errors.

---

### Post by Therion on 2008-10-08
Have you installed **ubuntu-restricted-extras** from the repo?  You may need the Iced Tea plugin and that's the easiest way I know of to install it.
Besides, if you haven't yet, you probably want to install it for other reasons.

---

### Post by NuNn DaDdY on 2008-10-08
I located a post on Frostwire's forum stating that a native version of Java comes with Hardy and this causes the mix up.  The fix for this is:

sudo update-java-alternatives -s java-6-sun


Thanks for your help though!

---

