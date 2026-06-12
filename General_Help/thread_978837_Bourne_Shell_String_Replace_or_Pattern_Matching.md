---
title: "Bourne Shell String Replace or Pattern Matching"
date: 2008-11-11
forum: General Help
---

### Post by seanmu13 on 2008-11-11
How do you do string replacement or pattern matching in a bourne shell script, while placing the replaced string into a variable.

---

### Post by Portmanteaufu on 2008-11-11
To do matching, I'd recommend grep. Use the -P flag to use Perl-style regular expressions and -o to make it only print the part of what it searched that matched your pattern.

Do: 

```

man grep

```

to find out more about its flags. You can use it like so: 

```

VAR=`grep -Po '\b\d\d\d\b' [someTextFile]`

```

to put a return-line-separated list of all the three-digit numbers in someTextFile in the variable $VAR.

For replacement, I'd recommend using sed. There's a good tutorial [here.]("www.grymoire.com/Unix/Sed.html")

---

### Post by spibou on 2008-11-11
> **seanmu13 said:**
> How do you do string replacement or pattern matching in a bourne shell script, while placing the replaced string into a variable.
Why don't you give us an example of what you want?

---

### Post by Cracauer on 2008-11-11
Read about the ${...%} and ${...#} syntax.

foo=barbaz
foo=${foo%baz}

echo $foo

---

### Post by seanmu13 on 2008-11-11
> **spibou said:**
> Why don't you give us an example of what you want?

I want to turn the string "javaw" into "java"

---

### Post by spibou on 2008-11-11
> **seanmu13 said:**
> I want to turn the string "javaw" into "java"
Which string do you want to go into the variable, javaw or java? Also, it's not clear from your example what substitution rule you are using. Is the point to eliminate the letter w? If yes then you do it like ```
result=$( echo "$original_string" | sed s/w//g )
``` or ```
result=$( echo "$original_string" | tr -d w )
``` If the point is to match the whole word javaw and make it java then you do it like ```
result=$( echo "$original_string" | sed s/javaw/java/g ) 
```

---

### Post by seanmu13 on 2008-11-11
I tried this:

result=$( echo "$original_string" | sed s/javaw/java/g )

on a couple of red hat machines and it worked fine.
However, I tried the same command in the same script on a Solaris 10 machine (and Sun OS 5.9) and it throws the following error:

./my_script: syntax error at line 3: 'result=$' unexpected

Any clue to what could be going on here?

---

### Post by spibou on 2008-11-11
Yes, either you're using a different shell or an older version of the same shell than what you use with Red Hat. The quickest answer is probably to do
```
result=` echo "$original_string" | sed s/javaw/java/g `
```
However using an old shell is bound to make you life difficult at some point in the future so you need to look into that. On Solaris  under /bin and /usr/bin you will find old versions of the usual UNIX utilities. The POSIX compliant versions (and the $(...) syntax *is* part of POSIX) exist under a different directory but I don't remember which one off the top of my head. Do **man grep** and see the various pathnames mentioned. But perhaps the problem isn't with the pathname of the shell you're using but rather that the most recent version of BASH (or whatever) is not installed in which case you should install it. But the most probable answer is that you're using the "wrong" pathname for your shell.

---

### Post by Cracauer on 2008-11-13
There is no need for invoking an additional process such as sed or perl, much less a complete pipe.

See my earlier reply. It runs entirely inside the shell. It's not bash specific either.

---

### Post by spibou on 2008-11-13
Your suggestion will match patterns in the beginning or end but not in the middle.

Noone has posted a BASH specific solution. But for one which also works in Korn shell there is ${parameter//pattern/string}

---

