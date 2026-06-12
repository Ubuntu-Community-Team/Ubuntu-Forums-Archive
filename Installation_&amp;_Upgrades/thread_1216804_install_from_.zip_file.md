---
title: "install from .zip file?"
date: 2009-07-18
forum: Installation &amp; Upgrades
---

### Post by James58321 on 2009-07-18
Hi Everyone,
I am a n00b to ubuntu (and therefore, linux) and am wondering how to install a program called Biogenesis. I have the link here and if anyone can be of assistance, I would appreciate it. (I've also attached the .zip file I downloaded.)
Thanks.

Link:[http://linux.softpedia.com/progDownload/Biogenesis-Download-19248.html](http://linux.softpedia.com/progDownload/Biogenesis-Download-19248.html)

> Remember, you can do anything with a command prompt.> Play now, Play later.

---

### Post by Partyboi2 on 2009-07-18
Hi, one way to run the program is to open a terminal (Applications>Accessories>Terminal) and download the binary version with wget
```
wget http://downloads.sourceforge.net/sourceforge/biogenesis/biogenesis_jar_0_5.zip?use_mirror=transact
```then unzip it with
```
unzip biogenesis_jar_0_5.zip 
```then enter the newly created directory
```
cd biogenesis_jar
```then make the 'biogenesis.jar' file executable
```
chmod +x biogenesis.jar
```then you can run it from the terminal in its source directory (Where you currently are) with
```
./biogenesis.jar
```or if you want to launch it from your Desktop you can right click on the Desktop and choose "Create launcher" then fill in the details
Type: Application
Name: biogenesis
Command: Browse to '/home/user/biogenesis_jar/biogenesis.jar' (replace user with your username)
Comments: Leave blank or add something
Change icon pic (left top) to what ever you like.

---

### Post by James58321 on 2009-07-19
thanks, but i got this during the end:

boris@james-laptop:~$ cd biogenesis_jar
boris@james-laptop:~/biogenesis_jar$ chmod +x biogenesis.jar
boris@james-laptop:~/biogenesis_jar$ ./biogenesis.jar
bash: ./biogenesis.jar: cannot execute binary file
boris@james-laptop:~/biogenesis_jar$ 

I also tried the launcher, didn't work, tried going to directory, didn't work.

I am attaching pics of the screen

---

### Post by Partyboi2 on 2009-07-19
ok, instead of using './biogenesis.jar' to run the program use
```
 java -jar biogenesis.jar
```If that works you will need to change the "command" field for the launcher to
```
java -jar /home/boris/biogenesis_jar/biogenesis.jar
```

---

### Post by James58321 on 2009-07-19
both times it gave me this:(check attachment for screenshot)

---

### Post by Partyboi2 on 2009-07-19
Have you got java installed?
```
java -version
```Also what version of Ubuntu are you using?

Edit: If you don't have java installed the output to 'java -version' will be 
```
bash: /usr/bin/java: No such file or directory
```If its not installed you can install java with
```
sudo apt-get install openjdk-6-jre
```[FONT=monospace]
[/FONT]```
java -jar biogenesis.jar
```

---

