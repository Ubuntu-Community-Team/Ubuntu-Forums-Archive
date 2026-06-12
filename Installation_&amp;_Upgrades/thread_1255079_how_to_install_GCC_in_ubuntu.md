---
title: "how to install GCC in ubuntu"
date: 2009-09-01
forum: Installation &amp; Upgrades
---

### Post by pro_net on 2009-09-01
hello,
To install gcc i do the following process:
Step 1: sudo apt-get install build -essential
Step 2: Give password
But Ubuntu replay Could not find package build.
Please give me outline how to solve this problem in Ubuntu 8.10 desktop verson.

---

### Post by mc4man on 2009-09-01
no space in name
```
sudo apt-get install build-essential
```

---

### Post by lisati on 2009-09-01
> **pro_net said:**
> hello,
To install gcc i do the following process:
Step 1: sudo apt-get install build -essential
Step 2: Give password
But Ubuntu replay Could not find package build.
Please give me outline how to solve this problem in Ubuntu 8.10 desktop verson.

Leave out the space after the word "build". It should be:
```
sudo apt-get install build-essential
```

---

### Post by anujpathania on 2009-09-01
spaces are very critical in terminal. Watch out for them.

---

### Post by pro_net on 2009-09-01
hi mc4man,
according to your suggestion i am trying to do the process in my computer. But the computer show the following message:
E: Command line option 'e' [from-essential] is not known.
Please tell me how to solve this problem.
 
Can I use Bore land C++ editor in Ubuntu?
Also inform me how to change display settings.

---

### Post by mc4man on 2009-09-01
To clear something up. 
When people post back with a command in a **code box** the intention is that that one would copy what's in that box and paste it in where intended ( in this case a terminal.

Usaually if something is in a quote box then it's showing an example

So if you were to copy the command from post 2 or 3 and paste into your terminal you'd be good.

Here's an example of what you've been doing, and the proper command in blue

.
> doug@doug-laptop:~$ sudo apt-get install build- essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package build
doug@doug-laptop:~$ sudo apt-get install build -essential
E: Command line option 'e' [from -essential] is not known.
doug@doug-laptop:~$ [COLOR="Blue"]sudo apt-get install build-essential[/COLOR]
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.

Note that I already have it installed

---

### Post by pro_net on 2009-09-01
Thanks to every one for given their valuable suggestion. Now gcc is install and tell me the following:
1) I have done a c program. Now i want to execute to that program.
In windows we use Turbo C as a editor to write and compile and run the program. In Ubuntu i am trying to write C programusing vi editor. But at the begining  vi editor does not accept  the symbol "#". and file also not run. I want to write a .c program and save as a filename.c  then execute the filename.c. In which way it can possible.

---

