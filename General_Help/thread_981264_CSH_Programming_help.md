---
title: "CSH Programming help"
date: 2008-11-13
forum: General Help
---

### Post by Rigas on 2008-11-13
Hey guys, I have a homework assignment to make a csh script that prints the number of users online every minute for 15 minutes.  I made one with a while loop, but I keep getting "Unknown variable modifier" errors.  When I ran csh -x I received: 
```
@ n = 0
while ( 0 < = 15 )
@ n = 0 + 1

```

My script
```
#!/bin/csh
#Created by Daniel Rodriguez
#
#November 13, 2008

date

@ n = 0

while ( $n <= 15 )
   @ n = $n + 1
   echo -n "Users on cycle $n: "
   who | wc | cut -c 7
   sleep 60s
end


```

Any help would be greatly appreciated.  I'm sorry if I posted this in the wrong section.

---

### Post by jamesrl on 2008-11-13
```

   echo -n "Users on cycle $n: "

```
The flaw is on this line as seen by running 
csh -x -v program_name.sh

Sorry I think I was a little too obtuse, originally.  Your error comes about because you have a variable name immediately followed by a colon.  You can get around it by explicitly limiting the variable name in braces like "${n}:"

---

### Post by bodhi.zazen on 2008-11-13
> **Rigas said:**
> Hey guys, I have a homework assignment ... <clip> ...

Please do not use these forums for assistance with home work. The point of home work is for you to learn the solution , not request help on internet forums.

---

