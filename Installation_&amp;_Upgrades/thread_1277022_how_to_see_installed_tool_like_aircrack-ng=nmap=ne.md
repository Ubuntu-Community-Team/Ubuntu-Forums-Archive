---
title: "how to see installed tool like aircrack-ng=nmap=netcat=and all others  in ubuntu9.04"
date: 2009-09-27
forum: Installation &amp; Upgrades
---

### Post by ramazani on 2009-09-27
hi i was wondering if anyone could tell me when installing any tool like aricrack=nmap=netcat= and all others using apt-get install, how to see them where they been installed any command line show them in a shell 
thank you

---

### Post by stlsaint on 2009-09-27
```
Locate <filename>
```

---

### Post by ramazani on 2009-09-27
> **stlsaint said:**
> ```
Locate <filename>
```

i don't understand i tried few thing like locate and name of file but no chance 
command not found

---

### Post by lswb on 2009-09-27
Also "type name" or "which name" will work. The "type" command will also tell if "name" is a file, shell builtin, shell function, or alias.

---

### Post by lswb on 2009-09-27
> **ramazani said:**
> i don't understand i tried few thing like locate and name of file but no chance 
command not found

The locate command depends on a database that is run periodically by a cron job. If you have just installed the program, "locate" will not be able to find it until its database is updated. 

The "which" command OTOH works by searching the directories in your path for the filename. The "type" command does the same, but checks for shell builtins, functions, and aliases of the same name first. 

"locate filename" by default will return anything that has "filename" in it, so the output is often quite lengthy, including libraries, config files, etc, that have a match for "filename" anywhere within them. "type" and "which" only look for the specific executable command that is used.

---

