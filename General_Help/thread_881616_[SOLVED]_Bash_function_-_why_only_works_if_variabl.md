---
title: "[SOLVED] Bash function - why only works if variable is specified?"
date: 2008-08-06
forum: General Help
---

### Post by abcuser on 2008-08-06
Hi,
I have written the following bach script:
```

#!/bin/bash
myfunction ()
{
echo $var
}

var=myvar
myfunction $var 

```
The above script echos "myvar".

I have changed it to:
```

#!/bin/bash
myfunction ()
{
echo $var
}

myfunction myvar

```
Note: last two lines are changed.

The second script does not work (it echos empty string). Why?

From [http://linux.byexamples.com/archives/133/write-a-function/](http://linux.byexamples.com/archives/133/write-a-function/) sample it looks like second script should be working.
Thanks,
Abcuser

---

### Post by kirsis on 2008-08-06
> **abcuser said:**
> Hi,
```

#!/bin/bash
myfunction ()
{
echo **$1**
}

myfunction myvar

```


$1 refers to the first param.
$var refers to a variable called var. In your first example, you create this variable before calling the function, so it works (I assume. I'm not that familiar with bash and variable scopes)

---

### Post by abcuser on 2008-08-06
kirsis, thanks for help it works...

I have found out more details on page: [http://tldp.org/LDP/Bash-Beginners-Guide/html/sect_11_01.html](http://tldp.org/LDP/Bash-Beginners-Guide/html/sect_11_01.html)
Thanks,
Abcuser

---

