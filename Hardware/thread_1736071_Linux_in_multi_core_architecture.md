---
title: "Linux in multi core architecture"
date: 2011-04-22
forum: Hardware
---

### Post by adaperfum on 2011-04-22
Can someone please help me with linux in multi core architecture? Can something be done in terminal? I would really appreciate your help.:)

---

### Post by stealth. on 2011-04-22
I would help you if I knew what you wanted.

> **adaperfum said:**
> Can someone please help me with linux in multi core architecture? 

That is very very general/vague

---

### Post by adaperfum on 2011-04-23
yes i know its too wide,i just have to talk about linux and multicore architecture and i have no clue what to talk about.i read something about multi core programming on linux but i have no idea whats that about?(i have just started using terminal so i am not good at it :( can you please suggest me any useful tutorial with terminal commands )

---

### Post by stealth. on 2011-04-23
Set this attachment as your background, it will help you with the command line. 

A few things

Learn how to navigate your system, you can do this with the cd command (current directory)
[B]
cd [directory][/B]

cd Desktop
cd /etc/
cd ~/ <--- The ~ symbol represents your "home" directory
cd ~/Pictures
cd ~/Documents

**ls **
ls (list the current files)

ls ~/Desktop

ls    <--With no arguments will list the current directory

ls /var/log

ls -l          <---- (lowercase L) will list everything with extra information
[B]
pwd[/B]    <--- with no arguments will tell you what the present working directory is

**[command] | grep [thing_to_find]** 

ls ~/Pictures | grep "my_pic"     <--grep is a regular expression tool, it will match what you tell it to, its pretty much like find in firefox. 


ls /usr/bin | grep  "youtube" <--This is useful to find a program name that you can quite remember but you know part of. /usr/bin is where all your executable command line programs are.  

Once you get done with that come back, I'll show you some more like editing files with nano etc... or you can always google stuff too :)

---

