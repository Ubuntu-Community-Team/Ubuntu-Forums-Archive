---
title: "c preprocessor problems..."
date: 2008-09-05
forum: General Help
---

### Post by adramalech on 2008-09-05
okay so i am having problems with just creating a simple hello world program...in C!!!

here is what i have as proof to show you that i have done every thing possible to make sure that it should work....

```

adramalech@adramalech:~$ pico helloWorld.h
adramalech@adramalech:~$ cat helloWorld.h
/*This program will print Hello World! */

#include <stdio.h>

void  main()
{
        printf("Hello, World!");
}//end main
adramalech@adramalech:~$ gcc hello
gcc: hello: No such file or directory
gcc: no input files
adramalech@adramalech:~$ gcc helloWorld.h
helloWorld.h:3:18: error: stdio.: No such file or directory
helloWorld.h: In function &#8216;main&#8217;:
helloWorld.h:7: warning: incompatible implicit declaration of built-in function &#8216;printf&#8217;
helloWorld.h:6: warning: return type of &#8216;main&#8217; is not &#8216;int&#8217;
adramalech@adramalech:~$ 


```

so what i did was make sure that all the packages necessary where installed...

```

adramalech@adramalech:~$ sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
adramalech@adramalech:~$ sudo apt-get install libc6-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libc6-dev is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
adramalech@adramalech:~$ sudo apt-get install gcc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gcc is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
adramalech@adramalech:~$ 
 


```


EDIT: okay so i seemed to have restarted ubuntu and it seems to atleast compile...but it was giving me problems with having main not an integer type!!!

so i switched the type to interger and just returned 0....to end the program...

but i don't see a helloWorld.out or something.out....

---

### Post by johnl on 2008-09-05
Code should live in a ".c" file.  Only declarations should be in a header file (".h").

Also, the proper signature for "main" is 

```

int main(int argc, char* argv[]) {

}

```

Although 'int main(void)' will also work.

You should return 0 from main on success and any other number on failure.

---

### Post by adramalech on 2008-09-05
whoops that is a very simple mistake...it was sooo late at night when i was trying it that i forgot that it should be filename.c instead of filename.h!!!!

okay so u say int main(void):confused:?? why not int main()??

---

### Post by mali2297 on 2008-09-05
The default name of the executable will be *a.out*. To name it something else, use the -o flag:
```

gcc helloworld.c -o helloworld

```
Then to run it, type
```

./helloworld

```

---

