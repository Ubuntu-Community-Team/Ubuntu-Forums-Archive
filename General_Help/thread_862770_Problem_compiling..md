---
title: "Problem compiling."
date: 2008-07-17
forum: General Help
---

### Post by ChanTico on 2008-07-17
Hi, I'm trying to teach myself some basic C but I get the following error message when trying to compile the famous "hello world" program.

> hello.c:1:20: error:  stdio.h: No such file or directory
hello.c:3: error: ‘::main’ must return ‘int’
hello.c: In function ‘int main()’:
hello.c:5: error: ‘printf’ was not declared in this scope

I tried google and the general solution seemed to be to install stdio.h and other libraries in /usr/include.

I downloaded the relevant packages and I have the file /usr/include/stdio.h

But I still get the same error message. Do I need to change a directory path to point the compiler at the C libraries?

Thanks in advance.

---

### Post by iaculallad on 2008-07-17
Install the essential files:

```
sudo apt-get install build-essential
```

---

### Post by ChanTico on 2008-07-17
I've already tried that. 

I also made sure that I had stdc++6-dev and libstdc++6-dev from the package managers, as those were the solutions I found elsewhere on the forum. I had one package and installed the other but I get the exact same error message.

---

### Post by lisati on 2008-07-17
Are you using ```
#include <stdio.h>
``` or ```
#include "stdio.h"
```

---

### Post by ChanTico on 2008-07-17
The first one, but I tried with the speech marks and stdio.h error disappeared. XD

Now my errors are just, 
> 
hello.c: In function &#8216;main&#8217;:
hello.c:4: warning: return type of &#8216;main&#8217; is not &#8216;int&#8217;

edit, the tutorial first program is,

> #include < stdio.h>

void main()
{
    printf("\nHello World\n");
}


---

### Post by |{urse on 2008-07-17
using namespace standard ?

> #include < stdio.h>
using namespace std
void main()
{
printf("\nHello World\n");
}

also there is some whitespace in < stdio.h>

you've tried 

int main()

?

the same thing is achieved also with 

> #include <iostream.h>
using namespace std
int main()
{
cout << "Hello World";
}

also also

you can remove the "using namespace std" and the .h and it will run fine

---

### Post by kunixos on 2008-07-17
Even though you might not use the program itself, when I installed build-essential it still didn't install all of the libraries I needed until I installed KDevelop.

But like I say, you might (or might not) want to use KDevelop anyhow. Decent GUI for C/C++.

Hope this helps!

---

### Post by ChanTico on 2008-07-17
Thanks, the following program compiled as desired.
> 
#include <stdio.h>

int main()
{
    printf("\nHello World\n");
}


I am a total novice to programming and do not have the experience for subtle changes like that. Does KDelevop just support more commands making the tutorial programs more likely to work?

And are there any C tutorials based on the C libraries in the default ubuntu package that anybody knows of?

Thanks for making hello.c work. XD

---

### Post by |{urse on 2008-07-17
[www.cplusplus.com](www.cplusplus.com) is the best resource out there for novice all the way to professional programmers.

---

