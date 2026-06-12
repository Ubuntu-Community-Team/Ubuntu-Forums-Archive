---
title: "Upgrading Java to 1.6.0_11"
date: 2009-01-14
forum: Installation &amp; Upgrades
---

### Post by JavaKrypt on 2009-01-14
This is starting to annoy me.
I've followed the Java website on how to install the updated version of Java, but that site is so ----ing outdated it's really surprising. I used it as a guide, though it basically did nothing but annoy me even more.
So I downloaded Java from the site, ran all the commands, got the thing to install, done the last part of copying the files over from the ffjcext.zip file, though still no luck - it wont work.
I run **java -version** and it comes back with: > [I]java version "1.6.0_0"
IcedTea6 1.3.1 (6b12-0ubuntu6) Runtime Environment (build 1.6.0_0-b12)
OpenJDK Client VM (build 1.6.0_0-b12, mixed mode, sharing)
[/I]

So it's not updated. What I'm trying to update it to is 1.6.0_11.

Here's what I ran, and my output. (PS: I copied the java installation to usr/lib/java

> 
*_(I already logged in as root btw, through su.)_*

cd /
_*(Note: I never used wget, I used firefox and saved the bin file over at usr/lib/java through the filesystem view. It was easier.)*_
chmod 777 /usr/lib/java/jre-6u11-linux-i586.bin
./jre-6u11-linux-i586.bin
*_(It then extracts the files like so, here's just a snippet.)_*
creating: jre1.6.0_11/lib/deploy/                                            
inflating: jre1.6.0_11/lib/deploy/ffjcext.zip                                 
inflating: jre1.6.0_11/lib/deploy/splash.gif                                  
inflating: jre1.6.0_11/lib/deploy/messages.properties                         
done.

cd /usr/lib/firefox/plugins
ln -s /usr/lib/java/jre1.6.0_11/plugin/i1386/ns7/libjavaplugin_oji.so
ln: creating symbolic link `./libjavaplugin_oji.so': File exists
cd /
cd /usr/lib/firefox/extensions
unzip /usr/lib/java/jre1.6.0_11/lib/deploy/ffjcext.zip

Archive:  /usr/lib/java/jre1.6.0_11/lib/deploy/ffjcext.zip            
creating: {CAFEEFAC-0016-0000-0011-ABCDEFFEDCBA}/                  
extracting: {CAFEEFAC-0016-0000-0011-ABCDEFFEDCBA}/chrome.manifest   
creating: {CAFEEFAC-0016-0000-0011-ABCDEFFEDCBA}/chrome/           
creating: {CAFEEFAC-0016-0000-0011-ABCDEFFEDCBA}/chrome/content/   
creating: {CAFEEFAC-0016-0000-0011-ABCDEFFEDCBA}/chrome/content/ffjcext/
extracting: {CAFEEFAC-0016-0000-0011-ABCDEFFEDCBA}/chrome/content/ffjcext/ffjcext.js
_(*It does more than this, it's just a snippet.)*_

*_( I then go to firefox after enabling, installing the extenstions etc, and restarting firefox and enter **about:plugins** - it doesn't show up. not surprising... so I check my ver in terminal.)_*

java -version
java version "1.6.0_0"
IcedTea6 1.3.1 (6b12-0ubuntu6) Runtime Environment (build 1.6.0_0-b12)
OpenJDK Client VM (build 1.6.0_0-b12, mixed mode, sharing)


so now I'm at a loose end, I'm stuck. I hate asking for help when it comes to things like this but I give in. Anyone know what I'm doing wrong, or not doing at all?

---

### Post by taurus on 2009-01-14
Run this command from a terminal and see if the latest version is on the list and whether it is the default version.

```
sudo update-alternatives -config java
```

---

### Post by JavaKrypt on 2009-01-14
> stephen@stephen:~$ sudo update-alternatives -config java
[sudo] password for stephen:
update-alternatives: **unknown argument** `-config'
stephen@stephen:~$


:S? I checked these forums before and I was told in one of the threads to use the same command, yet it never works.

---

### Post by JavaKrypt on 2009-01-18
Bump. Can anyone help, please?

---

### Post by taurus on 2009-01-18
```
sudo update-alternatives --config java
```

---

### Post by JavaKrypt on 2009-01-18
This is what I get,

```
root@stephen:/# update-alternatives --config java

There is only 1 program which provides java
(/usr/lib/jvm/java-6-openjdk/jre/bin/java). Nothing to configure.
root@stephen:/#

```

---

### Post by taurus on 2009-01-18
What's the output of this command?

```
ls -la /usr/lib/java/jre1.6.0_11/bin
```

---

### Post by JavaKrypt on 2009-01-19
> root@stephen:/# ls -la /usr/lib/java/jre1.6.0_11/bin
total 756
drwxr-xr-x 2 root root   4096 2008-11-10 11:41 .
drwxr-xr-x 8 root root   4096 2009-01-14 04:46 ..
lrwxrwxrwx 1 root root     10 2009-01-14 04:46 ControlPanel -> ./jcontrol
-rwxr-xr-x 1 root root  47308 2008-11-10 09:57 java
-rwxr-xr-x 1 root root  25634 2008-11-10 10:00 java_vm
-rwxr-xr-x 1 root root  83952 2008-11-10 10:00 javaws
-rwxr-xr-x 1 root root   6347 2008-11-10 10:00 jcontrol
-rwxr-xr-x 1 root root  47447 2008-11-10 09:57 keytool
-rwxr-xr-x 1 root root  47679 2008-11-10 09:57 orbd
-rwxr-xr-x 1 root root  47515 2008-11-10 09:57 pack200
-rwxr-xr-x 1 root root  47807 2008-11-10 09:57 policytool
-rwxr-xr-x 1 root root  47447 2008-11-10 09:57 rmid
-rwxr-xr-x 1 root root  47447 2008-11-10 09:57 rmiregistry
-rwxr-xr-x 1 root root  47475 2008-11-10 09:57 servertool
-rwxr-xr-x 1 root root  47679 2008-11-10 09:57 tnameserv
-rwxr-xr-x 1 root root 189274 2008-11-10 09:57 unpack200
root@stephen:/#


.

---

### Post by taurus on 2009-01-19
What is the output when you run this command from a terminal?

```
/usr/lib/java/jre1.6.0_11/bin/java -version
```
You can go into synaptic and remove the _openjdk_ version or you can create a link to the new version.

```
sudo ln -s /usr/lib/java/jre1.6.0_11/bin/java  /usr/local/bin/java
```

---

### Post by JavaKrypt on 2009-01-19
Here's the output;

> 
root@stephen:/# /usr/lib/java/jre1.6.0_11/bin/java -version
java version "1.6.0_11"
Java(TM) SE Runtime Environment (build 1.6.0_11-b03)
Java HotSpot(TM) Client VM (build 11.0-b16, mixed mode, sharing)


I do the 2nd one, which I've already tried, though Java still doesn't work.
Appreciate the help :)

