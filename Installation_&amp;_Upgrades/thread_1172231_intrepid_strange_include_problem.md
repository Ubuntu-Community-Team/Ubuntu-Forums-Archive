---
title: "intrepid strange include problem"
date: 2009-05-28
forum: Installation &amp; Upgrades
---

### Post by ebutz on 2009-05-28
Hi all, 

I have intrepid kubuntu installed and I am trying to do some development. 
During compilation I get the following error:

```

/usr/include/c++/4.3/cwchar:52:24: error: wchar.h: No such file or directory

```
However if I try to locate this file I get it perfectly well located in 

/usr/include/wchar.h

Anybody has any idea how this comes about or how to correct this error?

Cheers

---

### Post by ebutz on 2009-05-29
I am posting this in this forum since I did not do any modifications to the installation, so it seems the error is introduced during the installation process. 

I did not get any errors during the installation (of various packages), nor do I have any broken packages, so the problem has to be at least a bit more subtle.

---

### Post by ebutz on 2009-05-30
anyone? anything? I am this --><-- close to reinstalling my system as it renders completely useless for even the most stupid development. 

The problem seems to be even more general:

even with this programm:

```


#include <iostream>

int main(int argc, char** argv)
{
        std::cout << "Hello World" << std::endl;
        return 1;
}


```

doing 

```

g++ dummy.cpp -o test

```

I get the problem

---

