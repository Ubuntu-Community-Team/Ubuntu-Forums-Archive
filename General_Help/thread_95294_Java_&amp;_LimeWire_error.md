---
title: "Java &amp; LimeWire error"
date: 2005-11-26
forum: General Help
---

### Post by stealthdevil on 2005-11-26
Ive been trying for a long time now to install LimeWire. Ive followed the guide from ubuntuguide.org as well as search these forums.

I installed Java, and then installed LimeWire 4.9. But when i try to run LimeWire i get a bunch of errors of how java isnt installed or the wrong version is installed. But im using the latest version of Java from Sun. I even downloaded and installed the SDK as well but still no luck.

Here is the output from the console:

root@voyager-linux:/home/rameen# dpkg -i jre_1.5.0_05-1_i386.deb
(Reading database ... 60928 files and directories currently installed.)
Preparing to replace jre 1.5.0_05-1 (using jre_1.5.0_05-1_i386.deb) ...
Unpacking replacement jre ...
Setting up jre (1.5.0_05-1) ...
root@voyager-linux:/home/rameen# limewire
Starting LimeWire...
Java exec found in PATH. Verifying...
OOPS, you don't seem to have a valid JRE. LimeWire works best with Sun JRE available at [http://www.java.com](http://www.java.com)
OOPS, unable to locate java exec in  /usr/lib/  hierarchy
You need to upgrade to JRE 1.4.x or newer from [http://www.java.com](http://www.java.com)
Java exec found in  /usr/java/jre1.5.0_05/bin/
OOPS, you don't seem to have a valid JRE. LimeWire works best with Sun JRE available at [http://www.java.com](http://www.java.com)  [/usr/java/jre1.5.0_05/bin/java = Error]
You need to upgrade to JRE 1.4.x or newer from [http://www.java.com](http://www.java.com)
OOPS, unable to locate java exec in  /usr/java/  hierarchy
You need to upgrade to JRE 1.4.x or newer from [http://www.java.com](http://www.java.com)
ls: /opt/j*: No such file or directory
OOPS, unable to locate java exec in  /opt/  hierarchy
You need to upgrade to JRE 1.4.x or newer from [http://www.java.com](http://www.java.com)
root@voyager-linux:/home/rameen#


Any help would be much appreciated, thanks...

Rameen

---

### Post by akiro.yamamoto on 2005-11-26
Hiyah :smile:
This should help you specify which version of java will be the default:

CODE:
sudo update-alternatives --config java

And then just select which version you want as default.....

Regards

---

### Post by stealthdevil on 2005-11-26
That didnt fix the problem. I already have Sun Java selected as default for Java.

---

### Post by akiro.yamamoto on 2005-11-26
Ok,
I'm going to try to install limewire now.....


I'LL BE BACK!

---

### Post by woopud on 2005-11-26
Just use Automatix [http://ubuntuforums.org/showthread.php?t=66563](http://ubuntuforums.org/showthread.php?t=66563) and all your problems will be solved.

Bert

---

### Post by akiro.yamamoto on 2005-11-26
OK 
Now YMMV....
Here's what I did to get it to work....
1) Download the rpm limewire version.
2) Install alien (should be on the install cd).
3) Use alien to convert the rpm file to a deb file
4) Install the newly created deb file
5) Type "limewire" in a terminal or use the run command.
6) Enjoy.
Now this process has been tested on Ubuntu 5.10 with sun java installed and selected as the default java (not blackdown version). No other tweaks are needed.
Hope this helps...
Regards
:smile:

---

### Post by `GooZ´ on 2005-11-26
@akiro.yamamoto
exactly what I did :-)

---

### Post by stealthdevil on 2005-11-26
That's exactly what I did as well. Anybody know what the errors mean and how to fix them?

I had this problem wit Ubuntu 5.04. I also tried it on a fresh install of 5.10 and still got the same problems...

---

