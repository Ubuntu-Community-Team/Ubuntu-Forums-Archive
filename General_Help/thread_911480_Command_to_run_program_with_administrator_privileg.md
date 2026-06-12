---
title: "Command to run program with administrator privileges."
date: 2008-09-05
forum: General Help
---

### Post by enderal on 2008-09-05
I would like to run Adept Manager as root from the command line so I can manage programs.

The initial message that comes up says...

"this application needs special administrator (root) privileges. Please run it as root or through kdesu or sudo programs"

What is the command to do this. I know it begins with sudo but that is all I know in this matter.

Thank you very much.

---

### Post by Fixman on 2008-09-05
```
 kdesu adept 
``` if you use kde,
```
 gksu adept 
``` if you use gnome.

---

### Post by enderal on 2008-09-05
Thanks Fixman but I have tried everything that I can think of and get the same thing.

---

### Post by wolfen69 on 2008-09-05
when you access adept through the menus, it should ask you for your password. then you are "root", and can manage your apps.

---

### Post by enderal on 2008-09-05
Thanks wolfen69

It does not ask for a password, it just instantly gives me the message "this application needs special administrator (root) privileges."

---

### Post by enderal on 2008-09-07
Am I not understanding something?

I have tried everything I can think of. 

When I run "gksu adept" it asks for a password but then nothing happens and Adept still gives the message.

If I prefix the command with sudo it does nothing.

":kdesu adept" returns "Command not found!".

Sure would like to make Adept run.

Thank you.

---

### Post by Dougie187 on 2008-09-07
can you go into a terminal and post the results of
```
cat /etc/group | grep admin
```

---

### Post by jolx on 2008-09-07
> **enderal said:**
> When I run "gksu adept" it asks for a password but then nothing happens and Adept still gives the message.

If I prefix the command with sudo it does nothing.

":kdesu adept" returns "Command not found!".

Sure would like to make Adept run.

Thank you.

that would be because ":kdesu" is not a command, try "kdesu" instead

also instead of 'gksu', try 'gksudo'

if none of those work, u could try just plain old 'sudo' although it is recommended not to do so for graphical applications, however it doesnt usually make any difference

---

### Post by enderal on 2008-09-07
Thanks Dougie187 and jolx

I get:

"lpadmin:x:109:rainbow,root
admin:x:115:rainbow,root"

Dougie187

jolx, still can't get it to work.

---

### Post by enderal on 2008-09-07
Got it I think.

I need to use: "gksudo adept_manager" I was using the wrong name. Still learning this OS.

Thanks much for your assistance.

:)

---

### Post by lost_soul on 2008-09-07
u can use sudo adept_manager as well ..

---

### Post by mb_webguy on 2008-09-08
> **lost_soul said:**
> u can use sudo adept_manager as well ..

You should always run GUI applications with gksu (or kdesu), and use sudo for command-line stuff.

---

