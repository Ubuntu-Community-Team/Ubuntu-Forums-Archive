---
title: "[SOLVED] Need a Simple Bash Script"
date: 2008-11-12
forum: General Help
---

### Post by Aysah on 2008-11-12
Hello all, I was hoping some linux guru can help me out.  What I want to ultimately do is read the contents of a directory and output every file AND folder name to a logfile.  

Above and beyond (but not necessary) it would be nice if another script was able to run at 12:30 pm every day and list only the newly created files and folders created in the last 24 hours.  

For the time being I'm reading [http://tldp.org/LDP/Bash-Beginners-Guide/html/index.html]("http://tldp.org/LDP/Bash-Beginners-Guide/html/index.html") to start learning some scripting on my own.  But till I get to the necessary level I hope someone could help me out.  :roll:

---

### Post by russlar on 2008-11-12
> **Aysah said:**
> Hello all, I was hoping some linux guru can help me out.  What I want to ultimately do is read the contents of a directory and output every file AND folder name to a logfile.
ls -alrth directory > logfile  

> Above and beyond (but not necessary) it would be nice if another script was able to run at 12:30 pm every day and list only the newly created files and folders created in the last 24 hours.

to schedule it, use cron.

30 12 * * * username script

for the script, don't know. some mix of ls and grep

---

### Post by Idefix82 on 2008-11-12
To list all files and folders that were changed within the last 24 hours you can do
```
find /path/to/folder -mtime -1 printf file.log
```
where /path/to/folder is the full path to where you want to search and file.log is the name of the output file.

---

### Post by Aysah on 2008-11-12
> **Idefix82 said:**
> To list all files and folders that were changed within the last 24 hours you can do
```
find /path/to/folder -mtime -1 printf file.log
```
where /path/to/folder is the full path to where you want to search and file.log is the name of the output file.

Unfortunately it doesnt work for me but when I chop off the printf.log part it does work.
```
find /citadel/CommonShare -mtime -1 
```

This is what I get when I add the printf command:
```
find /citadel/CommonShare -mtime -1 printf file.log
find: paths must precede expression: printf
Usage: find [-H] [-L] [-P] [-Olevel] [-D help|tree|search|stat|rates|opt|exec] [path...] [expression]

```

---

### Post by Slim Odds on 2008-11-12
> **Aysah said:**
> Unfortunately it doesnt work for me but when I chop off the printf.log part it does work.
```
find /citadel/CommonShare -mtime -1 
```This is what I get when I add the printf command:
```
find /citadel/CommonShare -mtime -1 printf file.log
find: paths must precede expression: printf
Usage: find [-H] [-L] [-P] [-Olevel] [-D help|tree|search|stat|rates|opt|exec] [path...] [expression]

```

Well    it should be -printf

and probably> filename

---

### Post by Aysah on 2008-11-12
I just wanted to give a thanks to everyone who helped. Here's a quick heads up to anyone else who wants to do this:

For A List of Directories
```
find ./ -type d -mtime 1 -fprintf sftp.log "%f\n"
```

For A List of Files
```
find ./ -type f -mtime 1 -fprintf sftp.log "%f\n"
```

---

