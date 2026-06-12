---
title: "studying for LPIC1 and stuck with an assignment"
date: 2008-08-25
forum: General Help
---

### Post by JermainWijnhard on 2008-08-25
Its a long question but i hope you can translate from my command what i want to do..

find /etc/ -name "*" -exec grep -f root {};

also, i have to put all errors in a file with >
Problem is that i'm getting "find: missing argument to '-exec'"

Does anyone know what im doing wrong (and how to transfer the errors,.. i know a '2' is involved in there)

I thank you in advance!

---

### Post by c2olen on 2008-08-25
> **JermainWijnhard said:**
> Its a long question but i hope you can translate from my command what i want to do..

find /etc/ -name "*" -exec grep -f root {};

also, i have to put all errors in a file with >
Problem is that i'm getting "find: missing argument to '-exec'"

Does anyone know what im doing wrong (and how to transfer the errors,.. i know a '2' is involved in there)

I thank you in advance!


redirecting error output, aka STDERR is done like this:
```

#>command_goes_here 2> /output.log

```

If you want the STDERR to go to the same file as the STDOUT, you can tell it to do so like this;
```

#>command_goes_here 1> /output.log 2>&1

```

You can leave out the number 1 in 1>, as it is the default. I left it in to clarify.

---

### Post by c2olen on 2008-08-25
> **JermainWijnhard said:**
> Its a long question but i hope you can translate from my command what i want to do..

find /etc/ -name "*" -exec grep -f root {};



Here, you try to find all files and directories matching "*", meaning all files.
The -name "*" is quite redundant, as the find command itself would return the same results.

```

#>find /etc/*

```

In case you want to find all files matching root, try this;
```

#>find /etc -type f -name *root*

```

Maybe you have to be more ellaborate on the assignment you need to do.

---

### Post by JermainWijnhard on 2008-08-25
thank you for the fast reply :)

Actually i have to grep for the word 'root' in all files in /etc/ and output the errors in a logfile.

now i feel stupid, the question wasnt that long after all.. (but it was when i was translating it earlier ><)

do you have any idea on what caused the "find: missing argument to '-exec'" error?

---

### Post by kpkeerthi on 2008-08-25
> **JermainWijnhard said:**
> 
do you have any idea on what caused the "find: missing argument to '-exec'" error?

This should sort it out:
```

find /etc/ -name "*" -exec grep -f root '{}' ';'

```

---

### Post by JermainWijnhard on 2008-08-26
I found it!

The problem was that the ; didnt have \ so grep tried to use the ; while the -exec was looking for it, thats what caused the error i got!

```
find /etc/ -name "*" -exec grep -f root {} /;
```

Thanks to everyone who helped, i learned a lot from the different aproaches \\:D/

---

