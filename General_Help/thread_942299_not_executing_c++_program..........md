---
title: "not executing c++ program........."
date: 2008-10-09
forum: General Help
---

### Post by abhilashm86 on 2008-10-09
abhilash@abhilash-desktop:/bin$ sudo g++ binary.cpp
binary.cpp: In function ‘int main()’:
binary.cpp:5: error: ‘cout’ was not declared in this scope
binary.cpp:5: error: ‘endl’ was not declared in this scope
binary.cpp:7: error: ‘cin’ was not declared in this scope

when i executed above prgm,compiler is not recognising cout,endl etc............i used 
#include<iostream>
int main()
as libraries..............how to overcome this problem..............

---

### Post by majorhabib on 2008-10-09
I think you have forgotten to use the std namespace.
A hello world C++ application should look like this:
```

#include <iostream>

using namespace std;

int main(){
    cout << "hello world!\n";
    return 0;
}

```

---

