---
title: "[SOLVED] bash scripting ; extracting a string in a variable"
date: 2008-10-05
forum: General Help
---

### Post by Externalist on 2008-10-05
let's say I have this string stored in a variable

var='f:\dd\vctools\crt_bld\SELF_X86\crt\src\INTEL\mt_lib\chandler4.obj'

I want to only get 'chandler4.obj' this string and store it into another variable. To be more specific, the string that comes after the \ character. I'm reading about a thousand of those from a file so it'd be nice to have a way to do the task in an automated fashion. How would one go about making a bash script that does that?
Thanks

---

### Post by tonybaqain on 2008-10-05
try this :
```

basename $(echo "$var" | sed -e 's|\\|/|g' )

```

in a smart way, it replaces all **\** with **/** since we need the **/** to be used with basename, which outputs the last occurance of a string after the **/** character.

if this suits you, have fun :) , if not, refer back to find you another way.

---

### Post by Externalist on 2008-10-05
Thanks for the reply!
Unfortunately, basename prints an error due to the unexistance of the file 'f:\dd\vctools\crt_bld\SELF_X86\crt\src\INTEL\ mt_lib\chandler4.obj'
The file indeed doesn't exist on my drive so I'd have to find another way to do it. Any suggestions? :confused:

---

### Post by tonybaqain on 2008-10-05
the file is not indeed needed to be there for basename to run correctly, please paste the error , and make sure u're using bash / sh , and u're piping **|** with sed in the command.

---

### Post by tonybaqain on 2008-10-05
i.e 
```

[tony@ tony-desktop:~] # basename /i/dont/have/a/file
file
[tony@ tony-desktop:~] # 

```

---

### Post by tonybaqain on 2008-10-05
there is another way, if you wanna try it :
```

echo "$var" | awk -F\\ '{ words += NF } END{ print $words}'

```

this command creates an array from the **$var** variable, and counts the number of elements in that array, printing the last element out.

have fun :)

---

### Post by Externalist on 2008-10-05
I don't know why basename ceases to work but the second one works like a charm. Thanks a bunch! :D

Regards,

---

### Post by ghostdog74 on 2008-10-05
> **Externalist said:**
> let's say I have this string stored in a variable

var='f:\dd\vctools\crt_bld\SELF_X86\crt\src\INTEL\mt_lib\chandler4.obj'

I want to only get 'chandler4.obj' this string and store it into another variable. To be more specific, the string that comes after the \ character. I'm reading about a thousand of those from a file so it'd be nice to have a way to do the task in an automated fashion. How would one go about making a bash script that does that?
Thanks

dont' have to use external commands
```
# echo ${var##*\\}
chandler4.obj


```

---