---

### Post by taurus on 2009-01-19
Run this command again and see if the Sun's version is on the list now.

```
update-alternatives --config java
```

---

### Post by JavaKrypt on 2009-01-19
Nope, I have no idea why :l

> root@stephen:/# update-alternatives --config java

There is only 1 program which provides java
(/usr/lib/jvm/java-6-openjdk/jre/bin/java). Nothing to configure.

---

### Post by taurus on 2009-01-19
Any reason why you don't want to install the version from the repos?

```
sudo apt-get update
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
```
It's probably a good idea to remove the version that you installed by hand in /usr/lib/java/jre1.6.0_11.

```
sudo rm /usr/local/bin/java
```

---

### Post by JavaKrypt on 2009-01-19
There we go. It's installed v6.0_10.
Thanks for the help :)

---

### Post by blue13130 on 2009-01-19
Here is my personal method of installing the updated java version in Ubuntu 8.04.1.
Edit - This is to install the 32 bit java plugin on a 32 bit Ubuntu install.  To install 64 bit java plugin in 64 bit Ubuntu read my post later on in this thread.

1. Remove all prexisting java packages.  Remove all sun-java* packages and openjdk packages.

2. Download from the java site the file jre-6u11-linux-i586.bin

3. Extract and move the resulting directory to /opt
```
cd /path/to/downloadedjavafile
sh jre-6u11-linux-i586.bin
sudo mv jre1.6.0_11 /opt
```

