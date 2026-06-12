---
title: "Problems with JAVA j2sdk1.4.2_09 (Not compile and not run the java and class)"
date: 2005-11-25
forum: General Help
---

### Post by jrios_03 on 2005-11-25
Hi everybody...

I have a little problem when i want to execute a class...

The Terminal says that its a problem with the libgcj and don't run my programs... I try to instal the jedit42install.jar, but nothing... the same problem... I'm new on Linux and Ubuntu, but in the version 5.04 of Ubuntu when I install the j2sdk1.4.2_09 its run perfectly... (Compile, Run, All...) :confused: 

Wath is the problem?... :confused: 

Please help me and sorry my English, I'm Chilean and my English is very poor... :razz: 

Grettings...:D

---

### Post by qbproger on 2005-11-25
make sure java and javac are working.

java --version
javac --version

are the commands for that.

there is a special command for jar files... 
i think it's...
java -jar jedit42install.jar

---

### Post by jrios_03 on 2005-11-26
I know that...
But in the process of execute a .class teh Terminal says that is an error in the Main, thread NoMainMethodException or something like that... in the libgcj... and I don't know what I can do...

In Windows, the same file run perfectly...

What is the problem????

Please help me...

Thanks....

---

### Post by qbproger on 2005-11-26
You need to install java first.  You don't want to use libgcj you want to install Sun's VM.  I think this is the problem you're having.

Here are instructions in getting java from Sun
[http://help.ubuntu.com/starterguide/C/faqguide-all.html#sect-java](http://help.ubuntu.com/starterguide/C/faqguide-all.html#sect-java)

Those aren't the easiest instructions to follow. An easier way is make the bin executable (as in the instructions in the link "chmod +x") run it in your home directory.  Set the neccesary paths in the .bash_profile (so you don't have to worry about it each time).  Then source it (this is on a one time only thing)

the paths should look like hits
export PATH = $PATH:/home/username/java/bin
expart JAVA_HOME = /home/username/java

make sure to include $PATH with the path variable otherwise it'll mess things up.  If you have any other questions just ask.

---

