---
title: "Eclipse code completion works partily"
date: 2008-11-09
forum: General Help
---

### Post by caonima on 2008-11-09
I use Eclipse 3.2.2 on Ubuntu 8.04 for C++ programming. The code completion function only works for classes defined in user headers but not library headers. For example,  I have
#include <fstream>
#include <iostream>
using namespace std;

int main(){
	ifstream ifs;
	return 0;
}

"ifs." gives a blank box without any hints. The program compiles and the headers are found. So what could be the problem?

---

### Post by ratmandall on 2008-11-09
> **caonima said:**
> I use Eclipse 3.2.2 on Ubuntu 8.04 for C++ programming. The code completion function only works for classes defined in user headers but not library headers. For example,  I have
#include <fstream>
#include <iostream>
using namespace std;

int main(){
	ifstream ifs;
	return 0;
}

"ifs." gives a blank box without any hints. The program compiles and the headers are found. So what could be the problem?
I don't have an answer but next time you post about programming post here thanks.
[http://ubuntuforums.org/forumdisplay.php?f=39](http://ubuntuforums.org/forumdisplay.php?f=39)

---