4. Create firefox links for plugin
first remove all previous made links using that you made with ls

```
cd /usr/lib/firefox-addons/plugins
sudo ln -s /opt/jre1.6.0_11/plugin/i386/ns7/libjavaplugin_oji.so .
```

5. Create java.sh profile file so that it can be found every time machine starts

```
cd /etc/profile.d
```
create a file named java.sh with the following two lines:
```
export JRE_HOME=/opt/jre1.6.0_11
export PATH=$JRE_HOME/bin:$PATH
```

save it so that its owner and group are root and it is read only
```
sanjay@acer:/etc/profile.d$ ls -l java.sh 
-r--r--r-- 1 root root 65 2009-01-20 20:28 java.sh
```


6. Source the java.sh file then check version
```
sanjay@acer:~$ source /etc/profile.d/java.sh
sanjay@acer:~$ java -version
     java version "1.6.0_11"
     Java(TM) SE Runtime Environment (build 1.6.0_11-b03)
     Java HotSpot(TM) Client VM (build 11.0-b16, mixed mode, sharing)
sanjay@acer:~$ 

```

7. Restart firefox and check that the plugin works

8. Reboot and run java -version to make sure that it works after reboot

Hope this works for you!

---

### Post by MadL on 2009-01-26
On a somewhat related note...

My system (Hardy Heron) is currently stuck on Java Version 1.6.0_07, and both Synaptic and apt-get insist I have the latest version available.

This is what I get with "update-alternatives --config java":

>   Selection    Alternative
-----------------------------------------------
          1    /usr/bin/gij-4.1
*+        2    /usr/lib/jvm/java-6-sun/jre/bin/java
          3    /usr/bin/gij-4.2

---

### Post by blue13130 on 2009-01-26
> **MadL said:**
> On a somewhat related note...

My system (Hardy Heron) is currently stuck on Java Version 1.6.0_07, and both Synaptic and apt-get insist I have the latest version available.

This is what I get with "update-alternatives --config java":

That happens because 1.6.0_07 is the latest available from the repos for Heron.  You can remove all the java packages and use my method to download the latest java release from the website and install it yourself.

If things don't work out you can just reinstall the java packages from the repo.

---

### Post by klein de usa on 2009-01-30
hi 
i was following blue13130's instructions of how he installs the latest java and i got all the way to :

-r--r--r-- 1 root root 65 2008-12-21 18:19 java.sh

and my terminal is telling me :

klein@klein-hpdesktop:/etc/profile.d$ -r--r--r-- 1 root root 65 2008-12-21 18:19 java.sh
bash: -r--r--r--: command not found
 ive tried it several ways hopping it was a typo but i can't get it to work?            any ideas?

---

### Post by taurus on 2009-01-30
> **klein de usa said:**
> hi 
i was following blue13130's instructions of how he installs the latest java and i got all the way to :

-r--r--r-- 1 root root 65 2008-12-21 18:19 java.sh

and my terminal is telling me :

klein@klein-hpdesktop:/etc/profile.d$ -r--r--r-- 1 root root 65 2008-12-21 18:19 java.sh
bash: -r--r--r--: command not found
 ive tried it several ways hopping it was a typo but i can't get it to work?            any ideas?

You need to change the permission to include executable if you want to run it.

```
sudo chmod 755 /etc/profile.d/java.sh
ls -la /etc/profile.d/java.sh
```

---

### Post by klein de usa on 2009-01-30
thank you taurus

worked like a charm went to sun java free test page and it says i have 6.11 running

---

### Post by DeMus on 2009-01-30
> **blue13130 said:**
> That happens because 1.6.0_07 is the latest available from the repos for Heron.  You can remove all the java packages and use my method to download the latest java release from the website and install it yourself.

If things don't work out you can just reinstall the java packages from the repo.

