---
title: "SQL Programs and Linux"
date: 2008-10-09
forum: General Help
---

### Post by drakkus on 2008-10-09
ok, i've recently started a new job that requires me to work alot on SQL, i understand about all the current works and not works that are on linux, like .net and mono, etc, but the program my company require me to use are the SQL database management programs, along with visual studio/business intelligence, it's actually reporting services i work with... so if you've installed, or used this before then u will know what im talking about lol :)

but anyways, im wondering if its worth having a crack at getting it to work on linux... im not a windows fan... i dont actually like windows at all, so i would prefer to use linux, but i just wondered if any 1 has got any SQL server client programs working before... 

and just to state the obvious... im **_NOT_** trying to install SQL Server on a linux box... im try to install the client applications on a linux desktop....


if any 1 can help me, please let me know :)

---

### Post by Paul41 on 2008-10-09
You could try to install it with WINE. I have never tried so I don't know if it will work or not.

---

### Post by drakkus on 2008-10-09
yeah i have thought of using wine, im just wondered if it will damage the database or something along them lines, i work for an insurance company so theres alot of important information that is very valuable if damaged :P

just wondered if any actually has done it before and can confirm that all the features work fine etc :)

---

### Post by leg on 2008-10-09
You shouldn't need to worry about that as you "should" be working off of a testing copy of the data. If not be very careful as you could destroy data anyway.

---

### Post by Paul41 on 2008-10-09
I agree, I don't think it would hurt any of the data but I would test it on a dev box before using it on production data for sure.

---

### Post by drakkus on 2008-10-10
yeah i guess so, guess its just down to testing it and see if it does or doesnt work, Will mono work in the same way as .net does? the programs need .net installed in order to run, just wondering if this is gonna give me agro trying to get them to work correctly :)

---

### Post by forger on 2008-10-10
why specifically use their sql database management software? what sql server is it? oracle?
phpmyadmin does a great job with mysql as far as I know :)

---

### Post by Paul41 on 2008-10-10
SQL Server is Microsoft's RDBMS so the poster is trying to use Enterprise manager and Query analyzer from Microsoft. If that is incorrect let us know and forger is right that you have other options.

---

### Post by drakkus on 2008-10-10
> **forger said:**
> why specifically use their sql database management software? what sql server is it? oracle?
phpmyadmin does a great job with mysql as far as I know :)

its mircosoft sql 2005, and i need to build reports based on SQL the software i wanted to be able to use is reporting services 2005, i need to be able to make reports based on the databases, if there is a program suitable for using and doing this that is linux made, please let me know so i can atleast test it and see :P

---

### Post by directhex on 2008-10-10
> **drakkus said:**
> yeah i guess so, guess its just down to testing it and see if it does or doesnt work, Will mono work in the same way as .net does? the programs need .net installed in order to run, just wondering if this is gonna give me agro trying to get them to work correctly :)

Depends on how it's been written. If it tries to make calls into c:\windows\ntoskrnl.exe, that's not very cross-platform.

---

### Post by forger on 2008-10-11
well.. I don't know how you're doing with programming, but you have a client and a python module for mssql:
> python-pymssql - Python database access for MS SQL server and Sybase
sqsh - commandline SQL client for MS SQL and Sybase servers

I've never tested them, but you could give it a try:
```

sudo apt-get install pymssql
sudo apt-get install sqsh

```

for what is worth, you could make a whole query report with graphical interface in python and gtk :P

---

### Post by drakkus on 2008-10-13
i think its just a test and see sorta game :), i havent used any of the software to indepth to actually see what the benefits, if any (which is unlikely with windows :P) of using it is....

Prolly find i can just design and code a whole graphical report in most query based SQL programs lol

---

