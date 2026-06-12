---
title: "Crontab problem"
date: 2008-10-09
forum: General Help
---

### Post by johnny42 on 2008-10-09
I'm trying to schedual a program I wrote using crontab but the problem is that when I run it, it cannot access the directories and files within the directory it is located, it can only access those files located in my home directory. Is there a way around this without having to edit the program

Heres the crontab entry-

***/15 * * * * /home/johnny/analysis/nta**

"nta" is the program and I want to run every 15 mins and it requires access to folders and files within the analysis directory 


Any help would be great

---

### Post by unutbu on 2008-10-09
This is a hard problem to debug without seeing the nta program. However, perhaps change
```

*/15 * * * * /home/johnny/analysis/nta
```
to```

*/15 * * * * /home/johnny/analysis/nta 1>/home/johnny/nta.out 2>/home/johnny/nta.err
```
Then after cron runs the job look at ~/nta.out and ~/nta.err for clues. 

If you run into any more trouble, please post nta.out and nta.err.

---

### Post by milasch on 2008-10-09
How about creating a script, calling the script from crontab, and running this program as super user in your script?

---

### Post by johnny42 on 2008-10-09
Thanks alot for your help **unutbu**, Im sorry I should have given more details

The program is wirtten in C and it begins by opening and reading the configuration file **/home/johnny/analysis/dat/config.dat**
The pieces of code associated with this are -


[I]FILE *config;
char *configpath  = "dat/config.dat";



**//This part is in a function**
if((config = fopen(configpath,"a+")) == NULL)
{
	perror("fopen config");
	exit(1);
}[/I]


And as you have already guessed the output to the **nta.err** file was **"fopen config: No such file or directory"**.
The thing is this happens to all files the program tries to access because crontab seems to run the program from the **/home/johnny** directory and not the **/home/johny/analysis** directory where its actually located, (I think??) 
Should I maybe be declaring paths differently within the code, I'm lost

Thanks again for the help

---

### Post by johnny42 on 2008-10-09
Thanks **milasch**, I'm going to try that

---

### Post by johnny42 on 2008-10-09
Tried the script but still have the same problem :confused:

---

### Post by johnny42 on 2008-10-09
Got the script to work, have to navigate to the directory first


[B]#!/bin/bash

cd ~/analysis
./nta[/B]



Thanks alot for the help

---

### Post by DGortze380 on 2008-10-09
adding it to root's crontab instead of your own should solve any permissions issue. Be sure you're very careful about what the program does as it will be running with root access.

nvm.. see you got it working... going to leave this post for future reference though.

---