I also followed your instructions to the end, where it says I have the right version installed. But when I go to the java.com page and check if I have Java it says I need extra plugins:
GCJ Webbrowser plugin and GCJ Webbrowser plugin (using open JDK)
Even when I install those, the page keeps telling me I need the two plugins.
When I install them using Synaptic the java.com pages tells me I have an outdated java version.
What do I have to do?

---

### Post by klein de usa on 2009-01-30
hi 
it worked fine untill i rebooted and now it is saying i'm running 6.10 again, am missing something?

---

### Post by blue13130 on 2009-01-30
> **klein de usa said:**
> hi 
i was following blue13130's instructions of how he installs the latest java and i got all the way to :

-r--r--r-- 1 root root 65 2008-12-21 18:19 java.sh

and my terminal is telling me :

klein@klein-hpdesktop:/etc/profile.d$ -r--r--r-- 1 root root 65 2008-12-21 18:19 java.sh
bash: -r--r--r--: command not found
 ive tried it several ways hopping it was a typo but i can't get it to work?            any ideas?

I am sorry to confuse you but that line was not meant to be a command, it is the ouput of the ls -l command so you can see the properties and owner of the java.sh file.  I believe for it to be read after each boot it has to be owned by root and be read only.

```
sanjay@acer:/etc/profile.d$ ls -l java.sh 
-r--r--r-- 1 root root 65 2009-01-20 20:28 java.sh
```

---

### Post by blue13130 on 2009-01-30
> **DeMus said:**
> I also followed your instructions to the end, where it says I have the right version installed. But when I go to the java.com page and check if I have Java it says I need extra plugins:
GCJ Webbrowser plugin and GCJ Webbrowser plugin (using open JDK)
Even when I install those, the page keeps telling me I need the two plugins.
When I install them using Synaptic the java.com pages tells me I have an outdated java version.
What do I have to do?

Are you using this on a 64 bit machine?  Java 1.6.0_11 will not work for a 64 bit OS as the plugin is only 32 bit.

To install java for 64 bit you need to download the file from this website:
[https://jdk6.dev.java.net/6uNea.html](https://jdk6.dev.java.net/6uNea.html)

The link to the file is this:
[http://www.java.net/download/jdk6/6u12/promoted/b03/binaries/jre-6u12-ea-bin-b03-linux-amd64-22_dec_2008.bin](http://www.java.net/download/jdk6/6u12/promoted/b03/binaries/jre-6u12-ea-bin-b03-linux-amd64-22_dec_2008.bin)

It is a prerelease of Java 1.6 update 12 which has a 64 bit plugin.

Extract the file and move the directory to /opt
```
sanjay@acer:~$ ls -l /opt/
total 12
drwxr-xr-x 8 sanjay sanjay 4096 2009-01-20 20:23 jre1.6.0_12
```

Create the link for the firefox plugin
```
cd /usr/lib/firefox-addons/plugins
sudo ln -s /opt/jre1.6.0_12/lib/amd64/libnpjp2.so .
sanjay@acer:/usr/lib/firefox-addons/plugins$ ls -l
total 9320
-rwxr-xr-x 1 sanjay sanjay 9526312 2008-12-10 12:13 libflashplayer.so
lrwxrwxrwx 1 root   root        38 2009-01-20 20:26 libnpjp2.so -> /opt/jre1.6.0_12/lib/amd64/libnpjp2.so
```

Create your java.sh file in /etc/profile.d to be like this
```
sanjay@acer:/etc/profile.d$ cat java.sh 
export JRE_HOME=/opt/jre1.6.0_12
export PATH=$JRE_HOME/bin:$PATH
sanjay@acer:/etc/profile.d$ ls -l java.sh 
-r--r--r-- 1 root root 65 2009-01-20 20:28 java.sh
```

Then source the file and test the java version
```
sanjay@acer:~$ source /etc/profile.d/java.sh 
sanjay@acer:~$ java -version
java version "1.6.0_12-ea"
Java(TM) SE Runtime Environment (build 1.6.0_12-ea-b03)
Java HotSpot(TM) 64-Bit Server VM (build 11.2-b01, mixed mode)
```

Then restart firefox and check the version in the plugin.

You need to delete all previous java packages that you installed prior to doing this especially the ones from Synaptic.

---

