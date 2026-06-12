---
title: "[SOLVED] Launcher doesn't work but command in terminal does"
date: 2008-09-16
forum: General Help
---

### Post by RonB123123 on 2008-09-16
I am trying to run DrJava from a launcher using this command.

java -jar ~/Programs/DrJava/drjava*.jar

When I run that in the terminal, it works fine. I created a launcher on my desktop using that exact same command, yet it doesn't work. Am I using the wrong command? How can I get this program to launch?

---

### Post by iaculallad on 2008-09-16
Open your Launcher properties and change: 

> Type = Application

to

> Type = Application in Terminal

---

### Post by RonB123123 on 2008-09-16
That didn't work for me. I created a new launcher and used the same command above with the type set to Application in Terminal. Once I double clicked on it, all it did was blink the terminal window and disappear.

I was able to get the launcher to work by removing the wildcard and inserting the full file name. I also removed the tilda and replaced it with my full home directory. My launcher is still set to Application because I can't change the type unless I create a new launcher... ? weird. 

This is the working command I use in the launcher.

java -jar /home/USERNAME/Programs/DrJava/drjava-stable-20080904-r4668.jar

---

