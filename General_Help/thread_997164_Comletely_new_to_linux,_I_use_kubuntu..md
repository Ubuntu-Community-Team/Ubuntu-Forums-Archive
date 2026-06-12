---
title: "Comletely new to linux, I use kubuntu."
date: 2008-11-29
forum: General Help
---

### Post by atreestump on 2008-11-29
I have a few problems that I need help with.. 
easiest to hardest. here we go.
how do I open programs threw the terminal? and,
I can't get frostwire to open the icon just bounces and then it abates. I'm so lost help is appreciated :)
My kubuntu is fully updated just finished that yesterday.

---

### Post by TheLions on 2008-11-29
to open some programs with terminal just type ./name_of program but it is much easier to press Alt+F2 and type the name program

---

### Post by oldos2er on 2008-11-29
"how do I open programs threw the terminal?"

 Type the program name, then hit Enter.

 If you start Frostwire from the terminal, it will show any errors that occur.

---

### Post by atreestump on 2008-11-29
this is what I got.

Java exec found in PATH. Verifying...
1.4.2-02
OOPS, your java version is too old [java = 1.4.2-02]
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
OOPS, unable to locate java exec in  /usr/lib/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
ls: /usr/java/j*: No such file or directory
OOPS, unable to locate java exec in  /usr/java/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
ls: /opt/j*: No such file or directory
OOPS, unable to locate java exec in  /opt/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)

Just so I don't get any useless suggestions 'yes I have the latest version of java' and 'yes it is installed properly' I have heard of people having this problem with Mac osx and windows but of course I haven't heard of a solution.. nor have I been able to find one..

---

### Post by oldos2er on 2008-11-29
Run this command: sudo apt-get update && sudo apt-get install sun-java5-jre sun-java5-bin

 Then try Frostwire again.

---

