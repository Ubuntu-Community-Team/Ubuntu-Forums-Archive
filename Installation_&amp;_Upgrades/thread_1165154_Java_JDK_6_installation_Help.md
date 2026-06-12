---
title: "Java JDK 6 installation Help"
date: 2009-05-20
forum: Installation &amp; Upgrades
---

### Post by yma981 on 2009-05-20
I installed jdk-6u13-linux-i586.bin  
by using:

chmod +x jdk-6u13-linux-i586.bin
./jdk-6u13-linux-i586.bin 

the installation extracted the content to my /home/yma/jdk1.6.0_13

I renamed it to .jdk1.6.0_13 in order to hide the folder 

I am setting the JAVA_HOME and PATH by 

Adding those 2 lines to /etc/profile

export JAVA_HOME=/home/yma/.jdk1.6.0_13
export PATH=$PATH:$JAVA_HOME/bin

I am testing Java by typing:  

:~$ java --version
The program 'java' can be found in the following packages:
 * gij-4.3
 * java-gcj-compat-headless
 * openjdk-6-jre-headless
 * cacao
 * gij-4.2
 * jamvm
 * kaffe
Try: sudo apt-get install <selected package>
bash: java: command not found
:~$


As you can see no Java ?!!! Any help please

**Also I want to ask How to set the PATH  in general (I know in windows but not in Linux)**

---

### Post by uljanow on 2009-05-20
I'd remove the created folder and instead use:
```
sudo aptitude install sun-java6-jdk
```

---

### Post by yma981 on 2009-05-20
> **uljanow said:**
> I'd remove the created folder and instead use:
```
sudo aptitude install sun-java6-jdk
```

I knew the answer will be something similar to that, But unfortunately i am a little short on bandwidth, I have internet bandwidth limit that i can't exceed, that is the reason i took the .bin file from some1 i know !!! 


BTW when i browse to the JDK and try it, it works 

:~/.jdk1.6.0_13/bin$ ./java -version
java version "1.6.0_13"
Java(TM) SE Runtime Environment (build 1.6.0_13-b03)
Java HotSpot(TM) Server VM (build 11.3-b02, mixed mode)
:~/.jdk1.6.0_13/bin$

---

### Post by yma981 on 2009-05-20
I added the JDK Directory in PATH using the Following

PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/WHEREVER_U_PUT_IT/jdk1.6.0_13/bin

Test OK

---

